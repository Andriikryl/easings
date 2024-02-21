<script lang="ts">
  export let bezierCoordinates: string;
</script>

<g
  class="current-curve__moving-circle-wrapper"
  style="--bezierCoordinates: {bezierCoordinates}"
>
  <circle class="current-curve__moving-circle" cx="20" cy="200" r="8" />
</g>

<style>
  .current-curve__moving-circle {
    fill: #e63946;
  }
  .current-curve__moving-circle,
  .current-curve__moving-circle-wrapper {
    animation-name: move;
    animation-duration: 1.5s;
    animation-fill-mode: forwards;
    animation-timing-function: linear;
    animation-iteration-count: infinite;
    animation-direction: alternate-reverse;
    pointer-events: none;
  }

  .current-curve__moving-circle-wrapper {
    animation-name: move_up;
    animation-timing-function: cubic-bezier(var(--bezierCoordinates));
  }
  @keyframes move {
    0%,
    20% {
      transform: translateX(0);
    }
    80%,
    100% {
      transform: translateX(71.45%);
    }
  }

  @keyframes move_up {
    0%,
    20% {
      transform: translateY(0);
    }
    80%,
    100% {
      transform: translateY(-33.33%);
    }
  }
</style>
