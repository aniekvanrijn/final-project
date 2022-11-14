<template>
    <div v-if="artworks.count > 0" class="artworks">
        <h2>Currently in our collection:</h2>
        <ul>
            <li v-for="(artwork, index) in artworks.artObjects" v-bind:key="index">
                <a v-bind:href="artwork.links.web" target="_blank"><h3>{{ artwork.longTitle }}</h3></a>         
                <a v-bind:href="artwork.links.web" target="_blank">
                    <img v-if="artwork.hasImage" v-bind:src="artwork.webImage.url"/>
                    <img v-else src="../assets/building.png" alt="Image not available"/>
                </a>
            </li>    
        </ul>
    </div>
    <div v-else-if="artworks.count == 0">
        <p>No results found.</p>
        <p>Try typing the artist's full name.</p>
    </div>
    <div v-else-if="artworks.loading === true">
        <div class="loader"></div>
    </div>

</template>

<script>
export default {
    name: 'outputPainting',
    props: ['artworks']
}
</script>

<style lang="scss" scoped>
p {
    color: black;
    text-align: center;
}

img {
    width: 80%;
    height: auto;
}

div.artworks {
    margin: 0 150px;
}

ul {
    list-style-type: none;
    padding: 0;
    width: 100%;
    margin: auto;
}

ul li {
    width: 50%;
    float: left;
    margin-bottom: 40px;      
}
.loader {
  border: 12px solid #c1c1c1;
  border-top: 12px solid #d55140;
  border-radius: 50%;
  width: 50px;
  height: 50px;
  animation: spin 1.5s linear infinite;
  margin: 35px auto;
}

@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}
</style>