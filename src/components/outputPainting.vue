<template>
    <div v-if="artworks.count > 0" class="artworks">
        <h2>Currently in our collection:</h2>

        <ul>
            <li v-for="(artwork, index) in artworks.artObjects" v-bind:key="index">
                <a v-bind:href="artwork.links.web" target="_blank"><h3>{{ artwork.longTitle }}</h3></a>         
                <img v-bind:src="artwork.webImage.url"/>
            </li>    
        </ul>
    </div>
    <div v-else-if="artworks.count == 0">
        <p>No results found.</p>
        <p>Try typing the artist's full name.</p>
    </div>
    <div v-else-if="artworks.loading === true">
        <p>Loading...</p>
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
</style>