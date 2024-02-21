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
      margin-block-start: 20px;
      padding-block: 20px;
      border-top: 1px solid black;
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