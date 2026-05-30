# GIDFP 1.0
## Graphical Image Description Format Protocol

Version: 1.0
Status: Draft

--------------------------------------------------
1. OVERVIEW
--------------------------------------------------

Graphical Image Description Format (GIDF) is a text-based
image description format.

Instead of storing pixels directly, GIDF stores drawing
rules, mathematical expressions, colors, and graphical
objects.

Recommended use cases:

- Logos
- Icons
- UI elements
- Technical diagrams
- Mathematical graphics
- Simple illustrations

--------------------------------------------------
2. FILE STRUCTURE
--------------------------------------------------

A GIDF file consists of:

Header
Canvas Size
Variables (Optional)
Drawing Commands

Example:

GIDF
size|200*200

FFFFFF(*)

ED1A3D(CF(100,100,50))

--------------------------------------------------
3. HEADER
--------------------------------------------------

The first line MUST be:

GIDF

Example:

GIDF

--------------------------------------------------
4. CANVAS SIZE
--------------------------------------------------

Syntax:

size|WIDTH*HEIGHT

Example:

size|1920*1080

Rules:

- WIDTH MUST be greater than 0
- HEIGHT MUST be greater than 0
- Unit is pixels

--------------------------------------------------
5. COLORS
--------------------------------------------------

Colors are represented as 6-digit hexadecimal RGB values.

Syntax:

RRGGBB(command)

Examples:

FF0000(...)
00FF00(...)
0000FF(...)

--------------------------------------------------
6. VARIABLES
--------------------------------------------------

Variables may be defined using:

var name=value

Examples:

var cx=100
var cy=100
var radius=50

Variables may be used in commands.

Example:

FF0000(CF(cx,cy,radius))

--------------------------------------------------
7. DRAWING COMMANDS
--------------------------------------------------

7.1 Circle

C(x,y,r)

Draws a circle outline.

Example:

FF0000(C(100,100,50))

--------------------------------------------------

7.2 Filled Circle

CF(x,y,r)

Draws a filled circle.

Example:

FF0000(CF(100,100,50))

--------------------------------------------------

7.3 Rectangle

R(x1,y1,x2,y2)

Draws a rectangle outline.

Example:

000000(R(10,10,100,100))

--------------------------------------------------

7.4 Filled Rectangle

RF(x1,y1,x2,y2)

Draws a filled rectangle.

Example:

0000FF(RF(10,10,100,100))

--------------------------------------------------

7.5 Ellipse

E(x,y,rx,ry)

Draws an ellipse outline.

Example:

00FF00(E(100,100,50,30))

--------------------------------------------------

7.6 Filled Ellipse

EF(x,y,rx,ry)

Draws a filled ellipse.

Example:

00FF00(EF(100,100,50,30))

--------------------------------------------------

7.7 Line

L(x1,y1,x2,y2)

Draws a straight line.

Example:

000000(L(0,0,200,200))

--------------------------------------------------
8. BACKGROUND FILL
--------------------------------------------------

Syntax:

RRGGBB(*)

Example:

FFFFFF(*)

Fills the entire canvas with the specified color.

--------------------------------------------------
9. MATHEMATICAL EXPRESSIONS
--------------------------------------------------

GIDF supports mathematical image generation.

Example:

000000(
y=100+50*sin(x/10)
)

Pixels satisfying the expression SHALL be rendered.

Supported operators:

+
-
*
/
^
=
<
>
<=
>=

Supported functions:

sin()
cos()
tan()
sqrt()
abs()

--------------------------------------------------
10. BUILT-IN SHAPE DEFINITIONS
--------------------------------------------------

Circle:

C : (x-a)^2 + (y-b)^2 = r^2

Filled Circle:

CF : (x-a)^2 + (y-b)^2 <= r^2

Ellipse:

E : ((x-a)^2/rx^2)+((y-b)^2/ry^2)=1

Filled Ellipse:

EF : ((x-a)^2/rx^2)+((y-b)^2/ry^2)<=1

--------------------------------------------------
11. COMMENTS
--------------------------------------------------

Comments begin with #

Example:

# This is a comment

--------------------------------------------------
12. EXAMPLE FILE
--------------------------------------------------

GIDF
size|500*500

# Variables

var cx=250
var cy=250
var r=100

# Background

FFFFFF(*)

# Red circle

FF0000(CF(cx,cy,r))

# Black border

000000(C(cx,cy,r))

--------------------------------------------------
13. FILE EXTENSION
--------------------------------------------------

Official extension:

.gidf

--------------------------------------------------
14. MIME TYPE
--------------------------------------------------

Recommended MIME type:

image/gidf

--------------------------------------------------
15. FUTURE EXTENSIONS
--------------------------------------------------

Reserved for future versions:

Polygon:
P(...)
PF(...)

Layers:
layer

Transparency:
alpha

Gradients:
gradient

Image embedding:
img(...)
