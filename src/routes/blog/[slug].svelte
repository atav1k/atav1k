<script context="module">
  export async function preload({ params, query }) {
    // the `slug` parameter is available because
    // this file is called [slug].html
    const res = await this.fetch(`blog/${params.slug}.json`);
    const data = await res.json();

    if (res.status === 200) {
      return { post: data };
    } else {
      this.error(res.status, data.message);
    }
  }
</script>

<script>
  export let post;
</script>

<style>

</style>

<svelte:head>
  <title>{post.title}</title>
</svelte:head>
<section class="cols">
  <article class="col">
    <header>
      <p>{post.printDate} ~ {post.printReadingTime}</p>
      <h1>{post.title}</h1>
      <hr />
    </header>
    <div class="container">
      <article class="content">
        {@html post.html}
      </article>
      <hr />
    </div>
  </article>
</section>
