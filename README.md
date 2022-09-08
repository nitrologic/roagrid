# roagrid
New Zealand topography tile service

## Contributors

Image data courtesy Land Information New Zealand

https://data.linz.govt.nz/

LICENSE: Creative Commons Attribution 4.0 International

https://data.linz.govt.nz/license/attribution-4-0-international/

## Encoding

Aerial data is compressed 2K resolution with JPEG compression value of 85.

Topo data was uncompressed 32 bit PNG with overlapping resolution of 513 pixels square. ARGB encoding in which G B channels are Altitude (16 bit), top 3 bits of A are reserved, remaining A and R channels are Height (13 bits) and units are 16 per meter.

Topo data is now raw integer array.

## Available Layers

Coming soon...

## Examples

https://roa.nz/roagrid/aerial-ak2017/1/3432/11556.jpg

![https://roa.nz/roagrid/aerial-ak2017/1/3432/11556.jpg](https://roa.nz/roagrid/aerial-ak2017/1/3432/11556.jpg)

https://roa.nz/roagrid/lidar-ak2013/1/3432/11556.dif.png
![https://roa.nz/roagrid/lidar-ak2013/1/3432/11556.dif.png](https://roa.nz/roagrid/lidar-ak2013/1/3432/11556.dif.png)

