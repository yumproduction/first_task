
<template>
  <div class="wrapper">
      <div class="header">
          <div class="container">
              <div class="header__body">
                  <div class="header__logo">
                    <a href="#"><img :src='logo'/></a>
                  <h3 class="header__hi">FormsHI</h3>
                  </div>
                  <div class="header__ico">
                      <img :src='like'/>
                  </div>
              </div>
          </div>
      </div>
  </div>
</template>

<script>
import logo from './../../assets/logo.svg'
import like from './../../assets/like.svg'

export default {
  name: 'Header',
  data: function(){
      return{
          logo: logo,
          like: like
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang = 'scss'>

@import './Header.scss';
</style>