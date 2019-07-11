# foxhole-router

View Demo of one map here: https://foxholestats.com/router/ , but we want it over the whole world !


To view or help map all the roads in game foxhole: (Once setup a map will take about 1 hour to 'catalog')

Install QGIS from here: https://qgis.org/en/site/forusers/download.html (standalone) and open the program icon/version without "GRASS", QGIS Desktop 3.8.0

Add the world map background layer: 
* Browser->XYZ Tiles (rightclick)->New Connection
* Give it a name like "Foxhole World Map" and specify the url as 
* https://raw.githubusercontent.com/Kastow/Foxhole-Map-Tiles/master/Tiles/{z}/{z}_{x}_{y}.png
* Set min zoom to 0 and max to 5, Choose OK
* Double click newly added connection to add it your project/map. You should now see the foxhole world map.

Add hex grid border lines for reference:
 * Layer->Add Layer->Vector Layer
 * Source Type = Protocol HTTP
 * Type = GEOJSON
 * URI = https://raw.githubusercontent.com/hayden-t/foxhole-router/master/hexGridBorders.geojson
 * If this fails with error, save the file locally and add it from there.
  
 If you want for reference or examination you can add map geojson's already done from this repository.
  
  To start mapping a new region: (Please contact us to select a map, eg discord, or issues, so we dount double up)
  
  Turn on Snapping:
   * View->Toolbars->Snapping, Then click Magnet Icon to enable.  
  
  Create a new layer:
   * Click Layer->Create Layer->New Shapefile    
   * Filename = Choose file save location, naming it the map you are working on.
   *  Geometry Type = Line
   * Additional = Project CRS EPSG 3857 WGS 84
   * OK
   
 Hide form by default: 
 * Right click Layer->Properties->Form->"Hide Form on add feature" (top right)
 * (optionally also change line style to something easy to see, like "topo road"}

  Start mapping:
   * With new layer selected, click "Toggle Editing" button, & click "Add Line Feature" button,
   * Start clicking along the roads making sure to make a click/vertex point at each intersection, right click to end line.
   * Keep adding lines, for each road segment until taking a break or done, "Toggle Editing" off, and click save
   * You can also use the "Vertex Tool" to adjust or remove points.
   * At border edges end your lines on border line (hex grid)
   
   To share work export layer as geojson, but keep your original project and shape files.

    
Map Assignment List
 * AllodsBightHex
 * CallahansPassageHex
 * DeadLandsHex
 * DrownedValeHex
 * EndlessShoreHex
 * FarranacCoastHex - Leo
 * FishermansRowHex
 * GodcroftsHex		
 * GreatMarchHex
 * HeartlandsHex
 * LinnMercyHex
 * LochMorHex
 * MarbanHollow -> Hayden
 * MooringCountyHex
 * OarbreakerHex
 * ReachingTrailHex
 * ShackledChasmHex
 * StonecradleHex
 * TempestIslandHex
 * UmbralWildwoodHex
 * ViperPitHex
 * WeatheredExpanseHex -> Derp
 * WestgateHex

If you've read this far you may be interested in this :)
https://en.wikipedia.org/wiki/Null_Island

   
   These following are dev notes:
   
   QGIS's default line type is MultiLineString but the routing library needs LineString, so this can be converted when needed at the end: Vector->Geometry Tools->Multi Parts to Single Parts
   Also when exporting json for web use, change precision to 0 to save filesize, we dont need that accuracy, likely in post we can write a script to even further shorten the cord data length.
   Also i used in my demo the vector geometry "densify" tool to add more points along lines.
   If you want demo source let me know, im looking for help with it.
   Libs:

   http://www.liedman.net/geojson-path-finder/
   http://www.liedman.net/leaflet-routing-machine/
   
