<script>
  import Accordion from "./Accordion.svelte";
  import AccordionItem from "./AccordionItem.svelte";

  const items = [
    {
      title: "What are they?",
      content:
        "Parametric curves defined by four control points (hence 'cubic'`). Imagine points P0, P1, P2, and P3. The curve starts at P0, goes towards P1, and ends at P3, influenced by P2's direction. P1 and P2 are called 'handles' and don't necessarily lie on the curve itself, but they control its shape and direction",
    },
    {
      title: "Why are they useful?",
      content:
        "Flexibility: You can create a wide variety of shapes by adjusting the position of the control points. Scalability: Bézier curves can be resized infinitely without losing quality. Smoothness: The curves offer smooth transitions, making them ideal for animation and font design. Efficiency: They can be represented with just four numbers (coordinates of the points), making them efficient for storage and transmission.",
    },
    {
      title: "Where are they used?",
      content:
        "Graphics software: Creating smooth paths, shapes, and logos. Animation: Defining animation paths for objects and characters. Web design: Controlling shapes and transitions in user interfaces (e.g., CSS animations). Font design: Shaping and smoothing individual characters and font outlines.",
    },
  ];
</script>

<section class="content">
  <div class="container">
    <div class="content__box">
      <Accordion collapse --accordion-width="50ch">
        {#each items as item, i}
          <AccordionItem open={i === 0}>
            <svelte:fragment slot="title">{item.title}</svelte:fragment>
            <svelte:fragment slot="content">{item.content}</svelte:fragment>
          </AccordionItem>
        {/each}
      </Accordion>
    </div>
  </div>
</section>

<style>
  .content__box {
    margin-block: 50px;
    max-width: 500px;
    display: flex;
    justify-content: center;
    margin-inline: auto;
  }
</style>
