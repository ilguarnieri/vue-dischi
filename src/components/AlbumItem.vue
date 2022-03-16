<template>

    <div class="album-item">

        <figure class="album__img">
            <img class="album__img" :src="album.poster">
        </figure>

        <div class="album__info">
            <h3 class="album__title">{{album.title}}</h3>

            <p class="album__artist">{{album.author}}</p>
            <p class="album__year">{{album.year}}</p>
        </div>


    </div>
    
</template>

<script>
export default {
    name: 'AlbumItems',
    props: {
        album:{
            type: Object,
            required: true
        }
    }    
}
</script>

<style lang="scss" scoped>
@import '../assets/scss/variables.scss';

.album-item{

        display: flex;
        flex-direction: column;
        align-items: center;
        height: 360px;
        width: calc((100% / 5) - 30px);
        background-color: $bgHeader;

        .album__img{
            aspect-ratio: 1;
            width: 160px;
            margin-bottom: 25px;
        }

        .album__info{

            .album__title{
                text-transform: uppercase;
                margin-bottom: 40px;
            }
    
            .album__artist, .album__year{
                color: $bgGray;
                font-weight: 700;
            }
        }

    }

</style>