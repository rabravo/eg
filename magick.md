# magick (ImageMagick v7)

> **Note:** `convert` is deprecated in ImageMagick v7. Use `magick` instead.

install ImageMagick on Debian/Ubuntu

    sudo aptitude install imagemagick


convert eps to png at high quality

    magick -density 200 fig.eps fig.png

    # -density 200    render at 200 DPI (higher → sharper raster output)


make a background colour transparent

    magick fig.png -transparent 'COLOR' fig-trans.png

    # replace COLOR with the exact colour name or hex value, e.g. white or '#ffffff'
    # ref: https://stackoverflow.com/questions/9155377/set-transparent-background-using-imagemagick-and-commandline-prompt


resize an image to N×M pixels

    magick orig-img.ext -resize NxM target-img.ext

    # -resize NxM    fit within an N-wide by M-tall box; preserves aspect ratio by default
    # use -resize NxM\!  to force exact dimensions (ignores aspect ratio)
    # ref: https://www.howtogeek.com/109369/how-to-quickly-resize-convert-modify-images-from-the-linux-terminal/


scale an image by a percentage

    magick origin_pic.ext -scale XX% new_pic.ext

    # -scale 50%    halve the image dimensions


convert between formats (e.g. png to jpeg)

    magick input.png output.jpg

    # ImageMagick infers the format from the file extension


create an animated gif from a sequence of images

    magick -delay N00 -loop 0 *.jpeg filename.gif

    # -delay N00    N seconds between frames (e.g. 100 = 1 s, 200 = 2 s)
    # -loop 0       loop forever
    # all source images should be the same size and resolution


add a watermark to an image

    composite -watermark 10% -gravity south watermark.png target.png result.png

    # -watermark 10%    blend watermark at 10 % opacity
    # -gravity south    place it at the bottom centre
    # ref: http://www.imagemagick.org/Usage/annotating/


add a coloured frame around an image and output as eps

    magick source.ext -mattecolor 'rgb(105,8,25)' -frame 3%x3%+3+3 output.eps

    # -mattecolor    colour of the frame border
    # -frame WxH+O+I    frame width×height + outer + inner bevel


# -----------------------------------------------------------
# Perl script — wrap any image in a frame and save as eps
# -----------------------------------------------------------
# Usage: perl script_magick.pl <file_to_be_converted>
# When the source is already eps, the script prompts before
# overwriting; any other format is converted directly.
#
# #!/usr/bin/perl
# use Switch;
# my $source = $ARGV[0];
# my($target, $ext) = $source =~ m/(.*\.)(.*)$/;
# chop $target;
# if ($ext ne "eps") {
#   `magick $source -mattecolor 'rgb(105,8,25)' -frame 3\%x3\%+3+3 $target.eps`;
# } else {
#   print "Want to overwrite file (Y/N): ";
#   my $ans = <STDIN>; chop $ans;
#   switch ($ans) {
#     case m/^y/i { `magick $source -mattecolor 'rgb(105,8,25)' -frame 3\%x3\%+6+6 $target.eps`; }
#     case m/^n/i {
#       print "Name of file: "; my $ans2 = <STDIN>; chop $ans2;
#       `magick $source -mattecolor 'rgb(105,8,25)' -frame 3\%x3\%+6+6 $ans2`;
#     }
#   }
# }


# -----------------------------------------------------------
# Linux + OpenCV: compile and convert
# -----------------------------------------------------------

compile an OpenCV C++ program

    g++ -o output input.cpp -I/PATH/opencv2 -L/PATH/lib \
        -lopencv_core -lopencv_highgui -lopencv_imgproc

    # replace /PATH with the actual OpenCV installation prefix


convert an image from png to jpeg using OpenCV (C++)

    // #include <opencv2/opencv.hpp>
    // cv::Mat img = cv::imread("input.png");
    // cv::imwrite("output.jpg", img);
    // compile with the flags above
