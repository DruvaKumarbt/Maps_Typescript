# Maps_Typescript

This is Simple *Select and Shatre* application.

The application uses google maps API to render the maps.
Using Google Maps unfortunately requires a credit card, even though you got a generous free tier which you very likely wouldn't exceed.

If you got no credit card, you can look into OpenLayers as an alternative (here's how to render a map with it: https://openlayers.org/en/latest/doc/quickstart.html).

In our concrete example, this would render a map:
Include this in your HTML file:

 `<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/openlayers/openlayers.github.io@master/en/v6.1.1/css/ol.css" type="text/css">
    <script src="https://cdn.jsdelivr.net/gh/openlayers/openlayers.github.io@master/en/v6.1.1/build/ol..js"></script>`
    
In `app.ts`, use this code:

`declare var ol: any;
 function searchAddressHandler(event: Event) {
  event.preventDefault();
  const coordinates = {lat: 40.41, lng: -73.99}; // Can't fetch coordinates from Google API, use dummy ones
  document.getElementById('map')!.innerHTML = ''; // clear <p> from <div id="map">
  new ol.Map({
    target: 'map',
    layers: [
      new ol.layer.Tile({
        source: new ol.source.OSM()
      })
    ],
    view: new ol.View({
      center: ol.proj.fromLonLat([coordinates.lng, coordinates.lat]),
      zoom: 16
    })
  });
}`

The above example uses the hardcoded value.
You can explore the OpenLayers docs to learn how to render a broad variety of different things.
