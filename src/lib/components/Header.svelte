<script>
  import Container from "./Container.svelte";
</script>

<header class="header">
  <Container>
    <div>
      <p class="name">header</p>
    </div>
  </Container>
</header>

<style>
  .header {
    padding-block: 20px;
    border-bottom: 1px solid black;
    margin-block-end: 20px;
  }
  .name {
    text-transform: uppercase;
    color: var(--black, #1b1b1b);
    font-family: "Patrick Hand";
    font-size: 22px;
    font-style: normal;
    font-weight: 400;
    line-height: 28px; /* 127.273% */
  }
</style>
