<script lang="ts">
  import { slide } from "svelte/transition";
  import { getAccordionOptions } from "../../store/context";

  export let open = false;
  const componentId = crypto.randomUUID();
  const { collapse, activeComponentId } = getAccordionOptions();

  function setActive() {
    $activeComponentId = componentId;
  }

  function toggleOpen() {
    open = !open;
  }

  function handleClick() {
    collapse ? setActive() : toggleOpen();
  }

  $: open && collapse && setActive();
  $: isActive = $activeComponentId === componentId;
  $: isOpen = collapse ? isActive : open;
</script>

<div class="accordion-item">
  <button
    on:click={handleClick}
    class="accordion-toggle"
    aria-expanded={isOpen}
    aria-controls="accordion-{componentId}"
  >
    <div class="accordion-title">
      <slot name="title" />
    </div>

    <div class="accordion-caret" class:open={isOpen}></div>
  </button>

  {#if isOpen}
    <div
      transition:slide|local
      class="accordion-content"
      role="region"
      aria-hidden={!isOpen}
      aria-labelledby="accordion-{componentId}"
    >
      <slot name="content" />
    </div>
  {/if}
</div>

<style>
  .accordion-item {
    background-color: #ffffff;
    border: 1px solid #000000;
    border-radius: var(--accordion-radius, 4px);
  }
  .accordion-toggle {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: var(--accordion-padding, 1rem);
    border: none;
    background: none;
    cursor: pointer;
    border-radius: var(--accordion-radius, 4px);
    transition: background-color 0.1s ease;
    color: var(--black, #1b1b1b);
    font-family: Patrick Hand;
    font-size: 20px;
    font-style: normal;
    font-weight: 400;
    line-height: 22px; /* 137.5% */
    letter-spacing: 0.16px;
  }

  .accordion-caret {
    width: 20px;
    height: 2px;
    background-color: #000000;
    transition: rotate 0.3s ease;
    position: relative;
  }
  .accordion-caret::after {
    content: "";
    display: block;
    background-color: #000000;
    width: 10px;
    height: 2px;
    position: absolute;
    right: 2px;
    top: -3px;
    transform: rotate(20deg);
  }
  .accordion-caret::before {
    content: "";
    display: block;
    background-color: #000000;
    width: 10px;
    height: 2px;
    position: absolute;
    right: 2px;
    top: 3px;
    transform: rotate(-20deg);
  }
  .accordion-content {
    color: #14213d;
    padding: var(--accordion-content-padding, 1rem);
  }

  .open {
    rotate: 90deg;
  }
</style>
