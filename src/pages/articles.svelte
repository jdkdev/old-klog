<script>
  import { ajx } from "$frontier";
  import { onMount } from "svelte";

  let articles = [{ name: "third one", contents: "" }];

  $: currentArticle = { name: "", contents: "" };
  $: showArticles = true;

  function setCurrentArticle(article) {
    currentArticle.name = article.name;
    currentArticle.contents = markdownit().render(article.contents);
    showArticles = false;
  }

  onMount(() => {
    getFiles();
  });

  async function getFiles() {
    let res = await ajx.get("https://notekar.knight.works/api/v1/files");
    articles = res.data;
  }
</script>

<section class=" mt markdown">
  {#if showArticles}
    <article class="pl w-max-xxs stretch-all float-left" style="width: 300px;">
      <h2>Articles</h2>
      {#each articles as article}
        <span class="p" on:click={() => setCurrentArticle(article)}>
          {article.name}
        </span>
      {/each}
    </article>
  {:else}
    <div class="w-max-xxs">
      <button class="link" on:click={() => (showArticles = true)}>
        &lt;&lt; back to articles
      </button>
    </div>
  {/if}
  <div class="m-auto p w-max-lg">
    <h3>{currentArticle.name}</h3>
    <div>
      {@html currentArticle.contents}
    </div>
  </div>
</section>
