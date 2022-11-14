<template>
    <input type="text" placeholder="Artist Full Name" v-model="artist"/>
    <button @click="getPainting">Search Collection</button> 
</template>

<script>
const baseUrl = "https://www.rijksmuseum.nl/api/";
const apiKey = 'OVnGDx3G';
const lang = 'en';

export default {
  name: 'inputPainting',
  props: ['artworks'],
  data() {
    return {
      artist: ''
    }
  },
  methods: {
    getPainting() {
      let reqUrl = baseUrl + lang + '/collection?key=' + apiKey + '&involvedMaker=' + this.artist.replaceAll(' ', '+'); 
      // console.log(reqUrl);

      this.$emit('update:artworks', { loading: true });
      fetch(reqUrl)
        .then((response) => response.json())
        .then((data) => {
          console.log(data);
          this.$emit('update:artworks', data);
        });
          
      }
      //Also handle when there is no succes 
    }
  }

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
$button: #d55140;

div {
  width: 100%;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

input, button, select {
  display: block;
  margin: 0.80em auto;
  font-family: Work Sans, sans-serif;
  font-size: 16px;
}

input, select {
  background-color: #1e1e1e;
  color: #fff;
  border: 1px solid #fff;
  padding: 10px;
  width: 240px;
}

button {
  background: $button;
  color: #fff;
  padding: 10px;
  border: 0;
  transition: 0.3s;
  cursor: pointer; 
  margin-bottom: 0;
  font-weight: 600;
  width: 261px;
}

button:hover {
  // background-color: lighten($button, 10%);
  color: #000;
  background-color: #fff;
  transition: 0.3s;
}
</style>
