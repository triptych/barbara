# Target Language

The target language was created using the SVG.js library. The language was designed as a stack-based language.

## Shapes

### @circle (x, y, radius)

### @rect (x, y, width, height)

### @path (string)

### @polygon (string)

### @text (string)


## Fills

### @pattern (...)

### @gradient (...)


## Transformations

### @color (color)

### @outline (color, line-width)

### @radius (pixels)

### @flip (offset, axis)

### @diag (offet)

### @rotate (degree)

### @repeat

### @size (x, y) 

### @move (x, y)


## Animations

### @animate-color (color, time, loop?)

### @animate-rotate (degree, time, loop?)

### @animate-move (x, y, time, loop?)


## Getters, Setters, Grouping

### @all

### @copy

### @duplicate

### @define (name)

### @get (name)

### @group (elements...)




# Grammar Input Examples

### Polygon Example
```
(*0,0 100,50 50,100** polygon)
```

### Duplication Example
```
(*0,0 100,50 50,100** polygon 
duplicate 10 10 move 
duplicate 20 20 move 
duplicate 30 30 move)
```

### Duplication Example
```
(0 0 100 100 rect red color) 
(*100,10 40,198 190,78 10,78 160,198** polygon duplicate 25 25 move duplicate 50 50 move duplicate 75 75 move)
(all 50 50 size duplicate 50 50 move duplicate 0 50 move duplicate 50 0 move)
(all duplicate 50 50 size 25 25 move 90 rotate white color)
(all 50 50 size)
(all duplicate 50 x flip)
(all duplicate 50 y flip)
```


### Repetition, Ordering & Animation
```
(0 0 100 circle black color)
(50 50 50 circle lightblue color)
(all 50 50 size repeat)
(all 50 50 size repeat)
(all 50 50 size 35 rotate)
(all repeat)

(all 360 3000 true animate-rotate)

(0 0 100 100 rect lightgrey color back order)
```

### Repetition, Ordering & Animation
```
(0 0 100 circle black color)
(50 50 50 circle lightblue color)
(all 50 50 size repeat)
(all 50 50 size repeat)
(all 50 50 size 35 rotate)
(all repeat)

(all 360 3000 true animate-rotate)

(((0 0 50 50 rect) first-def define) first-def get grey color)
(((0 50 50 50 rect) sec-def define) sec-def get pink color)
(((50 0 50 50 rect) thir-def define) thir-def get lightgreen color)
(((50 50 50 50 rect) four-def define) four-def get violet color)

(first-def sec-def thir-def four-def group five-def define)
(five-def get 50 50 size repeat five-def define)
(five-def get back order)
```

### Squares!
```
(((0 0 50 50 rect) first-def define) first-def get blue color)
(((0 50 50 50 rect) sec-def define) sec-def get red color)
(((50 0 50 50 rect) thir-def define) thir-def get yellow color)
(((50 50 50 50 rect) four-def define) four-def get green color)

(first-def sec-def thir-def four-def group five-def define)

(five-def get 50 50 size)

(five-def copy fivedef-cpy define fivedef-cpy get 50 50 move 180 rotate)
(five-def copy fivedef-cpy1 define fivedef-cpy1 get 0 50 move 270 rotate)
(five-def copy fivedef-cpy2 define fivedef-cpy2 get 50 0 move 90 rotate)

(five-def fivedef-cpy fivedef-cpy1 fivedef-cpy2 group bigone define)
(bigone get 50 50 size)

(bigone copy big-cpy define big-cpy get 50 50 move)
(bigone copy big-cpy1 define big-cpy1 get 0 50 move)
(bigone copy big-cpy2 define big-cpy2 get 50 0 move)

(all 50 50 size repeat)
(all duplicate 45 rotate)
        
```


### Glowing Red Heart
```
(*M 213.1,6.7
  c -32.4-14.4-73.7,0-88.1,30.6
  C 110.6,4.9,67.5-9.5,36.9,6.7
  C 2.8,22.9-13.4,62.4,13.5,110.9
  C 33.3,145.1,67.5,170.3,125,217
  c 59.3-46.7,93.5-71.9,111.5-106.1
  C 263.4,64.2,247.2,22.9,213.1,6.7
  z** path 100 100 size #ff0000 3000 false animate-color)
```



### Prelim Pattern

```
(pattern mything define)
(0 0 100 100 rect $mything color)
```

### Prelim Gradient

```
(gradient mygrad define)
(0 0 100 circle $mygrad color)
(all 360 4000 true animate-rotate)
```



---

Kit Zellerbach & Prof. Charlie Roberts