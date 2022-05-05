<template>
  <footer>
      <div>
          <h4>Created with love by <span> ROMA &copy;</span></h4>
      </div>
  </footer>
</template>

<script>
export default {
name: 'SiteFooter'
}
</script>

<style lang="scss" scoped>
@import '@/assets/scss/style.scss';

div{
    width: 100%;
    height: 70px;
    background-color: $bg-nav;
    color: $text-white;
    text-align: center;
    h4{
        padding: 1.65rem 0 ;
        
        span{
            &:hover{
            color: #adff2f;
            cursor: pointer;
        }
        }
    }

}

</style>