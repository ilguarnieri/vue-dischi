<template>

    <main>   
        <div class="container">
            <div class="albums-wrapper">

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
}

</style>