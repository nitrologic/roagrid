# roagrid
Simon's topography tile service

## Grid

North is +y

East is +x

## Endpoints

Server provides data, topo, and aerial tiles where indicated in mask

  https://roa.nz/roagrid/%name%/%layer%/%col%/%row%.json

  https://roa.nz/topogrid/topo-%name%/%layer%/%col%/%row%.raw

  https://roa.nz/aerialgrid/%name%/%layer%/%col%/%row%.jpg

## Contributors

Image data courtesy Land Information New Zealand

https://data.linz.govt.nz/

LICENSE: Creative Commons Attribution 4.0 International

https://data.linz.govt.nz/license/attribution-4-0-international/

## Encoding

Aerial data is compressed 2K resolution with JPEG compression value of 85.

Topo data is uncompressed raw integer array.

## Available Layers

Coming soon...

## Examples

https://roa.nz/roagrid/aerial-auckland2017/1/3432/11556.jpg

![https://roa.nz/roagrid/aerial-auckland2017/1/3432/11556.jpg](https://roa.nz/roagrid/aerial-auckland2017/1/3432/11556.jpg)

