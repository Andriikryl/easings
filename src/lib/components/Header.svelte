<script>
  import Container from "./Container.svelte";
</script>

<header class="header">
  <Container>
    <div class="flex__group">
      <div class="side__one"></div>
      <div class="side__one"></div>
    </div>
  </Container>
</header>

<style>
  .flex__group {
    display: flex;
  }
  .side__one {
    width: 50px;
    height: 50px;
    border: 1px solid tomato;
  }
  .side__one:nth-child(2) {
    transform: translateX(-20px) translateY(10px);
  }
  .header {
    position: sticky;
    top: 0;
    padding-block: 20px;
    border-bottom: 1px solid black;
    background-color: #f1faee;
    margin-block-end: 20px;
    z-index: 100;
  }
</style>
