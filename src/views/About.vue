<template>
  <div class="about">
    <h1>This is an about page</h1>
  </div>
  
</template>
<body>
<div id='map' style='width: 400px; height: 300px;'></div>
<script>

mapboxgl.accessToken = 'pk.eyJ1IjoiYXJ0ZW12YXMiLCJhIjoiY2tsZmN6dTV5MGlocDJvb2k5ZWt2dmF0bSJ9.oHMAYMC2QDhIq7Uj6Paxqw';
var map = new mapboxgl.Map({
container: 'map', // container ID
style: 'mapbox://styles/mapbox/streets-v11', // style URL
center: [-74.5, 40], // starting position [lng, lat]
zoom: 9 // starting zoom
});
</script>
</body>
