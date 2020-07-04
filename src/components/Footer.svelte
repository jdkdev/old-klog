<script>
  export const user = false;
  import { isActive, url, goto } from "$router";
</script>

{#if user}
  <footer>Footer</footer>
{:else if !$isActive('/index')}
  <footer class="mt" style="background-color:#000;" />
{/if}
