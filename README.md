# GIDFP
## Graphical Image Description Format Protocol

---

# 1. Overview

Graphical Image Description Format Protocol (GIDFP) defines the syntax and rendering rules for Graphical Image Description Format (GIDF) files.

Unlike raster image formats, GIDF stores graphical descriptions, mathematical expressions, and drawing instructions rather than individual pixels.

GIDF is intended for:

- Logos
- Icons
- Web graphics
- UI elements
- Technical diagrams
- Mathematical graphics

GIDF is not optimized for photographic images.

---

# 2. File Structure

A GIDF file consists of:

- Header
- Canvas Definition
- Variable Definitions (optional)
- Drawing Instructions

Example:

```gidf
GIDF
size|200*200

FFFFFF(*)

ED1A3D(CF(100,100,50))
```

---

# 3. Header

The first line of a valid file MUST be:

```gidf
GIDF
```

Future versions may support:

```gidf
GIDF|2.0
```

---

# 4. Canvas Definition

Syntax:

```gidf
size|WIDTH*HEIGHT
```

Example:

```gidf
size|1920*1080
```

Requirements:

- Width > 0
- Height > 0
- Integers only

---

# 5. Color Format

Colors are represented as 6-digit hexadecimal RGB values.

Syntax:

```gidf
RRGGBB
```

Examples:

```gidf
FFFFFF
000000
ED1A3D
00FF00
```

---

# 6. Variables

Variables may be declared before drawing instructions.

Syntax:

```gidf
var name=value
```

Example:

```gidf
var cx=100
var cy=100
var r=50
```

Variables are case-sensitive.

---

# 7. Drawing Instructions

General syntax:

```gidf
COLOR(SHAPE(parameters))
```

Example:

```gidf
FF0000(CF(100,100,50))
```

---

# 8. Built-in Shapes

## Circle

Definition:

```gidf
C(x,y,r)
```

Mathematical form:

```text
(x-a)^2+(y-b)^2=r^2
```

Example:

```gidf
FF0000(C(100,100,50))
```

---

## Filled Circle

Definition:

```gidf
CF(x,y,r)
```

Mathematical form:

```text
(x-a)^2+(y-b)^2<=r^2
```

Example:

```gidf
FF0000(CF(100,100,50))
```

---

## Rectangle

Definition:

```gidf
R(x1,y1,x2,y2)
```

Example:

```gidf
0000FF(R(10,10,100,100))
```

---

## Filled Rectangle

Definition:

```gidf
RF(x1,y1,x2,y2)
```

Example:

```gidf
0000FF(RF(10,10,100,100))
```

---

## Line

Definition:

```gidf
L(x1,y1,x2,y2)
```

Example:

```gidf
000000(L(0,0,199,199))
```

---

## Ellipse

Definition:

```gidf
E(x,y,rx,ry)
```

Mathematical form:

```text
((x-a)^2)/(rx^2)+((y-b)^2)/(ry^2)=1
```

Example:

```gidf
00FF00(E(100,100,50,25))
```

---

## Filled Ellipse

Definition:

```gidf
EF(x,y,rx,ry)
```

Mathematical form:

```text
((x-a)^2)/(rx^2)+((y-b)^2)/(ry^2)<=1
```

Example:

```gidf
00FF00(EF(100,100,50,25))
```

---

# 9. Canvas Fill

Entire canvas:

```gidf
FFFFFF(*)
```

Meaning:

```text
For all pixels:
    color = FFFFFF
```

---

# 10. Layer Order

Instructions are rendered from top to bottom.

Example:

```gidf
FFFFFF(*)

0000FF(CF(100,100,80))

FFFFFF(CF(100,100,40))
```

Result:

- White background
- Blue circle
- White hole in center

---

# 11. Mathematical Expressions

Implementations MAY support direct equations.

Example:

```gidf
000000(
y=100+50*sin(x/20)
)
```

Supported functions MAY include:

```gidf
sin()
cos()
tan()
sqrt()
abs()
log()
exp()
```

---

# 12. Comments

Lines beginning with:

```gidf
#
```

are ignored.

Example:

```gidf
# Logo background

FFFFFF(*)
```

---

# 13. File Extension

Recommended extension:

```gidf
.gidf
```

MIME type:

```text
image/gidf
```

---

# 14. Example File

```gidf
GIDF
size|800*600

# Background
FFFFFF(*)

# Red circle
ED1A3D(CF(400,300,150))

# Black border
000000(C(400,300,150))
```

---

# 15. Design Goals

1. Human-readable
2. Text-editable
3. Lossless
4. Resolution-independent
5. Efficient for logos and graphics
6. Mathematical representation support
7. Simple implementation

---

End of GIDFP
