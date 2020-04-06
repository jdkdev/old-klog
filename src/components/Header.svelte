<script>
  import { auth, currentUser } from "@frontierjs/frontend";
  import Brand from "$c/Brand.svelte";
  import Nav from "$c/Nav.svelte";
  import { isActive, url, goto } from "$router";
</script>

<style>
  .title {
    font-family: Raleway, sans-serif;
    color: #fff;
    letter-spacing: 2px;
    font-size: 50px;
    font-weight: 300;
  }
  .contact {
    font-family: Montserrat, sans-serif;
    letter-spacing: 3px;
    font-size: 24px;
    color: #f0f0f0;
    border-bottom: 5px solid transparent;
  }
  .contact:hover {
    border-bottom: 5px solid #f0f0f0;
  }
</style>

{#if $currentUser}
  <header class="">
    <article class="m">
      <span class="stretch">
        <span class="show-md">Logged in:</span>
        {$currentUser.email}
      </span>
    </article>
    <article class="row space-around">
      <a class="lm" href={$url('/')}>Home</a>
      <a class="lm" href={$url('/examples')}>Examples</a>
    </article>
  </header>
{:else if !$isActive('/index')}
  <header class="bg flex" style="opacity: .92;">
    <article class="stretch">
      <a href={$url('/index')}>
        <h1 class="title">Knightworks</h1>
      </a>
    </article>
    <article class="row">
      <a class="contact" href={$url('/articles')}>articles</a>
      <a class="contact" href={$url('/about')}>about</a>
    </article>
  </header>
{/if}
