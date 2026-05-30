# 2. File Structure

A GIDF file consists of:

Header
Canvas Definition
Variable Definitions (optional)
Drawing Instructions

Example:

```gidf
GIDF
size|200*200

FFFFFF(*)

ED1A3D(CF(100,100,50))
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

---

# 6. Variables

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

# 10. Layer Order

Example:

```gidf
FFFFFF(*)

0000FF(CF(100,100,80))

FFFFFF(CF(100,100,40))
```

---

# 11. Mathematical Expressions

Example:

```gidf
000000(
y=100+50*sin(x/20)
)
```

Supported functions:

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

Example:

```gidf
# Logo background

FFFFFF(*)
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
