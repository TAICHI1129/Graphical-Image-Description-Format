GIDFP

Graphical Image Description Format Protocol

Version 1.0 Draft


---

1. Overview

Graphical Image Description Format Protocol (GIDFP) defines the syntax and rendering rules for Graphical Image Description Format (GIDF) files.

Unlike raster image formats, GIDF stores graphical descriptions, mathematical expressions, and drawing instructions rather than individual pixels.

GIDF is intended for:

Logos

Icons

Web graphics

UI elements

Technical diagrams

Mathematical graphics


GIDF is not optimized for photographic images.


---

2. File Structure

A GIDF file consists of:

Header
Canvas Definition
Variable Definitions (optional)
Drawing Instructions

Example:

GIDF
size|200*200

FFFFFF(*)

ED1A3D(CF(100,100,50))


---

3. Header

The first line of a valid file MUST be:

GIDF

Future versions may support:

GIDF|2.0


---

4. Canvas Definition

Syntax:

size|WIDTH*HEIGHT

Example:

size|1920*1080

Requirements:

Width > 0

Height > 0

Integers only



---

5. Color Format

Colors are represented as 6-digit hexadecimal RGB values.

Syntax:

RRGGBB

Examples:

FFFFFF
000000
ED1A3D
00FF00


---

6. Variables

Variables may be declared before drawing instructions.

Syntax:

var name=value

Example:

var cx=100
var cy=100
var r=50

Variables are case-sensitive.


---

7. Drawing Instructions

General syntax:

COLOR(SHAPE(parameters))

Example:

FF0000(CF(100,100,50))


---

8. Built-in Shapes

Circle

Definition:

C(x,y,r)

Mathematical form:

genui{"math_block_widget_always_prefetch_v2":{"content":"(x-a)^2+(y-b)^2=r^2"}}Example:

FF0000(C(100,100,50))


---

Filled Circle

Definition:

CF(x,y,r)

Mathematical form:

(x-a)^2+(y-b)^2\le r^2

Example:

FF0000(CF(100,100,50))


---

Rectangle

Definition:

R(x1,y1,x2,y2)

Example:

0000FF(R(10,10,100,100))


---

Filled Rectangle

Definition:

RF(x1,y1,x2,y2)

Example:

0000FF(RF(10,10,100,100))


---

Line

Definition:

L(x1,y1,x2,y2)

Example:

000000(L(0,0,199,199))


---

Ellipse

Definition:

E(x,y,rx,ry)

Mathematical form:

\frac{(x-a)^2}{r_x^2}+\frac{(y-b)^2}{r_y^2}=1


---

Filled Ellipse

Definition:

EF(x,y,rx,ry)

Mathematical form:

\frac{(x-a)^2}{r_x^2}+\frac{(y-b)^2}{r_y^2}\le1


---

9. Canvas Fill

Entire canvas:

FFFFFF(*)

Meaning:

For all pixels:
    color = FFFFFF


---

10. Layer Order

Instructions are rendered from top to bottom.

Example:

FFFFFF(*)

0000FF(CF(100,100,80))

FFFFFF(CF(100,100,40))

Result:

White background

Blue circle

White hole in center



---

11. Mathematical Expressions

Implementations MAY support direct equations.

Example:

000000(
y=100+50*sin(x/20)
)

Supported functions MAY include:

sin()
cos()
tan()
sqrt()
abs()
log()
exp()


---

12. Comments

Lines beginning with:

#

are ignored.

Example:

# Logo background

FFFFFF(*)


---

13. File Extension

Recommended extension:

.gidf

MIME type:

image/gidf


---

14. Example File

GIDF
size|800*600

# Background
FFFFFF(*)

# Red circle
ED1A3D(CF(400,300,150))

# Black border
000000(C(400,300,150))


---

15. Design Goals

1. Human-readable


2. Text-editable


3. Lossless


4. Resolution-independent


5. Efficient for logos and graphics


6. Mathematical representation support


7. Simple implementation




---

End of GIDFP Version 1.0 Draft
