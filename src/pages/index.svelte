<script>
  import { url } from "$router";
</script>

<style>
  .title {
    font-family: Raleway, sans-serif;
    color: #fff;
    letter-spacing: 2px;
    font-size: 50px;
    font-weight: 300;
  }
  .subtitle {
    font-family: Montserrat, sans-serif;
    color: #fff;
    font-weight: 400;
    font-size: 24px;
    text-align: center;
  }
  .primary-color {
    color: #ffae32;
    font-style: italic;
  }
  .pad-title {
    padding-top: 160px;
  }
  .splash {
    background: url("https://res.cloudinary.com/knightworks/image/upload/q_35/v1584417552/knight-unsplash-medium-dark-reduced_srbz9a.jpg");
    height: 100vh;
    background-size: cover;
    display: flex;
    flex-flow: column;
    justify-content: space-between;
  }
  .photo-credit {
    display: none;
    position: fixed;
    bottom: 0;
    right: 0;
    font-size: 8px;
  }
  .contact {
    font-family: Montserrat, sans-serif;
    margin-left: 20px;
    letter-spacing: 3px;
    font-size: 24px;
    color: #f0f0f0;
    border-bottom: 2px solid transparent;
  }
  .contact:hover {
    border-bottom: 2px solid #f0f0f0;
  }
  @media only screen and (min-width: 768px) {
    .pad-title {
      padding-top: 210px;
    }
    .contact {
      font-size: 30px;
    }
    .photo-credit {
      display: inline-block;
    }
    .title {
      font-size: 115px;
      font-weight: 200;
      letter-spacing: 4px;
      line-height: 85px;
    }
    .subtitle {
      font-size: 34px;
      margin-left: 370px;
    }
  }
  @media only screen and (min-width: 1090px) {
    .title {
      font-size: 185px;
      font-weight: 100;
      letter-spacing: 7px;
      line-height: 150px;
      padding-top: 70px;
    }
    .subtitle {
      font-size: 42px;
      margin-left: 488px;
    }
  }
</style>

<svelte:head>
  <title>Knightworks</title>
</svelte:head>

<section class="flex splash">

  <div class="pad-title">
    <article class="block x i">
      <h1 class="title">Knightworks</h1>
      <h2 class="subtitle">
        code with
        <span class="primary-color" title="">honor</span>
      </h2>
    </article>
  </div>

  <!-- <article class="row stretch mt-auto" style="background-color:#000000b8"> -->
  <article class="row i" style="background-color:#000000b8">
    <a
      class="contact dn d@lm"
      style="margin-right:3.5rem;flex: 0 0 auto;"
      href="mailto:dev@knight.works">
      <div class="">
        <span style="">dev</span>
        <span style="font-size:26px; color:#ffae32e3;margin: 0 -10px;">@</span>
        <span>knight.works</span>
      </div>
    </a>
    <div class="">
      <a class="contact" href={$url('/articles')}>articles</a>
      <a class="contact" href={$url('/about')}>about</a>
    </div>
    <div class="spacer" />
    <a
      class="photo-credit"
      style="background-color:black;color:white;text-decoration:none;padding:4px
      6px;font-family:-apple-system, BlinkMacSystemFont, &quot;San
      Francisco&quot;, &quot;Helvetica Neue&quot;, Helvetica, Ubuntu, Roboto,
      Noto, &quot;Segoe UI&quot;, Arial,
      sans-serif;font-size:12px;font-weight:bold;line-height:1.2;border-radius:3px"
      href="https://unsplash.com/@tjump?utm_medium=referral&amp;utm_campaign=photographer-credit&amp;utm_content=creditBadge"
      target="_blank"
      rel="noopener noreferrer">
      <span style="display:inline-block;padding:2px 3px">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          style="height:8px;width:auto;position:relative;vertical-align:middle;top:-2px;fill:white"
          viewBox="0 0 32 32">
          <title>unsplash-logo</title>
          <path d="M10 9V0h12v9H10zm12 5h10v18H0V14h10v9h12v-9z" />
        </svg>
      </span>
      <span style="display:inline-block;padding:2px 3px; font-size:8px;">
        Photo by Nik Shuliahin
      </span>
    </a>
  </article>

</section>
