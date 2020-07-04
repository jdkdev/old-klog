<script>
  import { ajx } from "$frontier";
  import { onMount } from "svelte";

  let articles = [{ attributes: { filename: "loading...", contents: "" } }];

  $: currentArticle = { name: "", contents: "" };
  $: showArticles = true;

  function setCurrentArticle(article) {
    currentArticle.name = article.attributes.name;
    // currentArticle.contents = markdownit().render(article.attributes.contents);
    currentArticle.contents = article.attributes.html;
    showArticles = false;
  }

  onMount(() => {
    getFiles();
  });

  async function getFiles() {
    // let res = await ajx.get("/files");
    let res = await ajx.get(
      "https://notekar.knight.works/api/v1/published/knight.works"
    );
    articles = res.data;
  }
</script>

<style>

</style>

<section class=" mt markdown">
  {#if showArticles}
    <article class="pl w-max-xxs stretch-all float-left" style="width: 300px;">
      <h2>Articles</h2>
      {#each articles as article}
        <button
          class="link flex-start text-align-left"
          on:click={() => setCurrentArticle(article)}>
          {article.attributes.filename}
        </button>
      {/each}
    </article>
  {:else}
    <div class="w-max-xxs" style="width:306px;float:left;">
      <button class="link" on:click={() => (showArticles = true)}>
        &lt;&lt; back to articles
      </button>
    </div>
  {/if}
  <div class="m-auto p w-max-lg">
    <div>
      {@html currentArticle.contents}
    </div>
  </div>
</section>
