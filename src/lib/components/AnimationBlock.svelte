<script lang="ts">
  import HeigthEasing from "./HeigthEasing.svelte";
  import MovementEasing from "./MovementEasing.svelte";
  import RotateEasing from "./RotateEasing.svelte";
  import ScaleEasing from "./ScaleEasing.svelte";
  import WidthEasing from "./WidthEasing.svelte";
  export let currentEasingType: string | any;
  export let curveCSS: string;
</script>

<div class="animation__wrapper">
  <h3 class="title">animation</h3>
  <MovementEasing {curveCSS} {currentEasingType} />
  <WidthEasing {curveCSS} {currentEasingType} />
  <HeigthEasing {curveCSS} {currentEasingType} />
  <ScaleEasing {curveCSS} {currentEasingType} />
  <RotateEasing {curveCSS} {currentEasingType} />
</div>

<style>
  .title {
    color: #fff;
  }
</style>
