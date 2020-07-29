<template>
  <div id="app">
    <Header />
    <Forms msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import Forms from './components/Forms/Forms'
import Header from './components/Header/Header'
export default {
  name: 'App',
  components: {
    Forms,
    Header
  }
}
</script>

<style lang = 'scss'>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;500;600;700;800&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,300;0,400;0,500;0,600;0,700;1,800&display=swap');
  *{
    margin: 0;
    padding: 0;
  }
  body{
  color: #2c3e50;
  font-family: 'Montserrat', sans-serif;
}

$maxWidth: 1280;

@mixin fontSize($pcSize, $mobSize) {
 $addSize: $pcSize - $mobSize;
 $maxWidth: $maxWidth - 320;
 font-size: calc(#{$mobSize + px} + #{$addSize} * ((100vw - 320px) / #{$maxWidth}));
}

body{
    font-family: 'Montserrat', sans-serif;
    @include fontSize(16, 14);
    -webkit-font-smoothing: antialaised;
    -webkit-overflow-scrolling: touch;
}

h1{
    @include fontSize(50, 34);
}

h3{
    @include fontSize(34, 22);
    font-weight: 500;
    color: #555555;
}
h4{
    @include fontSize(29.219239, 14.60962);
    font-weight: 600;
    color: #555555;
  }
  h5{
    @include fontSize(20, 18.60962);
    font-weight: 400;
    color: #555555;
  }

a{
    @include fontSize(18, 16);
    text-decoration: none;
    color: #fff;
}

p{
    @include fontSize(18, 16);
    color: #8c8c8c;
}

/**
 * Сброс стилей у кнопки.
 * Придётся немного поработать, чтобы получить нейтральный вид.
*/
button {
  padding: 0;
  border: none;
  font: inherit;
  color: inherit;
  background-color: transparent;
  /* отображаем курсор в виде руки при наведении; некоторые
  считают, что необходимо оставлять стрелочный вид для кнопок */
  cursor: pointer;
}
button:focus{
  outline: 0;
}


/* Remove the stupid outer glow in Webkit */
select:focus,input:focus
{
  outline:0;
  border: 2px solid #42b983;

}

</style>
