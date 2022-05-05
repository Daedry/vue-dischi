<template>
  <header>
      <nav>
        <div class="logo">
          <img src="https://upload.wikimedia.org/wikipedia/commons/1/19/Spotify_logo_without_text.svg" alt="">
        </div>
      </nav>
    </header>
</template>

<script>
export default {
name:'SiteHeader'
}
</script>

<style lang="scss" scoped>
@import '@/assets/scss/style.scss';

header{
  nav{
    width: 100%;
    height: 50px;
    background-color: $bg-nav;

    .logo{
      width: 40px;
      padding: 0.2rem 0 ;
      margin-left: 4rem;
    }
  }
}

</style>