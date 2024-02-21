<script lang="ts">
  export let startHandleX: number;
  export let startHandleY: number;
  export let endHandleX: number;
  export let endHandleY: number;
</script>

<line
  class="current-curve__handle-tether"
  x1="20"
  y1="200"
  x2={startHandleX}
  y2={startHandleY}
  stroke="#34657f"
/>
<line
  class="current-curve__handle-tether"
  x1="120"
  y1="100"
  x2={endHandleX}
  y2={endHandleY}
  stroke="#34657f"
/>

<style>
  .current-curve__handle-tether {
    pointer-events: none;
    stroke-width: 1px;
  }
  line {
    touch-action: none;
    user-select: none;
  }
</style>
