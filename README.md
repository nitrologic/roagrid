# roagrid
Simon's topography tile service

## Grid

North is +y

East is +x

Bounds are inclusive and in [W E S N] order until further notice.

Masks use Chr(88) X character to indicate availability in bounds and are listed North to South. 

Topo data features integer heightmaps where height is 16 units per meter for all levels.

## Endpoints

Project Roa server provides data, topo, and aerial tiles where indicated in master tiles.json mask.

### Aerial tiles 2048x2048

  https://roa.nz/aerialgrid/%name%/%layer%/%col%/%row%.jpg

### HD Aerial tiles 4096x4096

  https://roa.nz/hd-aerialgrid/%name%/%layer%/%col%/%row%.jpg
  
### SD Aerial tiles 1024x1024  

  https://roa.nz/sd-aerialgrid/%name%/%layer%/%col%/%row%.jpg

### Heightmap tiles

  https://roa.nz/topogrid/%name%/%layer%/%col%/%row%.raw

### Outline tiles

  https://roa.nz/roagrid/%name%/%layer%/%col%/%row%.json

## Resolution

Metric real world dimension of tiles at each level are

Level | Metric Size
------| ---------
0 | 64 meters²
1 | 512 meters²
2 | 4096 meters²
3 | 32768 meters²
4 | 262144 meters²
5 | 2097152 meters²

## Encoding

Aerial data of 2K, 4K and 1K resolutions with JPEG compression (85%, 92% and 80% respectively).

Topo data is uncompressed raw integer array 1052676 bytes (513 x 513 x (16bit + 16bit)) 

Json outline encoding is based on a 2K resolution target canvas.

## Topo Delivery

Server response to http GET on topogrid endpoints has hardcoded contentEncoding="gzip".

Resolution of data can be deduced from contentLength:

Resolution | Content Length
-----------| --------------
1 | 4
129 | 264196
513 | 1052676 
1025 | 4202500
2049 | 16793604

## Topo Encoding

[ Work in progress ] 

```
const SeaLevel=186*16;
const TopoLevel=0x4000;

		for(let y=0;y<res;y++){
			for(let x=0;x<res;x++){
				let h=(bytes[p+1]<<8)+bytes[p+0];
				if(h==0) h=SeaLevel;
				h=(h-SeaLevel);	
				topo[i]=h-TopoLevel;
				let d=(bytes[p+3]<<8)+bytes[p+2];
				d=(d&0x7fff);
				if(d==0x7fff) d=0;
				if(d) {
					d=d-0x1000;
				}
				diff[i]=d;
				i++;
				p+=4;
			}
		}
```

## Examples

https://roa.nz/aerialgrid/aerial-auckland2017/1/3432/11556.jpg

![https://roa.nz/aerialgrid/aerial-auckland2017/1/3432/11556.jpg](https://roa.nz/aerialgrid/aerial-auckland2017/1/3432/11556.jpg)


https://roa.nz/roagrid/roof/1/3432/11556.json

https://roa.nz/topogrid/topo-auckland-north/1/3432/11556.raw


## Contributors

Image data courtesy Land Information New Zealand

https://data.linz.govt.nz/

LICENSE: Creative Commons Attribution 4.0 International

https://data.linz.govt.nz/license/attribution-4-0-international/
