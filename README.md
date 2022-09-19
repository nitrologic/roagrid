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

  https://roa.nz/roagrid/%name%/%layer%/%col%/%row%.json

  https://roa.nz/topogrid/topo-%name%/%layer%/%col%/%row%.raw

  https://roa.nz/aerialgrid/%name%/%layer%/%col%/%row%.jpg

A second faster AWS instance at http://mojolabs.nz is serving same dataset minus encryption. (NEW)

## Contributors

Image data courtesy Land Information New Zealand

https://data.linz.govt.nz/

LICENSE: Creative Commons Attribution 4.0 International

https://data.linz.govt.nz/license/attribution-4-0-international/

## Resolution

The metric real world dimension of tiles at each level are

Level | Metric Size
------| ---------
0 | 64 meters²
1 | 512 meters²
2 | 4096 meters²
3 | 32768 meters²
4 | 262144 meters²
5 | 2097152 meters²

## Encoding

Aerial data is compressed 2K resolution with JPEG compression value of 85.

Topo data is uncompressed raw integer array 1052676 bytes. Binary encoding is 2 x 16 bit unsigned 

Json outline encoding is based on a 2K resolution target canvas.

## Examples

https://roa.nz/aerialgrid/aerial-auckland2017/1/3432/11556.jpg

![https://roa.nz/aerialgrid/aerial-auckland2017/1/3432/11556.jpg](https://roa.nz/aerialgrid/aerial-auckland2017/1/3432/11556.jpg)


https://roa.nz/roagrid/roof/1/3432/11556.json

https://roa.nz/topogrid/topo-auckland-north/1/3432/11556.raw
