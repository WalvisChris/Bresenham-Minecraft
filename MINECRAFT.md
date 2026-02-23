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

## loop logic  
| Item | Bits | Mode | Range |
|------|------|------|-------|
| D - 2*dx | 5b | unsigned | 0..31 |
| D + 2*dy | 5b | unsigned | 0..31 |

## other  
| Item | Bits | Mode | Range |
|------|------|------|-------|
| Display | 3b | unsigned | 0..7 |

_These sizes are not required. I tried them at random before understanding and they worked. Assuming x1 > x0 and x0 >= 0 you will mostly use 3b unsigned, and when you multiply by 2 you might need 4b or even 5b unsigned._  

# 64x64 display bresenham all octant line renderer  
## starting values  
| Item | Bits | Mode | Range | Reasoning |
|------|------|------|-------|-----------|
| Input | 6b | 2s-complement | -32..31 | I want a 64x64 display |
| x1 - x0 | 7b | 2s-complement | -128..127 | limit is `-32 - 31 = -63` |
| abs(x1 - x0) | 6b | unsigned | 0..63 | same limit but no signed bit |
| sign(x1 - x0) | ANY | 2s-complement | ANY | just extend top bits |
| 2*dy - dx | 7b | 2s-complement | -128..127 | limits are `2*63 - 0 = 126` and `2*0 - 63 = -63` |
| 2*dy | 7b | 7b unsigned | 0..127 | limit is `2*63 = 126` |
| 2*(dy - dx) | 7b | 2s-complement | -128..127 | limits are `2*(0 - 63) = -63` and `2*(63 - 0) = 126` |

## loop logic  
| Item | Bits | Mode | Range |
|------|------|------|-------|
|..|..|..|..|