<template>

    <div class="filter-wrapper">

        <div class="genre-filter">
            <label for="list-genres">Select a genre:</label>
            <select name="genres" id="list-genres">
                <option value="all">All</option>
                <option v-for="(genre,i) in genres" :key="i" value="genre">{{genre}}</option>
            </select>
        </div>

        <div class="artist-filter">
            <label for="list-artists">Select a genre:</label>
            <select name="genre" id="album-genre">
                <option value="all">All</option>
                <option v-for="(artist,i) in artists" :key="i" value="artist">{{artist}}</option>
            </select>
        </div>

    </div>
    
</template>

<script>
export default{
    name: 'SpSearch',
    props:{
        artists:{
            type: Array
        },
        genres:{
            type: Array
        }
    }
}

</script>

<style lang="scss" scoped>

.filter-wrapper{
    margin-bottom: 30px;
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 20px;
}

@media all and (max-width:500px) {

    .filter-wrapper{
        flex-direction: column;
    }        
}

</style>
