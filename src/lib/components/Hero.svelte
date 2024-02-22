<script>
  import Container from "./Container.svelte";
</script>

<section class="hero">
  <Container>
    <div>
      <div class="title__box">
        <h1 class="hero__title">How Cubic Bezier Curves works?</h1>
      </div>
      <div class="qa__box">
        <div class="flex__group">
          <img src="/men.svg" width="54" height="54" alt="men" />
          <div class="info__bloc">
            <p>Do you know Cubic Bezier?</p>
          </div>
        </div>
        <div class="flex__group">
          <div class="info__bloc">
            <p>Cubic?</p>
          </div>
          <div class="image__boxWem">
            <img src="/women.svg" width="54" height="54" alt="women" />
          </div>
        </div>
      </div>
      <div class="arrow__dowBox">
        <img src="/Arrow left.svg" width="251" height="14" alt="" />
      </div>
    </div>
  </Container>
</section>

<style>
  .hero {
    margin-block-end: 150px;
  }
  .title__box {
    margin-block: 20px;
    padding: 12px;
    border-radius: 8px;
    background: var(--gray-1, #eee);
  }

  .qa__box {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
    gap: 30px;
  }

  .arrow__dowBox {
    margin-block: 100px;
    display: grid;
    place-items: center;
    transform: rotate(-90deg);
  }

  .hero__title {
    padding: 32px;
    text-align: center;
    color: var(--black, #1b1b1b);
    font-family: Patrick Hand;
    font-size: 30px;
    font-style: normal;
    font-weight: 400;
    line-height: normal;
    letter-spacing: -0.3px;
  }

  .flex__group {
    display: flex;
    gap: 10px;
    align-items: center;
  }

  .info__bloc {
    max-width: 233px;
    border-radius: 12px;
    border: 3px solid var(--black, #1b1b1b);
    background: var(--white, #fff);
    padding: 12px 16px 18px 16px;
    box-shadow: 0px 4px 4px 0px rgba(0, 0, 0, 0.16);
  }

  .info__bloc p {
    color: var(--black, #1b1b1b);
    font-family: Patrick Hand;
    font-size: 16px;
    font-style: normal;
    font-weight: 400;
    line-height: 22px; /* 137.5% */
    letter-spacing: 0.16px;
  }

  .image__boxWem {
    transform: matrix(-1, 0, 0, 1, 0, 0);
  }
</style>
