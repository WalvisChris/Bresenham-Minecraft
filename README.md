# Bresenham's Algorith  
```py
dx = x1 - x0    # delta x
dy = y1 - y0    # delta y

D = 2*dy - dx   # binary shift 1<<

x = x0
y = y1

while x < x1:   # 5 bit magnitude comparator
    plot(x, y)

    if D > 0:   # NOT 2s complement MSB
        y = y + 1
        D = D - 2*dx

    D = D + 2*dy
```

# All octant line draws  
```py
dx = abs(x1 - x0)
dy = abs(y1 - y0)

sx = (x0 < x1) ? 1 : -1
sy = (y0 < y1) ? 1 : -1

err = dx + dy

while true:
    plot(x0, y0)

    e2 = 2 * err

    if e2 >= dy:
        if x0 == x1 break
        err = err + dy
        x0 = x0 + sx

    if e2 <= dx:
        if y0 == y1 break
        err = err + dx
        y0 = y0 + sy
```