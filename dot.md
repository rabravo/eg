# dot

generate a png image from a dot graph file

    dot graph.dot -Tpng -o image.png


generate a postscript image

    dot graph.dot -Tps -o image.ps


generate an eps image

    dot graph.dot -Teps -o image.eps



# Basic Usage

    dot <graph.dot> -T<format> -o <output>



# Graph Direction

set left-to-right layout inside the dot file

    rankdir="LR";



# Invisible Edge

hide an edge between two nodes

    node1 -> node2 [style=invis];


