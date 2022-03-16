<template>

    <header>
        <figure class="header__logo">
            <img src="../assets/img/logo.png" alt="logo">
        </figure>
    </header>
        
</template>

<script>

export default{
    name: 'SpHeader'
}

</script>

<style lang="scss" scoped>

header{

    padding: 10px 20px;
    background-color: rgba(white, 0.1);
    position: fixed;
    top: 0;
    left: 0;
    right: 0;

    .header__logo{
        width: 45px;
        cursor: pointer;
        display: block;
    }
}

</style>