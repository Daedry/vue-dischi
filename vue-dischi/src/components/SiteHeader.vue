<template>
  <header>
    <nav>
      <Logo />
    </nav>
  </header>
</template>

<script>
import Logo from "@/components/LogoComponent";

export default {
  name: "SiteHeader",
  components: {
    Logo,
  },
};
</script>

<style lang="scss" scoped>
@import "@/assets/scss/style.scss";

header {
  nav {
    width: 100%;
    height: 50px;
    background-color: $bg-nav;
    border-top: 1px solid $bg-main;
  }
}
</style>