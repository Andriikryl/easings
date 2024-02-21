<script lang="ts">
  type AnimationProps =
    | "movement"
    | "width"
    | "height"
    | "scale"
    | "rotate"
    | "opacity";
  export let type: AnimationProps;
</script>

{#if type === "movement"}
  <div class="container">
    <h3 class="curent__title">Liniar</h3>
    <div class="playground">
      <div class="box"></div>
    </div>
  </div>
{/if}
{#if type === "width"}
  <div class="container">
    <h3 class="curent__title">Liniar</h3>
    <div class="playground | play__width">
      <div class="box__width"></div>
    </div>
  </div>
{/if}
{#if type === "height"}
  <div class="container">
    <h3 class="curent__title">Liniar</h3>
    <div class="playground | play__height">
      <div class="box__height"></div>
    </div>
  </div>
{/if}

<style>
  .playground {
    width: 100%;
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

  .curent__title {
    font-weight: bold;
    font-size: 40px;
    font-family: HelveticaNowDisplay, "Helvetica Neue Light", "Helvetica Neue",
      Helvetica, Arial, "Lucida Grande", sans-serif;
    color: rgb(255, 255, 255);
    text-decoration: none;
    margin-block-end: 10px;
  }
  .container {
    margin-block-end: 20px;
  }

  .box {
    --size: 50px;
    width: var(--size);
    height: var(--size);
    border: 2px solid tomato;
    animation: move 1500ms cubic-bezier(0, 0, 1, 1) infinite;
  }
  @keyframes move {
    0% {
      transform: translateX(0%);
    }

    50% {
      transform: translateX(500%);
    }
    100% {
      transform: translateX(0%);
    }
  }

  .play__width {
    display: grid;
    place-items: center;
  }

  .box__width {
    --size: 50px;
    width: var(--size);
    height: var(--size);
    border: 2px solid tomato;
    animation: move-width 1500ms cubic-bezier(0, 0, 1, 1) infinite;
  }
  @keyframes move-width {
    0% {
      transform: scaleX(1);
    }

    50% {
      transform: scaleX(7);
    }
    100% {
      transform: scaleX(1);
    }
  }
  .play__height {
    display: grid;
    place-items: center;
    width: 300px;
    height: 300px;
  }
  .box__height {
    --size: 50px;
    width: var(--size);
    height: var(--size);
    border: 2px solid tomato;
    animation: move-height 1500ms cubic-bezier(0, 0, 1, 1) infinite;
  }
  @keyframes move-height {
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
