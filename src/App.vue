<template>
    <div id="header">
      <a href="http://localhost:8080/"><img src="./assets/building.png" style="width: 120px; margin-top: 20px;"/></a><br/>
      <a href="http://localhost:8080/"><img src="./assets/rijksmuseum-white.png" style="padding: 30px 0 0; "/></a>
      <p>The Rijksmuseum is the national museum of the Netherlands. We tell the story of 800 years of Dutch history, from 1200 to now. In addition, 
      we organize several exhibitions per year from our own collection and with (inter) national loans. Check out our current collection!</p>
      <inputPainting v-model:artworks="artworks"/>
  </div>
  <outputPainting :artworks="artworks"/>
</template>

<script>
import inputPainting from './components/inputPainting.vue'
import outputPainting from './components/outputPainting.vue'

export default {
  name: 'App',
  components: {
    inputPainting,
    outputPainting
  },
  data() {
    return {
      artworks: {
        loading: false
      }
    }
  }
}
</script>

<style lang="scss">
$background: #F9F3ED;

body {
  margin: 0;
  background-color: $background;
}

#header {
  background-color: #1e1e1e; 
  width: 100%; 
  margin-bottom: 30px;
  padding-bottom: 50px;
}

#app {
  font-family: Work Sans, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #000;
}

h1 {
  font-size: 1.7em;
  color: white;
  margin-bottom: 0;
}

h2 {
  font-size: 1.6em;
  font-family: Barlow, sans-serif;
  font-weight: 700;
  text-transform: uppercase;
}

h3 {
  font-family: Work Sans, sans-serif;
  font-size: 1.2em;
}

img {
  margin: auto;
  width: 400px;
}

p {
  color: white;
  font-family: Work Sans, sans-serif;
  width: 60%;
  margin: 40px auto 40px;
  text-align: left;
  line-height: 1.4em;
}

a {
  text-decoration: none;
  color: #000;
  transition: 0.3s;
}

a:hover {
  color: lighten(#000, 40%);
  transition: 0.3s;
}
</style>
