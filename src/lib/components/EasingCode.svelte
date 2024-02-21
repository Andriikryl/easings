<script lang="ts">
  export let curveCSS: string;
</script>

<code class="current-curve__coordinates">
  {curveCSS};
</code>

<style>
  .current-curve__coordinates {
    white-space: normal;
    font-size: 0.5rem;
    display: inline-block;
    margin: 0 auto;

    @media (min-width: 34rem) {
      font-size: 0.7rem;
    }

    @media (min-width: 66rem) {
      font-size: 0.8rem;
    }
  }
</style>
