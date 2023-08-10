# Git
8/8

use (bcw serve) to run the web

windows key and period to bring up emojis

* will select everything on page

shift alt down press down to duplicate

ex. (
    .d-flex{
        display: flex;
    }
)

hold down alt to create multiple cursors

justify-content: ;
align-items: ;
object-fit: ;
text-decoration: ;  

a.active {}
a:hover

:root{
    --dark: #34234;
    --light: #32566;
}
use it like this 
var(--dark)

link:mdi (to use icons)
mdi-i



"em" matches up with the font size

use anchor or a tag to create a link

using flex direction, justify content will not work, align-items is correct for this case



8/9
link:b5 will you give bootstrap  (your style sheet should come after your external or css link to the bottom)  

rows and columns exists in containers, container fluid wraps all the way to the end

started off with creating a section(row), put a div(column or col) in the section, adding another div created 50 50 split on row oe even use a number on a div from 1-12 depending on how large you want it

bg primary is a blue color


<!-- NOTE cols are over 12 segments with gap and justify, you should always have a "base" col size with no infix -->
<!-- NOTE using col, col's with evenly distribute through row -->
<!-- NOTE cols be given a exact size to fit -->


<!-- justify-content is a class and can be used with empty space -->

header contains the class using container fluid

p = padding     fw = font weight    fs = font size , btn is class for button, ms = margin start, ps = padding start, rounded = border radius, pe = padding end, img-fluid is supposed to make the image fit in the container  py = padding for top and bottom, px = padding for left and right                     

code breaks and Apply now etc are in different divs, you can also try level it out by padding

apply justify content to whatever is flex or the row(section), sections are always display flex!
use "text end" to push all to the end

align-items end will drop the text to the bottom   

vh = view height 
background size = cover

Ex: col 12 col-md-6, is supposed to help align things vertically in smaller screens
Ex: p-1 p-md-5 padding for smaller screens
Ex: order-2 order-md-1

order-first, arranges it be first or top
order-last


8/10 
    EX:     :root{
        --green: 11d200;
    }

    parent have position: relative
    children have position: absolute

    rounded = border radius
    background-size:
    background-position
    style:debug
   text-center 
   text-align
   justify-content: moves things left to right
   align-content: moving things up and down 
   margin: adds space around
   when dealing with rows, use align-items

d-md-block = use for blocking things in small screens


EX: think about mobile first
@media(min-width:768px){
    .hero-row{
        background-image: url()
    }
}

@media(max-width:768px){
    .class{
        background-image: url()
    }
}

sticky-top = applies position fix, can be used for header. For example can use on a nav bar 

