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
@import '../assets/scss/variables.scss';

header{
    height: 70px;
    background-color: $bgHeader;
    display: flex;
    align-items: center;

    .header__logo{
        width: 45px;
        margin-left: 20px;
    }

}

</style>