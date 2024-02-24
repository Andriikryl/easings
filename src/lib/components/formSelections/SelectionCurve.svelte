<script lang="ts">
  export let title: string;
  export let group: string;
  export let curve: number[];
  export let currentEasingType: any;
</script>

<div class="curve-selection__option-group">
  <input
    bind:group={currentEasingType}
    id={title}
    class="sr"
    value={{ group, title }}
    type="radio"
    name="currentEasingType"
  />
  <label for={title} class={title.slice(0, 4)}>
    <svg
      class="curve-selection__illustration"
      width="100%"
      viewBox="0 0 1.4 1.4"
      version="1.1"
    >
      <path
        class="curve-selection__curve"
        d="M0.2,1.2 C{curve[0] + 0.2},{1.4 - (curve[1] + 0.2)} {curve[2] +
          0.2},{1.4 - (curve[3] + 0.2)} 1.2,0.2"
      />
    </svg>
    <code class="curve-selection__title">{title}</code>
  </label>
</div>

<style lang="scss">
  input:checked + label,
  input:focus + label {
    box-shadow: 0 0 0 3px #ffc300;
  }
  label {
    display: flex;
    .curve-selection__title {
      flex-grow: 1;
      flex-shrink: 1;
      width: 100%;
      text-align: center;
      line-height: 1;
      margin-top: 0;
      font-size: 0.615rem;
      border-top-right-radius: 0;
      border-top-left-radius: 0;
      display: block;
      padding-block: 10px;
    }
  }
  .circ code {
    background: var(--lighterBlue);
    border-color: var(--lighterBlue);
    color: var(--black);
  }
  .sine code {
    background: var(--yellow);
    border-color: var(--yellow);
    color: var(--black);
  }
  .quad code {
    background: var(--darkBlue);
    border-color: var(--darkBlue);
    color: var(--white);
  }
  .cubi code {
    background: var(--lightBlue);
    border-color: var(--lightBlue);
    color: var(--black);
  }
  .quin code {
    background: var(--orange);
    border-color: var(--orange);
    color: var(--white);
  }
  .back code {
    background: var(--red);
    border-color: var(--red);
    color: var(--white);
  }
  .expo code {
    background: var(--darkGray);
    border-color: var(--darkGray);
    color: var(--white);
  }
  .curve-selection__option-group {
    max-width: 300px;
  }
  .curve-selection__illustration {
    width: 100px;
    height: 50px;
    border: 1px solid var(--lighterGray);
    background: repeating-linear-gradient(
        to bottom,
        hsl(182, 43%, 76%, 0.4),
        hsl(182, 43%, 76%, 0.4) 1px,
        transparent 1px,
        transparent 20.14%
      ),
      repeating-linear-gradient(
        to right,
        hsl(182, 43%, 76%, 0.4),
        hsl(182, 43%, 76%, 0.4) 1px,
        transparent 1px,
        transparent 20.14%
      );
    background-position: -1px -1px;
  }

  .curve-selection__curve {
    fill: none;
    stroke: #e63946;
    stroke-width: 0.05px;
    pointer-events: none;
  }
</style>
