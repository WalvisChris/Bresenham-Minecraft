# Bresenham's Algorith  
```py
dx = x1 - x0
dy = y1 - y0

D = 2*dy - dx

y = y1
x = x0
while x < x1:
    plot(x, y)

    if D > 0:
        y = y + 1
        D = D - 2*dx

    D = D + 2*dy
```

# Multidirectional  
```py
dx = abs(x1 - x0)
dy = abs(y1 - y0)

sx = (x0 < x1) ? 1 : -1
sy = (y0 < y1) ? 1 : -1


```