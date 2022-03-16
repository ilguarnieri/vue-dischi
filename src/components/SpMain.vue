<template>

    <section class="album-wrapper">

        <AlbumItems v-for="(el,i) in albums" :key="i" :album="el"/>        

    </section>
        
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
            albums: undefined
        }
    },

    methods: {
        fetchAlbums: function(){
            axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            .then( res => {
                this.albums = res.data.response;
            })
        }
    },

    created() {
        this.fetchAlbums();
    }
}

</script>

<style lang="scss" scoped>
@import '../assets/scss/variables.scss';
@import '../assets/scss/common.scss';

.album-wrapper{

    @include container;
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
        
}

</style>