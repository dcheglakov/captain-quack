<script>
  import Header from "./Header.svelte";
  import Footer from "./Footer.svelte";
</script>

<style>
  div {
    min-height: 100vh;
    display: grid;
    grid-template-rows: auto 1fr auto;
  }
</style>

<div>
  <Header />

  <main>
    <slot>
      <!-- optional fallback -->
    </slot>
  </main>

  <Footer />
</div>
