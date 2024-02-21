<script lang="ts">
  export let copyToClipboard: () => void;
  export let copyButtonIcon: string;
</script>

<button
  class="current-curve__copy-btn"
  on:click={copyToClipboard}
  type="button"
>
  <span aria-hidden="true">{copyButtonIcon}</span>
</button>

<style>
  .current-curve__copy-btn {
    min-width: 210px;
    margin-inline: auto;
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
  }
</style>
