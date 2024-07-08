# latest

Hurrah! 

After hiatus nitrologic pipeline 1.95 is baking again.

Stay tuned, 2024 endpoints coming soon.

## July 2024 Tile Audit 

roa: 4,606,799 (shape)

lidar: 163,454 (height)

aerial: 1,928,826 (image)

## Current Shape Layers (11)

coast 
rivers 
waters 
land 
transit 
buildings 
ramm 
power 
marine 
leisure 
parcels

# roagrid - Toitū Te Whenua

This repository is part of Simon's topographic tile services.

Image and contour data originate from Crown Copyright sources paid for by the New Zealand public and released with Community Commons Attribution license.

The documentation below is a work in progress as various applications are added to the platform.

# random tile 

![coast](
sentinel2-nz2022-3-63-177.jpg)

## Grid

North is +y

East is +x

Coordinates are in [NZTM](https://www.linz.govt.nz/guidance/geodetic-system/coordinate-systems-used-new-zealand/projections/new-zealand-transverse-mercator-2000-nztm2000) projection.

Bounds are inclusive and in [W E S N] order until further notice.

Masks use base64 encoding of north is top bitmap where bit indicates availability of tile data inside bounds.

Topo data features integer heightmaps where height is 16 units per meter for all levels.

## Tile Size

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

## Gridding

The grid.json file is included for purposes of converting WGS84 spherical coordinate to NZTM metric.

```
let AppGrid;

function WGS2NZTM(latlon){
	const lat=latlon[0];
	const lon=latlon[1];
	const grid=AppGrid.wgsNZTM;
	const y=grid.bounds[2]-lat;
	const x=lon-grid.bounds[0];
	const yy=(y/grid.increment)|0;
	const xx=(x/grid.increment)|0;
	const row=grid.meters[yy];
	return [row[xx*2+0],row[xx*2+1]];
}

function NZTM2WGS(northeast){
	const n=northeast[0];
	const e=northeast[1];
	const grid=AppGrid.nztmWGS;
	const y=n-grid.bounds[2];
	const x=e-grid.bounds[0];
	const yy=(y/grid.increment)|0;
	const xx=(x/grid.increment)|0;
	const row=grid.degrees[yy];
	return [row[xx*2+0],row[xx*2+1]];
}

function fetchGrid(){
	const url="json/grid.json";
	fetch(url).then(response=>response.json()).then(
		_grid=>{
			AppGrid=_grid;		
			const ne=WGS2NZTM([-40,174]);
			const latlon=NZTM2WGS(ne);
		},_error=>{
			console.log("fetchGrid fail epix");
		}
	);
}

```

## Contributors

Image data courtesy Land Information New Zealand

https://data.linz.govt.nz/

LICENSE: Creative Commons Attribution 4.0 International

https://data.linz.govt.nz/license/attribution-4-0-international/
