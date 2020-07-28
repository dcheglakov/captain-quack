<script>
  import Table from "./components/Table.svelte";
  import Title from "./components/Title.svelte";
  import Headline from "./components/Headline.svelte";
  import Layout from "./components/Layout.svelte";
  import Container from "./components/Container.svelte";
  import "normalize.css";
</script>

<style>
  :global(body) {
    font-size: 0.875rem;
    font-family: "Roboto", sans-serif;
  }
</style>

<Layout>
  <Title>¡Ay caramba!</Title>
  <Container>
    <Headline>Автомобили в наличии</Headline>
    <Table />
  </Container>

</Layout>
