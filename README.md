# ArcGIS Maps SDK for JavaScript Project

This project demonstrates how to create and display a map using the ArcGIS Maps SDK for JavaScript. The map is centered on the Mariana Trench and uses the "oceans" basemap.

## Prerequisites

- An ArcGIS Location Platform or ArcGIS Online account.
- An API key with the necessary privileges to access the location services.

## Getting Started

### Create a new HTML file

Create an `index.html` file with the following content:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="initial-scale=1, maximum-scale=1, user-scalable=no">
    <title>ArcGIS Maps SDK for JavaScript Tutorials: Display a map</title>
    <style>
        html, body, #viewDiv {
            padding: 0;
            margin: 0;
            height: 100%;
            width: 100%;
        }
    </style>
    <link rel="stylesheet" href="https://js.arcgis.com/4.30/esri/themes/light/main.css">
    <script src="https://js.arcgis.com/4.30/"></script>
</head>
<body>
    <div id="viewDiv"></div>
    <script>
        require(["esri/config", "esri/Map", "esri/views/MapView"], function(esriConfig, Map, MapView) {
            esriConfig.apiKey = "YOUR_ACCESS_TOKEN"; // Replace with your actual access token

            const map = new Map({
                basemap: "oceans" // Change basemap to "oceans"
            });

            const view = new MapView({
                map: map,
                center: [142.2, 11.35], // Longitude, latitude for Mariana Trench
                zoom: 5, // Decreased zoom level
                container: "viewDiv" // Div element
            });

            view.when(() => {
                console.log("Map and View are ready");
            }, (error) => {
                console.error("Error: ", error);
            });
        });
    </script>
</body>
</html>
