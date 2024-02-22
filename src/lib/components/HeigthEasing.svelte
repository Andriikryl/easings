<script lang="ts">
  import LiniarEasing from "./LiniarEasing.svelte";
  export let currentEasingType: string | any;
  export let curveCSS: string;
</script>

<div class="movement__box">
  <h4 class="movement__title">Heigth</h4>
  <LiniarEasing type={"height"} />

  <h3 class="curent__title">{currentEasingType?.title || "custom"}</h3>
  <div class="playground">
    <div class="box__curent" style="--bize: {curveCSS}"></div>
  </div>
</div>

<style>
  .movement__title {
    font-weight: bold;
    font-size: 40px;
    font-family: HelveticaNowDisplay, "Helvetica Neue Light", "Helvetica Neue",
      Helvetica, Arial, "Lucida Grande", sans-serif;
    background-color: #ffff;
    padding: 8px;
    text-decoration: none;
    margin-block-end: 10px;
  }
  .movement__box {
    border: 1px solid #ffc300;
    padding: 20px;
    margin-block-end: 20px;
  }
  .curent__title {
    font-weight: bold;
    font-size: 40px;
    font-family: HelveticaNowDisplay, "Helvetica Neue Light", "Helvetica Neue",
      Helvetica, Arial, "Lucida Grande", sans-serif;
    color: rgb(255, 255, 255);
    text-decoration: none;
    margin-block-end: 10px;
  }
  .box__curent {
    --size: 50px;
    width: var(--size);
    height: var(--size);
    border: 2px solid tomato;
    animation: move__curent 1500ms var(--bize) infinite;
  }
  .playground {
    display: grid;
    place-items: center;
    width: 300px;
    height: 300px;
    padding-block: 20px;
    padding-inline: 10px;
    border: 1px solid var(--lighterGray);
    background: repeating-linear-gradient(
        to bottom,
        hsl(182, 43%, 76%, 0.4),
        hsl(182, 43%, 76%, 0.4) 1px,
        transparent 1px,
        transparent 10.14%
      ),
      repeating-linear-gradient(
        to right,
        hsl(182, 43%, 76%, 0.4),
        hsl(182, 43%, 76%, 0.4) 1px,
        transparent 1px,
        transparent 10.14%
      );
    border-radius: 10px;
  }

  @keyframes move__curent {
    0% {
      transform: scaleY(1);
    }

    50% {
      transform: scaleY(5);
    }
    100% {
      transform: scaleY(1);
    }
  }
</style>
