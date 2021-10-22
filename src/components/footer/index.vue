<template>
    <footer>
        <p>Copyright &copy; 2021</p>
        <router-link to='/about'>About</router-link>
        <img alt="Vue logo" src="../../assets/logo.png" />
    </footer>
</template>

<script>
    export default {
        name: 'Footer'
    }
</script>

<style scoped>
    a {
        color: #333;
    }
    footer {
        margin-top: 30px;
        text-align: center;
    }

    img {
        display: block;
        margin: 10px auto;
        height: 20px;
        width: auto;
    }
</style>