<template>

    <main>   
        <div class="container">

            <div v-if="albums.length == 0" class="lds-ring"><div></div><div></div><div></div><div></div></div>

            <div v-else class="albums-wrapper">

            <AlbumItems v-for="(el,i) in albums" :key="i" :album="el"/>

            <!-- error= true CI DISPIACE MA NON E' STATO POSSIBILE COMPLETARE LA RICHIESTA -->

            </div>
        </div>
    </main>
        
</template>

<script>
import axios from 'axios'
import AlbumItems from './AlbumItem.vue'

export default{
    name: 'SpMain',
    components:{
        AlbumItems
    },

    data(){
        return{
            albums: [],
            eroor: false
        }
    },

    methods: {
        fetchAlbums: function(){
            axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            .then( res => {
                this.albums = res.data.response;
                this.error = false;
            })
            .catch(err => {
                console.error(err.response);
                this.albums = [];
                this.error = true;
            })
        }
    },

    created() {
        setTimeout(this.fetchAlbums, 1500)
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
        border-color: #fff transparent transparent transparent;
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