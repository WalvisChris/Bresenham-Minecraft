# 8x8 display bresenham one octant line renderer  
## formula  
![minecraft formula](media/minecraft_formula.png)  

## components  
![minecraft build](media/minecraft_build.png)  
1. 8x8 Display  
2. Incrementor with load function (x)  
3. Incrementor with load function (y)  
4. Magnitude comparator (x > x1)  
5. Subtractor (x1 - x0)  
6. Subtractor (y1 - y0)  
7. Subtractor (2*dy - dx)  
8. Subtractor (D - 2*dx)  
9. Adder (D + dy*2)  

## starting values  
| Item | Bits | Mode | Range |
|------|------|------|-------|
| Input | 3b | unsigned | 0..7 |
| x0 - x1 | 3b | unsigned | 0..7 |
| 2*dy - dx | 5b | unsigned | 0..31 |
| D - 2*dx | 5b | unsigned | 0..31 |
| D + 2*dy | 5b | unsigned | 0..31 |
| Display | 3b | unsigned | 0..7 |

# 64x64 display bresenham all octant line renderer  
## starting values  
| Item | Bits | Mode | Range |
|------|------|------|-------|
| Input | 6b | 2s-complement | -64..63 |
| x1 - x0 | 7b | 2s-complement | -128..127 |
| abs(x1 - x0) | 6b | unsigned | 0..63 |
| sign(x1 - x0) | ANY | 2s-complement | ANY |
| 2*dy - dx | 8b | 2s-complement | -256..255 |
| 2*dy | 7b | 2s-complement | -128..127 |
| 2*(dy - dx) | 8b | 2s-complement | -256..255 |

## loop logic  
| Item | Bits | Mode | Range |
|------|------|------|-------|
|..|..|..|..|