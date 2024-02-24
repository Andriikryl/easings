<script lang="ts">
  import throttle from "just-throttle";
  import { clamp } from "../../utils/clamp";
  import formatDecimal from "../../utils/formatDecimal";
  import { onMount } from "svelte";
  import Container from "./Container.svelte";
  import { premadeEasings } from "../../utils/easingPar";
  import CurentRectBeg from "./svg/CurentRectBeg.svelte";
  import CurentCircleMove from "./svg/CurentCircleMove.svelte";
  import EasingCode from "./svg/EasingCode.svelte";
  import CurentButton from "./svg/CurentButton.svelte";
  import CurentEasingPath from "./svg/CurentEasingPath.svelte";
  import CurentDragLins from "./svg/CurentDragLins.svelte";
  import CircleControls from "./svg/CircleControls.svelte";
  import SelectionCurve from "./formSelections/SelectionCurve.svelte";
  import AnimationBlock from "./animations/AnimationBlock.svelte";
  import ArrowDown from "./icons/ArrowDown.svelte";

  let startHandleX: number = 30;
  let startHandleY: number = 140;
  let endHandleX: number = 90;
  let endHandleY: number = 100;
  let dragging: string | null = null;
  let currentEasingType: { group: string; title: string } | null = null;
  let copyButtonIcon: string = `copy`;
  let startHandle: SVGElement | null = null;
  let endHandle: SVGElement | null = null;
  let outerFrame: SVGElement | null = null;
  let itemsToDisplay = 6;

  $: startHandleXToBinary = formatDecimal((startHandleX - 20) / 100);
  $: startHandleYToBinary = formatDecimal((300 - startHandleY) / 100 - 1);
  $: endHandleXToBinary = formatDecimal((endHandleX - 20) / 100);
  $: endHandleYToBinary = formatDecimal((300 - endHandleY) / 100 - 1);
  $: bezierCoordinates = `${startHandleXToBinary}, ${startHandleYToBinary}, ${endHandleXToBinary}, ${endHandleYToBinary}`;
  $: curveCSS = `cubic-bezier(${bezierCoordinates})`;

  const trackMovement = (e: any) => {
    if (!dragging || !outerFrame) return;

    const rect = outerFrame.getBoundingClientRect();
    const left = e.clientX || e.changedTouches[0].clientX;
    const top = e.clientY || e.changedTouches[0].clientY;

    let xPosition = Math.round((140 / rect.width) * (left - rect.left));
    let yPosition = Math.round((300 / rect.height) * (top - rect.top));

    xPosition = clamp(20, xPosition, 120);
    yPosition = clamp(0, yPosition, 300);

    if (dragging === "start") {
      startHandleX = xPosition;
      startHandleY = yPosition;
    } else if (dragging === "end") {
      endHandleX = xPosition;
      endHandleY = yPosition;
    }
    currentEasingType = null;
  };

  const handleDragStart = (e: any) => {
    if (startHandle === e.target) {
      dragging = "start";
    } else if (endHandle === e.target) {
      dragging = "end";
    }
    trackMovement(e);
  };

  const handleDragEnd = () => (dragging = null);

  const copyToClipboard = () => {
    navigator.clipboard.writeText(curveCSS);
    copyButtonIcon = "Copyed";
    setTimeout(() => {
      copyButtonIcon = "Copy";
    }, 1200);
  };

  $: if (currentEasingType) {
    const thisEasing =
      premadeEasings[currentEasingType.group][currentEasingType.title];
    startHandleX = thisEasing[0] * 100 + 20;
    startHandleY = 300 - (thisEasing[1] * 100 + 100);
    endHandleX = thisEasing[2] * 100 + 20;
    endHandleY = 300 - (thisEasing[3] * 100 + 100);
  }

  let isFrame = false;

  onMount(() => {
    if (window.self !== window.top) isFrame = true;
  });
</script>

