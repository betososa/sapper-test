<script context="module">
  export function preload({ params, query }) {
    return this.fetch(`http://my-json-server.typicode.com/betososa/sapper-test/articles/1`).then(r => r.json()).then(article => {
      return { article };
    });
  }
</script>

<script>
  export let article;
</script>

<style>
  ul {
    margin: 0 0 1em 0;
    line-height: 1.5;
  }
</style>

<svelte:head>
  <title>{article.title}</title>
  <meta property="og:title" content={article.title} />
  <meta property="og:image" content={article.image} />
  <meta property="og:description" content={article.description} />
</svelte:head>

<h1>{article.title}</h1>

<img src={article.image}>
