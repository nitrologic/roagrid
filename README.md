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

A second faster AWS instance at http://mojolabs.nz is serving same dataset sans encyption. (NEW)

## Contributors

Image data courtesy Land Information New Zealand

https://data.linz.govt.nz/

LICENSE: Creative Commons Attribution 4.0 International

https://data.linz.govt.nz/license/attribution-4-0-international/

## Encoding

Aerial data is compressed 2K resolution with JPEG compression value of 85.

Topo data is uncompressed raw integer array 1052676 bytes.

Json outline encoding is based on a 2K resolution target canvas.

## Examples

https://roa.nz/aerialgrid/aerial-auckland2017/1/3432/11556.jpg

![https://roa.nz/aerialgrid/aerial-auckland2017/1/3432/11556.jpg](https://roa.nz/aerialgrid/aerial-auckland2017/1/3432/11556.jpg)


https://roa.nz/roagrid/roof/1/3432/11556.json

https://roa.nz/topogrid/topo-auckland-north/1/3432/11556.raw
