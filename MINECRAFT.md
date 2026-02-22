# 64x64 display bresenham all octant line renderer  
| Item | Bits | Mode | Range |
|------|------|------|-------|
| Input | 6b | 2s-complement | -64..63 |
| x1 - x0 | 7b | 2s-complement | -128..127 |
| abs(x1 - x0) | 6b | unsigned | 0..63 |
| sign(x1 - x0) | ANY | 2s-complement | ANY |
| 2*dy - dx | 8b | 2s-complement | -256..255 |
| 2*dy | 7b | 2s-complement | -128..127 |
| 2*(dy - dx) | 8b | 2s-complement | -256..255 |
