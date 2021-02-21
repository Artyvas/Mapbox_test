<template>
  <div class="about">
    <h1>This is an about page</h1>
    <p>The value is {{ value }}</p>
    <div id="map"></div>
  </div>
</template>

<style>
#map {
  width: 100%;
  height: 300px;
}
#marker {
background-image: url('https://docs.mapbox.com/mapbox-gl-js/assets/washington-monument.jpg');
background-size: cover;
width: 50px;
height: 50px;
border-radius: 50%;
cursor: pointer;
}
 
.mapboxgl-popup {
max-width: 200px;
}
</style>
<script>
/* global mapboxgl */
export default {
  data() {
    return {
      value: null,
      options: ["list", "of", "options"],
      places: [
        { lat: 63.07002, lng: -151.00733, description: "Denali - THE Alaskan summie"},
        { lat: 62.95146, lng: -151.08944, description: "Hunter - another sweet Alaskan summie!" },
        { lat: 62.96126, lng: -151.39823, description: "Foraker - also a preeeetty sick Alaskan summie!" }
      ]
    };
  },
  mounted: function() {
    this.setupMap();
  },
  methods: {
    setupMap: function() {
      mapboxgl.accessToken = process.env.VUE_APP_AVMAPBOX_API_KEY;
      var map = new mapboxgl.Map({
        container: "map", // container id
        style: "mapbox://styles/mapbox/outdoors-v11", // style URL
        center: [this.places[0].lng, this.places[0].lat], // starting position [lng, lat]
        zoom: 9, // starting zoom
      });

      this.places.forEach(function(place) {
        var popup = new mapboxgl.Popup({ offset: 25}).setText(
              place.description
            );
        var marker = new mapboxgl.Marker()
            .setLngLat([place.lng, place.lat])
            .setPopup(popup)
            .addTo(map);
        console.log(marker);
      });

        var popup = new mapboxgl.Popup({ offset: 25}).setText(
              'What a nice summie, eh'
            );
        var marker = new mapboxgl.Marker()
            .setLngLat([-151.00733, 63.07002])
            .setPopup(popup)
            .addTo(map);
        console.log(marker);
        console.log(map);
    },
  },
};
</script>
