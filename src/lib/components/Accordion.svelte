<script lang="ts">
  import { setAccordionOptions } from "../../store/context";
  export let collapse = false;
  setAccordionOptions({ collapse });
</script>

<div class="accordion">
  <slot />
</div>

<style>
  .accordion {
    display: flex;
    flex-direction: column;
    gap: 20px;
    width: var(--accordion-width, 100%);
    padding: var(--accordion-padding, 1rem);
    color: var(--accordion-color, hsl(220 10% 98%));
    background-color: transparent;
    border: 3px solid #a8dadc;
    border-radius: var(--accordion-radius, 4px);
    box-shadow: var(--accordion-shadow, 0px 1px 20px hsl(220 10% 8%));
  }
</style>
