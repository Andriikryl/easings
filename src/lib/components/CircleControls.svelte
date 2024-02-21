<script lang="ts">
  export let startHandleX: number;
  export let startHandleY: number;
  export let endHandleX: number;
  export let endHandleY: number;
  export let startHandle: SVGElement | null;
  export let endHandle: SVGElement | null;
</script>

<circle
  class="current-curve__handle"
  bind:this={startHandle}
  cx={startHandleX}
  cy={startHandleY}
  r="5"
/>
<circle
  class="current-curve__handle"
  bind:this={endHandle}
  cx={endHandleX}
  cy={endHandleY}
  r="5"
/>

<style>
  .current-curve__handle {
    fill: #fb6f92;
    stroke: #ffb3c6;
    stroke-width: 1px;
  }
</style>