<section class="easing__section">
  <Container>
    <form
      class="easing__wrapper"
      class:is-frame={isFrame}
      on:submit|preventDefault
    >
      <!-- svelte-ignore a11y-no-static-element-interactions -->
      <div
        class="current-curve"
        id="demo-curve"
        on:mousemove={throttle((e) => trackMovement(e), 10, { leading: true })}
        on:mousedown={handleDragStart}
        on:mouseup={handleDragEnd}
        on:mouseleave={handleDragEnd}
        on:touchstart={handleDragStart}
        on:touchend={handleDragEnd}
        on:touchmove={throttle((e) => trackMovement(e), 10, { leading: true })}
        on:touchcancel={handleDragEnd}
      >
        <h1 class="curent__title">{currentEasingType?.title || "custom"}</h1>
        <svg
          bind:this={outerFrame}
          class="current-curve__svg"
          width="100%"
          height="500"
          viewBox="0 0 140 300"
          version="1.1"
        >
          <CurentRectBeg />
          <CurentEasingPath
            {startHandleX}
            {startHandleY}
            {endHandleX}
            {endHandleY}
          />
          <g class:transparent={dragging}>
            <CurentDragLins
              {startHandleX}
              {startHandleY}
              {endHandleX}
              {endHandleY}
            />
            <CurentCircleMove {bezierCoordinates} />
            <CircleControls
              bind:endHandle
              bind:startHandle
              {startHandleX}
              {startHandleY}
              {endHandleX}
              {endHandleY}
            />
          </g>
        </svg>
        <EasingCode {curveCSS} />
        <CurentButton {copyToClipboard} {copyButtonIcon} />
      </div>

      <div class="inner__wrapper">
        <div class="curve-selection">
          {#each Object.entries(premadeEasings).slice(0, itemsToDisplay) as [group, _]}
            <h3 class="selection__title">
              {group === "browser" ? "Popular easing" : "Extra easing"}
            </h3>
            {#each Object.entries(premadeEasings[group]).slice(0, itemsToDisplay) as [title, curve]}
              <SelectionCurve {title} {curve} {group} bind:currentEasingType />
            {/each}
          {/each}
        </div>
        {#if itemsToDisplay < 55}
          <div class="box">
            <button class="select__more" on:click={() => (itemsToDisplay += 5)}
              >Show More</button
            >
          </div>
        {/if}
      </div>
    </form>

    <ArrowDown />
    <div>
      <AnimationBlock {currentEasingType} {curveCSS} />
    </div>
  </Container>
</section>

<style lang="scss">
  .box {
    display: grid;
    place-items: center;
  }
  .select__more {
    width: max-content;
    padding: 12px 16px;
    border-radius: 8px;
    border: 2px solid var(--black, #1b1b1b);
    background: var(--white, #fff);
    color: var(--black, #1b1b1b);
    text-align: center;
    font-family: Patrick Hand;
    font-size: 22px;
    font-style: normal;
    font-weight: 400;
    line-height: 28px;
    cursor: pointer;
    margin-inline: auto;
  }
  .easing__wrapper {
    display: flex;
    flex-wrap: wrap;
    padding: 20px;
    gap: 20px;
    border-radius: 10px;
  }
  .curent__title {
    text-transform: uppercase;
    text-align: center;
    color: #f8f9fa;
    font-family: Patrick Hand;
    font-size: 30px;
    font-style: normal;
    font-weight: 400;
    line-height: normal;
    letter-spacing: -0.3px;
    padding-block-end: 10px;
  }
  .current-curve {
    width: 300px;
    display: flex;
    flex-direction: column;
    gap: 10px;
    margin-inline: auto;
    z-index: 3;

    .current-curve__svg {
      border: 2px solid #a8dadc;
      margin: 0 auto;
      display: block;
      background: repeating-linear-gradient(
          to bottom,
          #a8dadc,
          #a8dadc 1px,
          transparent 1px,
          transparent 20.14%
        ),
        repeating-linear-gradient(
          to right,
          #a8dadc,
          #a8dadc 1px,
          transparent 1px,
          transparent 20.14%
        );
      border-radius: 10px;

      @media (min-width: 56rem) {
        max-width: 18rem;
      }
    }
  }

  svg {
    fill-rule: evenodd;
    clip-rule: evenodd;
    stroke-linecap: round;
    stroke-miterlimit: 1.5;
  }

  .inner__wrapper {
    width: 70%;
    margin-inline: auto;
  }

  .curve-selection {
    margin-block-end: 20px;
    width: 100%;
    --layout-grid-min: 20ch;
    --layout-grid-gap: 1vw;
    display: grid;
    grid-template-columns: repeat(
      auto-fit,
      minmax(min(100%, var(--layout-grid-min)), 1fr)
    );
    gap: var(--layout-grid-gap);
    grid-auto-rows: min-content;
    .selection__title {
      padding: 12px;
      background: var(--gray-1, #eee);
      grid-column: 1 / -1;
      text-align: left;
      color: var(--black, #1b1b1b);
      font-family: Patrick Hand;
      font-size: 30px;
      font-style: normal;
      font-weight: 400;
      line-height: normal;
      letter-spacing: -0.3px;
      height: max-content;
    }
  }
  .transparent {
    opacity: 0.4;
  }
</style>
