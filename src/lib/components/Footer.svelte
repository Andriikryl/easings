<script>
  import Container from "./Container.svelte";
  import Flag from "./Flag.svelte";
</script>

<footer class="footer">
  <Container>
    <div class="header__box">
      <Flag />
    </div>
  </Container>
</footer>

<style>
  .footer {
    padding-block: 20px;
    border-bottom: 1px solid black;
    background-color: #f1faee;
    margin-block-end: 20px;
  }
</style>
