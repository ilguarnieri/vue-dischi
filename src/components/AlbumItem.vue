<template>

    <div class="album-item">
        <figure class="album__img">
            <img :src="album.poster">
        </figure>

        <div class="album__info">
            <h3 class="album__title">{{album.title}}</h3>
            <p class="album__artist">{{album.author}}</p>
            <p class="album__year">{{album.year}}</p>
        </div>
    </div>
    
</template>

<script>
export default{
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

.album-item{
    text-align: center;
    background-color: rgba(white, 0.1);
    padding: 20px;
    border-radius: 10px;
    box-shadow: 5px 4px 14px 0px rgba(black, 0.5);
    cursor: pointer;
    user-select: none;
    transition: all 350ms ease-in-out;

    &:hover{
        transform: scale(1.05);
    }

    .album__img{
        max-height: 160px;
        overflow: hidden;
        margin-bottom: 20px;
        border-radius: 10px;

        img{
            object-fit: cover;
            aspect-ratio: 1;
        }
    }

    .album__title{
        margin-bottom: 25px;
    }

    .album__artist, .album__year{
        color: #808080;
        font-weight: 700;
    }
}

</style>