<script lang="ts">
  import MapLibre from '$lib/MapLibre.svelte';
  import CodeSample from '$site/CodeSample.svelte';
  import code from './+page.svelte?raw';
  import type { PageData } from './$types';

  export let data: PageData;

  let styles = [
    'https://basemaps.cartocdn.com/gl/positron-gl-style/style.json',
    'https://basemaps.cartocdn.com/gl/voyager-gl-style/style.json',
  ];

  function swapStyle() {
    styles = [...styles].reverse();
  }
</script>

<button class="btn variant-filled mb-4" type="button" on:click={swapStyle}>Swap Style</button>

<MapLibre
  style={styles[0]}
  class="relative w-full aspect-[9/16] max-h-[70vh] sm:max-h-full sm:aspect-video"
  standardControls
/>

<CodeSample {code} startBoundary="let styles" endBoundary="/>" />
