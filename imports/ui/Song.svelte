<script>
  const MarkdownIt = require('markdown-it')

  export let song

  const md = new MarkdownIt()
  $: mainContentHtml = md.render(song.mainContentMarkdown)
  // $: console.log(song)
</script>

<header class="mt-4 mb-4">
  <h1 class="display-4">{ song.title }</h1>
  {#if song.tune}
    <p class="text-muted">tune: {song.tune}</p>
  {/if}
</header>

<div style="font-size: 1.3rem;">{@html mainContentHtml}</div>

<div class="mt-4 mb-5">
  <p class="text-muted">
    source:
    <a href={song.url} target="_blank" class="text-decoration-none text-muted">
      {song.url.replace(/https?\:\/\//, '')}
    </a>
  </p>
</div>