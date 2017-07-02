# Leaflet.js map
Gennady Kalashnikov  
02 July, 2017  

## Treasure Map
### Source code

```r
library(leaflet)

set.seed(1234567)

iconNorth <- makeIcon(
  iconUrl = "http://upload.wikimedia.org/wikipedia/commons/4/4a/Arrow_north.svg",
  iconWidth = 12, iconHeight = 32
)
iconSouth <- makeIcon(
  iconUrl = "http://upload.wikimedia.org/wikipedia/commons/f/ff/Arrow_south.svg",
  iconWidth = 12, iconHeight = 32
)
iconWest <- makeIcon(
  iconUrl = "http://upload.wikimedia.org/wikipedia/commons/9/9f/Arrow_west.svg",
  iconWidth = 32, iconHeight = 12
)
iconEast <- makeIcon(
  iconUrl = "http://upload.wikimedia.org/wikipedia/commons/7/71/Arrow_east.svg",
  iconWidth = 32, iconHeight = 12
)

getMarkers <- function(n) {
  data.frame(lat = runif(n, min = 20.037689, max = 20.081873),
             lng = runif(n, min = -72.875710, max = -72.788840))
}

markersNorth <- getMarkers(4)
markersSouth <- getMarkers(4)
markersWest <- getMarkers(4)
markersEast <- getMarkers(4)

map <- markersNorth %>% leaflet() %>% addTiles() %>% addMarkers(icon = iconNorth)

map <- addMarkers(map, lng = markersNorth$lng, lat = markersNorth$lat, icon = iconNorth, popup = rep("\"Go North\"", nrow(markersNorth)))
map <- addMarkers(map, lng = markersSouth$lng, lat = markersSouth$lat, icon = iconSouth, popup = rep("\"Go South\"", nrow(markersSouth)))
map <- addMarkers(map, lng = markersWest$lng, lat = markersWest$lat, icon = iconWest, popup = rep("\"Go West\"", nrow(markersWest)))
map <- addMarkers(map, lng = markersEast$lng, lat = markersEast$lat, icon = iconEast, popup = rep("\"Go East\"", nrow(markersEast)))

circles <- data.frame(lat = runif(4, min = 20.037689, max = 20.081873),
                      lng = runif(4, min = -72.875710, max = -72.788840),
                      col = sample(c("red", "red", "blue", "blue"), 4, replace = FALSE),
                      stringsAsFactors = FALSE)

map <- addCircleMarkers(map, lng = circles$lng, lat = circles$lat, color = circles$col)

map <- addLegend(map, labels = c("Marker", "Pitfall", "Skeleton"), colors = c("black", "red", "blue"))

boxIcon <- makeIcon(
  iconUrl = "http://upload.wikimedia.org/wikipedia/commons/a/a4/Treasure_chest_color.png",
  iconWidth = 32, iconHeight = 32
)

map <- addMarkers(map,
  lng = -72.838493,
  lat = 20.059758,
  icon = boxIcon,
  popup = c("Expected treasure chest location")
)

map
```

