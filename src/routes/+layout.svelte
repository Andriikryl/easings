<script lang="ts">
  import Footer from "$lib/components/Footer.svelte";
  import Header from "$lib/components/Header.svelte";
  import "../styles/global.scss";
</script>

<svelte:head>
  <title>Cubic Bezier Curves</title>
</svelte:head>

<Header />
<main>
  <slot />
</main>
<Footer />
