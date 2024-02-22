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
  <h3 class="title">animation exemples</h3>
  <MovementEasing {curveCSS} {currentEasingType} />
  <WidthEasing {curveCSS} {currentEasingType} />
  <HeigthEasing {curveCSS} {currentEasingType} />
  <ScaleEasing {curveCSS} {currentEasingType} />
  <RotateEasing {curveCSS} {currentEasingType} />
</div>

<style>
  .animation__wrapper {
    margin-block-start: 30px;
  }
  .title {
    padding: 12px;
    border-radius: 8px;
    background: var(--gray-1, #eee);
    margin-block-end: 20px;
    padding: 32px;
    text-align: center;
    color: var(--black, #1b1b1b);
    font-family: Patrick Hand;
    font-size: 30px;
    font-style: normal;
    font-weight: 400;
    line-height: normal;
    letter-spacing: -0.3px;
    text-transform: uppercase;
  }
</style>
