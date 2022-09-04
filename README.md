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


## No Longer Supported

Based on NZTM mapping

### layers.json

```
const _ak2017_1={
	level:1,
	bitmap:"aerial-ak2017/1",
	extension:".jpg",
	heightmap:"lidar-ak2013/1",
	x:3431,
	y:11557,
	left:3370,bottom:11467,right:3525,top:11572
};

const _nz2={
	level:2,
	bitmap:"sat-nz2021/2",
	extension:".jpg",
	heightmap:"lidar-nz2012/2",
	x:383.5,
	y:1510,
	left:264,bottom:1187,right:510,top:1520
};

const _nz3={
	level:3,
	bitmap:"sat-nz2021/3",
	extension:".jpg",
	heightmap:"lidar-nz2012/3",
	x:39,
	y:153,
	left:32,bottom:145,right:64,top:155
};

const _nz4={
	level:4,
	bitmap:"sat-nz2021/4",
	extension:".jpg",
	heightmap:"lidar-nz2012/4",
	x:5,
	y:18,
	left:4,bottom:18,right:7,top:23
};

const _nz5={
	level:5,
	bitmap:"sat-nz2021/5",
	extension:".jpg",
	heightmap:"lidar-nz2012/5",
	x:0.8,
	y:1.8,
	left:0,bottom:2,right:0,top:2
};
```

## Examples

https://roa.nz/roagrid/aerial-ak2017/1/3432/11556.jpg

![https://roa.nz/roagrid/aerial-ak2017/1/3432/11556.jpg](https://roa.nz/roagrid/aerial-ak2017/1/3432/11556.jpg)

https://roa.nz/roagrid/lidar-ak2013/1/3432/11556.dif.png
![https://roa.nz/roagrid/lidar-ak2013/1/3432/11556.dif.png](https://roa.nz/roagrid/lidar-ak2013/1/3432/11556.dif.png)

