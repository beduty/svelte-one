<script>
  import Header from "./header.svelte";
  import Content from "./content.svelte";
  import Footer from "./footer.svelte";
  let name = "ty";
</script>

<h1>Welcome to {name}</h1>
<p>
  Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation
</p>
<Header />
<Content />
<Footer />

<style>
  h1 {
    font-size: 20px;
    color: red;
  }
</style>
