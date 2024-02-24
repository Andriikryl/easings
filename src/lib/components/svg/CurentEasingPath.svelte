<script lang="ts">
  export let startHandleX: number;
  export let startHandleY: number;
  export let endHandleX: number;
  export let endHandleY: number;
</script>

<path
  class="current-curve__curve"
  d="M20,200 C{startHandleX},{startHandleY} {endHandleX},{endHandleY} 120,100"
/>

<style>
  .current-curve__curve {
    fill: none;
    stroke: #e63946;
    stroke-width: 2px;
    pointer-events: none;
  }
</style>
