<script context="module">
  export function preload({ params, query }) {
    return this.fetch(`blog.json`)
      .then(r => r.json())
      .then(posts => {
        return { posts };
      });
  }
</script>

<script>
  export let posts;
</script>

<style>

</style>

<svelte:head>
  <title>Blog</title>
</svelte:head>

<section class="cols">
  <article class="col">
    <h1>Blog</h1>
    {#each posts as post, index}
      {#if index}
        <hr />
      {/if}
      <div class="post-item">
        <h2>
          <a rel="prefetch" href="blog/{post.slug}">{post.title}</a>
        </h2>
        <p>{post.excerpt}</p>
        <div class="post-item-footer">
          <span class="post-item-date">— {post.printDate}</span>
        </div>
      </div>
    {/each}
  </article>
</section>
