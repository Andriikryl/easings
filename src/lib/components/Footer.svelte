<script>
  import Container from "./Container.svelte";
</script>

<footer class="footer">
  <Container>
    <div class="header__box">
      <p class="name">footer</p>
    </div>
  </Container>
</footer>

<style>
  .footer {
    padding-block: 20px;
    border-bottom: 1px solid black;
    background-color: #f1faee;
    margin-block-end: 20px;
    z-index: 100;
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
