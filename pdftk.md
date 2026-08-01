# pdftk

extract the Kth page from in.pdf into out.pdf (e.g. page 5)

    pdftk A=in.pdf A5 output out.pdf


remove the Kth page (e.g. page 13) from in.pdf

    pdftk A=in.pdf cat A1-12 A14-end output out.pdf


extract a range of pages (e.g. pages 24-42)

    pdftk A=in.pdf cat A24-42 output out.pdf


join two pdf files into one

    pdftk in1.pdf in2.pdf cat output out.pdf


split a pdf into individual pages

    pdftk in.pdf burst output page_%02d.pdf


