<script>
  import { ajx } from "$frontier";
  import { onMount } from "svelte";

  let articles = [
    { mattter: { html: "", md: "" }, meta: { name: "loading..." } }
  ];

  $: currentArticle = {
    name: "Welcome!",
    contents: "Welcome! Select an article to read..."
  };

  $: showArticles = true;

  function setCurrentArticle(article) {
    currentArticle.name = article.meta.name;
    // currentArticle.contents = markdownit().render(article.meta.contents);
    currentArticle.contents = article.matter.html;
    showArticles = false;
  }

  onMount(() => {
    getFiles();
  });

  async function getFiles() {
    // let res = await ajx.get("/files");
    let res = await ajx.get(
      "https://notekar.knight.works/api/v1/files/published/knight.works"
    );
    articles = res.data;
  }
</script>

<style>

.v\.\.\. {
  width: 100%;
  text-overflow: ellipsis;
  overflow: hidden;
}
</style>

<section class="markdown row">
  <article class="ml" style="width: 320px;">
    <h2>Articles</h2>
    {#each articles as article}
      <button title={ article.meta.name } class="vl i link ..." on:click={() => setCurrentArticle(article)}>
        {article.meta.name}
      </button>
    {/each}
  </article>
  <div class="box _r">
    <div>
      {@html currentArticle.contents}
    </div>
  </div>
</section>
