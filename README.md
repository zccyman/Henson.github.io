# zccyman.github.io

# meshgrid

```
import torch
from sympy import *

x = torch.linspace(-1, 1, 33)
y = torch.linspace(-1, 1, 33)
z = torch.linspace(-1, 1, 33)

grid_x, grid_y, grid_z = torch.meshgrid(x, y, z)
print(grid_x.shape, grid_y.shape, grid_z.shape, "\n\n")

x = Symbol('x')
y = Symbol('y')
z = Symbol('z')
T = Symbol('T')

print(((x+y+T)**3).expand(), "\n\n")
print(((x+y+z+T)**3).expand(), "\n\n")

```
