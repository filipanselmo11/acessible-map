<template>
  <div id="map"></div>
</template>

<script>
import "leaflet/dist/leaflet.css";
import L from "leaflet";
export default {
  name: "MapaComponent",
  data: () => ({
    map: undefined,
  }),
  mounted() {
    this.setupMap();
  },
  methods: {
    setupMap() {
      //   this.map = L.map("map").setView([-3.042602743486333, -59.95165651808512], 13);
      this.map = L.map("map").fitWorld();
      this.map.locate({ setView: true, maxZoom: 16 });
      this.map.on("locationfound", this.onLocationFound);
      this.map.on("locationError", this.onLocationError);
      L.tileLayer("https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png", {
        maxZoom: 19,
        attribution: "© OpenStreetMap",
      }).addTo(this.map);
      L.marker([-3.09163241662778, -60.01723436419292], { alt: "EST" })
        .addTo(this.map)
        .bindPopup("Escola Superior de Tecnologia");
    },
    onLocationFound(e) {
      const radius = e.accuracy;
      //   L.marker(e.latlng)
      //     .addTo(this.map)
      //     .bindPopup("You are within " + radius + " meters from this point")
      //     .openPopup();
      L.circle(e.latlng, radius).addTo(this.map);
    },
    onLocationError(e) {
      alert(e.message);
    },
  },
};
</script>

<style>
#map {
  width: 80vw;
  height: 100vh;
}
</style>