### Map
<!--html_preserve--><div id="htmlwidget-97231983b35293da598c" style="width:672px;height:480px;" class="leaflet html-widget"></div>
<script type="application/json" data-for="htmlwidget-97231983b35293da598c">{"x":{"options":{"crs":{"crsClass":"L.CRS.EPSG3857","code":null,"proj4def":null,"projectedBounds":null,"options":{}}},"calls":[{"method":"addTiles","args":["//{s}.tile.openstreetmap.org/{z}/{x}/{y}.png",null,null,{"minZoom":0,"maxZoom":18,"maxNativeZoom":null,"tileSize":256,"subdomains":"abc","errorTileUrl":"","tms":false,"continuousWorld":false,"noWrap":false,"zoomOffset":0,"zoomReverse":false,"opacity":1,"zIndex":null,"unloadInvisibleTiles":null,"updateWhenIdle":null,"detectRetina":false,"reuseTiles":false,"attribution":"&copy; <a href=\"http://openstreetmap.org\">OpenStreetMap<\/a> contributors, <a href=\"http://creativecommons.org/licenses/by-sa/2.0/\">CC-BY-SA<\/a>"}]},{"method":"addMarkers","args":[[20.0625319328659,20.0697886099185,20.0781283994504,20.0390010160644],[-72.8090364320346,-72.8340077108871,-72.8680324641406,-72.800745892675],{"iconUrl":{"data":"http://upload.wikimedia.org/wikipedia/commons/4/4a/Arrow_north.svg","index":0},"iconWidth":12,"iconHeight":32},null,null,{"clickable":true,"draggable":false,"keyboard":true,"title":"","alt":"","zIndexOffset":0,"opacity":1,"riseOnHover":false,"riseOffset":250},null,null,null,null,null,null,null]},{"method":"addMarkers","args":[[20.0625319328659,20.0697886099185,20.0781283994504,20.0390010160644],[-72.8090364320346,-72.8340077108871,-72.8680324641406,-72.800745892675],{"iconUrl":{"data":"http://upload.wikimedia.org/wikipedia/commons/4/4a/Arrow_north.svg","index":0},"iconWidth":12,"iconHeight":32},null,null,{"clickable":true,"draggable":false,"keyboard":true,"title":"","alt":"","zIndexOffset":0,"opacity":1,"riseOnHover":false,"riseOffset":250},["\"Go North\"","\"Go North\"","\"Go North\"","\"Go North\""],null,null,null,null,null,null]},{"method":"addMarkers","args":[[20.0596309094714,20.0754002220219,20.0653432325428,20.0483573374859],[-72.8724358918755,-72.8308335686252,-72.8046105637774,-72.8326984955062],{"iconUrl":{"data":"http://upload.wikimedia.org/wikipedia/commons/f/ff/Arrow_south.svg","index":0},"iconWidth":12,"iconHeight":32},null,null,{"clickable":true,"draggable":false,"keyboard":true,"title":"","alt":"","zIndexOffset":0,"opacity":1,"riseOnHover":false,"riseOffset":250},["\"Go South\"","\"Go South\"","\"Go South\"","\"Go South\""],null,null,null,null,null,null]},{"method":"addMarkers","args":[[20.045595375757,20.0765330202041,20.0570124640739,20.0697785688197],[-72.8005875515685,-72.8497265495669,-72.7941900144538,-72.8386800786005],{"iconUrl":{"data":"http://upload.wikimedia.org/wikipedia/commons/9/9f/Arrow_west.svg","index":0},"iconWidth":32,"iconHeight":12},null,null,{"clickable":true,"draggable":false,"keyboard":true,"title":"","alt":"","zIndexOffset":0,"opacity":1,"riseOnHover":false,"riseOffset":250},["\"Go West\"","\"Go West\"","\"Go West\"","\"Go West\""],null,null,null,null,null,null]},{"method":"addMarkers","args":[[20.0532698500294,20.0562615969213,20.0513436775935,20.0408251828232],[-72.8501570392839,-72.8059694097325,-72.8143742271945,-72.7910783072791],{"iconUrl":{"data":"http://upload.wikimedia.org/wikipedia/commons/7/71/Arrow_east.svg","index":0},"iconWidth":32,"iconHeight":12},null,null,{"clickable":true,"draggable":false,"keyboard":true,"title":"","alt":"","zIndexOffset":0,"opacity":1,"riseOnHover":false,"riseOffset":250},["\"Go East\"","\"Go East\"","\"Go East\"","\"Go East\""],null,null,null,null,null,null]},{"method":"addCircleMarkers","args":[[20.0408918198906,20.0818114787278,20.0618379553868,20.0461394696795],[-72.8371357814,-72.8183434411612,-72.8307386539427,-72.8027817903622],10,null,null,{"lineCap":null,"lineJoin":null,"clickable":true,"pointerEvents":null,"className":"","stroke":true,"color":["red","blue","red","blue"],"weight":5,"opacity":0.5,"fill":true,"fillColor":["red","blue","red","blue"],"fillOpacity":0.2,"dashArray":null},null,null,null,null,null,null,null]},{"method":"addLegend","args":[{"colors":["black","red","blue"],"labels":["Marker","Pitfall","Skeleton"],"na_color":null,"na_label":"NA","opacity":0.5,"position":"topright","type":"unknown","title":null,"extra":null,"layerId":null,"className":"info legend"}]},{"method":"addMarkers","args":[20.059758,-72.838493,{"iconUrl":{"data":"http://upload.wikimedia.org/wikipedia/commons/a/a4/Treasure_chest_color.png","index":0},"iconWidth":32,"iconHeight":32},null,null,{"clickable":true,"draggable":false,"keyboard":true,"title":"","alt":"","zIndexOffset":0,"opacity":1,"riseOnHover":false,"riseOffset":250},"Expected treasure chest location",null,null,null,null,null,null]}],"limits":{"lat":[20.0390010160644,20.0818114787278],"lng":[-72.8724358918755,-72.7910783072791]}},"evals":[],"jsHooks":[]}</script><!--/html_preserve-->
