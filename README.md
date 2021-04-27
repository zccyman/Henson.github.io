# zccyman.github.io

# color enhancement

## fivek dataset
- [Preparing-data-for-the-MIT-Adobe-FiveK-Dataset-with-Lightroom](https://github.com/yuanming-hu/exposure/wiki/Preparing-data-for-the-MIT-Adobe-FiveK-Dataset-with-Lightroom)
- [DeepLPF](https://github.com/sjmoran/DeepLPF)
- [Image-Adaptive-3DLUT](https://github.com/HuiZeng/Image-Adaptive-3DLUT)

## 3DLUT meshgrid

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

# (x + y + T)**3
coef = pred[:, 0]*T + \
    pred[:, 1]*x + \
    pred[:, 2]*y + \
    pred[:, 3]*x**2 + \
    pred[:, 4]*x*y + \
    pred[:, 5]*y**2 + \
    pred[:, 6]*x**3 + \
    pred[:, 7]*x**2*y + \
    pred[:, 8]*x*y**2 + \
    pred[:, 9]*y**3
            
# (x + y + z + T)**3
LUTs = pred[:, 0]*T + \
    pred[:, 1]*x + \
    pred[:, 2]*y + \
    pred[:, 3]*z + \
    pred[:, 4]*x*x + \
    pred[:, 5]*x*y + \
    pred[:, 6]*x*z + \
    pred[:, 7]*y*y + \
    pred[:, 8]*y*z + \
    pred[:, 9]*z*z + \
    pred[:, 10]*x*x*x + \
    pred[:, 11]*x*x*y + \
    pred[:, 12]*x*x*z + \
    pred[:, 13]*x*y*y + \
    pred[:, 14]*x*y*z + \
    pred[:, 15]*x*z*z + \
    pred[:, 16]*y*y*y + \
    pred[:, 17]*y*y*z + \
    pred[:, 18]*y*z*z + \
    pred[:, 19]*z*z*z

# (x + y + z + T)**5
  LUTs = pred[:, 0]*T + \
  pred[:, 1]*x + \
  pred[:, 2]*y + \
  pred[:, 3]*z + \
  pred[:, 4]*x**2 + \
  pred[:, 5]*x*y + \
  pred[:, 6]*x*z + \
  pred[:, 7]*y**2 + \
  pred[:, 8]*y*z + \
  pred[:, 9]*z**2 + \
  pred[:, 10]*x**3 + \
  pred[:, 11]*x**2*y + \
  pred[:, 12]*x**2*z + \
  pred[:, 13]*x*y**2 + \
  pred[:, 14]*x*y*z + \
  pred[:, 15]*x*z**2 + \
  pred[:, 16]*y**3 + \
  pred[:, 17]*y**2*z + \
  pred[:, 18]*y*z**2 + \
  pred[:, 19]*z**3 + \
  pred[:, 20]*x**4 + \
  pred[:, 21]*x**3*y + \
  pred[:, 22]*x**3*z + \
  pred[:, 23]*x**2*y**2 + \
  pred[:, 24]*x**2*y*z + \
  pred[:, 25]*x**2*z**2 + \
  pred[:, 26]*x*y**3 + \
  pred[:, 27]*x*y**2*z + \
  pred[:, 28]*x*y*z**2 + \
  pred[:, 29]*x*z**3 + \
  pred[:, 30]*y**4 + \
  pred[:, 31]*y**3*z + \
  pred[:, 32]*y**2*z**2 + \
  pred[:, 33]*y*z**3 + \
  pred[:, 34]*z**4 + \
  pred[:, 35]*x**5 + \
  pred[:, 36]*x**4*y + \
  pred[:, 37]*x**4*z + \
  pred[:, 38]*x**3*y**2 + \
  pred[:, 39]*x**3*y*z + \
  pred[:, 40]*x**3*z**2 + \
  pred[:, 41]*x**2*y**3 + \
  pred[:, 42]*x**2*y**2*z + \
  pred[:, 43]*x**2*y*z**2 + \
  pred[:, 44]*x**2*z**3 + \
  pred[:, 45]*x*y**4 + \
  pred[:, 46]*x*y**3*z + \
  pred[:, 47]*x*y**2*z**2 + \
  pred[:, 48]*x*y*z**3 + \
  pred[:, 49]*x*z**4 + \
  pred[:, 50]*y**5 + \
  pred[:, 51]*y**4*z + \
  pred[:, 52]*y**3*z**2 + \
  pred[:, 53]*y**2*z**3 + \
  pred[:, 54]*y*z**4 + \
  pred[:, 55]*z**5 
        
```

# sdr2hdr

## dataset
- [yinfans](https://www.yinfans.me/)
- [bugutv](https://www.bugutv.cn/4kmovie)

## BT709->BT2020

```
os.system(f'/usr/local/bin/ffmpeg -r {fps} -y -f image2 -i {output_path}/%08d_{style_list[style_id]}.png \
    -c:v libx265 -x265-params high-tier=1:profile=main10 \
    -b:v 10M -pix_fmt yuv420p10le -c:a aac -color_primaries bt2020 -colorspace bt2020_ncl -color_trc smpte2084 \
    {os.path.join(output_path, video_name)}')
```

## BT2020->BT709

```
/usr/local/bin/ffmpeg -ss 00:02:55 -to 00:03:10 -y -i ./hdr/videos/Avengers3.mkv \
-pix_fmt yuv420p -color_primaries bt709 -colorspace bt709 -color_trc bt709 \
./Avengers3_sdr.mp4
```

## 10bit->rgb48 or 8bit->rgb48

```
/usr/local/bin/ffmpeg -ss 00:00:00 -to 00:02:00 -y -i ./hdr/videos/hdr.mkv -pix_fmt rgb48 ./hdr/images/%012d.png
/usr/local/bin/ffmpeg -ss 00:00:00 -to 00:02:00 -y -i ./hdr/videos/hdr.mkv -pix_fmt rgb48 ./sdr/images/%012d.png
```
