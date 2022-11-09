<template>
    <h2>Currently in our collection:</h2>
    <div style="margin-left: 150px; margin-right: 150px;">
        <ul>
            <li v-for="(artwork, index) in artworks" v-bind:key="index">
                <a v-bind:href="artwork.links.web" target="_blank"><h3>{{ artwork.longTitle }}</h3></a>         
                <img v-bind:src="artwork.webImage.url"/>
            </li>    
        </ul>
    </div>
</template>

<script>
export default {
    name: 'outputPainting',
    props: ['artworks']
}
</script>

<style lang="scss" scoped>
img {
    width: 80%;
    height: auto;
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