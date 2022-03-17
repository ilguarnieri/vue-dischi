<template>

    <main>   
        <div class="container">

            <!-- text error -->
            <div class="api__error" v-if="error">
                <h2>CI DISPIACE MA NON E' STATO POSSIBILE COMPLETARE LA RICHIESTA</h2>
            </div>

            <!-- loader -->
            <div v-else-if="albums.length == 0" class="lds-ring"><div></div><div></div><div></div><div></div></div>

            <!-- wrapper music -->
            <div v-else>

                <!-- filters -->
                <SpSearch :genres="genres" :artists="artists"/>
                
                <!-- albums -->
                <div class="albums-wrapper">
                    <AlbumItems v-for="(album,i) in albums" :key="i" :album="album"/>
                </div>

            </div>
        </div>
    </main>
        
</template>

<script>
import axios from 'axios'
import AlbumItems from './AlbumItem.vue'
import SpSearch from './SpSearch.vue'

export default{
    name: 'SpMain',
    components:{
        AlbumItems,
        SpSearch
    },

    data(){
        return{
            albums: [],
            genres:[],
            artists:[],
            error: false
        }
    },

    methods: {
        fetchAlbums: function(){
            axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            .then( res => {
                this.albums = res.data.response;
                this.getGenre;
                this.error = false;
            })
            .catch(err => {
                console.error(err.response);
                this.albums = [];
                this.error = true;
            })
        },
    },

    computed:{

        getGenre: function(){

            return this.albums.forEach(el => {
                if(!this.genres.includes(el.genre)){
                    this.genres.push(el.genre);
                }

                if(!this.artists.includes(el.author)){
                    this.artists.push(el.author);
                }
            })
        }
    },

    created() {
        setTimeout(this.fetchAlbums, 1000)
    }
}

</script>

<style lang="scss" scoped>
@import '../assets/scss/common.scss';

main{
    min-height: 100vh;
    padding: 90px 10px;
    background-color: #1E2D3B;
    color: white;
    display: flex;
    justify-content: center;
    align-items: center;    

    .albums-wrapper{            
        display: flex;
        justify-content: space-evenly;
        flex-wrap: wrap;
        gap: 30px;

        & > *{
            width: 200px;
        }
    }    

    .api__error{
        text-align: center;
    }

    .lds-ring {
        display: inline-block;
        position: relative;
        width: 80px;
        height: 80px;
    }
    .lds-ring div {
        box-sizing: border-box;
        display: block;
        position: absolute;
        width: 64px;
        height: 64px;
        margin: 8px;
        border: 8px solid #fff;
        border-radius: 50%;
        animation: lds-ring 1.2s cubic-bezier(0.5, 0, 0.5, 1) infinite;
        border-color: #aaa transparent transparent transparent;
    }
    .lds-ring div:nth-child(1) {
        animation-delay: -0.45s;
    }
    .lds-ring div:nth-child(2) {
        animation-delay: -0.3s;
    }
    .lds-ring div:nth-child(3) {
        animation-delay: -0.15s;
    }
    @keyframes lds-ring {
        0% {
            transform: rotate(0deg);
        }
        100% {
            transform: rotate(360deg);
        }
    }
}

</style>