<script lang="ts">
  import { onMount } from "svelte";

  import Map from "ol/Map";
  import View from "ol/View";
  import TileLayer from "ol/layer/Tile";
  import OSM from "ol/source/OSM";
  import Overlay from "ol/Overlay";
  import { fromLonLat } from "ol/proj";

  const center = fromLonLat([-74.5465931, 40.6943]);
  let mapTarget: HTMLElement;

  onMount(() => {
    const map: Map = new Map({
      target: mapTarget,
      layers: [
        new TileLayer({
          source: new OSM({
            attributions: [],
          }),
        }),
      ],
      view: new View({
        center,
        zoom: 17,
      }),
      overlays: [
        new Overlay({
          position: fromLonLat([-74.5465931, 40.6948376]),
          positioning: "center-center",
          stopEvent: false,
          element: document.getElementById("test") ?? undefined,
        }),
      ],
    });
  });
</script>

<div class="map" bind:this={mapTarget} />
<div id="test">hi</div>

<style>
  .map {
    height: 400px;
    border-radius: 10px;
  }
</style>
