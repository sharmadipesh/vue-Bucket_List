<template>
    <div id="app">
        <Header />
        <router-view/>
    </div>
</template>

<script>

    import Header from './components/layout/Header';

    export default {
        components :{
            Header
        }
    }
</script>

<style>
 *{
        margin: 0;
        padding: 0;
    }

    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        color: #2c3e50;

        /* temparary style */
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    #nav a {
        font-weight: 900;
        color: #2c3e50;
        text-decoration: none;
        font-style: italic;
    }

    #nav a.router-link-exact-active {
        color: #42b983;
    }

    .card-style{
        box-shadow: 0 0 10px 10px rgba(0,0,0,0.12);
        padding:10px 20px;
        border-radius: 10px;
        width: 28vw;
        margin-bottom: 20px;
    }
</style>
