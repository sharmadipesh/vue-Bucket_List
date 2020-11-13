<template>
    <div>
        
        <div class="header-link-container">
            <div class="header-title-style">
                <!-- <img src="/img/logo.svg" height="40px" width="40px" alt="logo"> -->
                <div>
                    Bucket List ://
                </div>
            </div>
            <div id="nav">
                <router-link to="/">Home</router-link> |
                <router-link to="/about">About</router-link>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name:'Header'
    }
</script>

<style scoped>
    .header-title-style{
        font-weight: 700;
        font-size: 35px;
        margin: 0 0 10px 0;
        font-style: italic;
        text-shadow: 2px 3px rgba(0,0,0,0.4);
        letter-spacing: 5px;

        display: flex;
        align-items: center;
        justify-content: center;
    }
    .header-link-container{
        background: #fff;
        padding: 10px 20px;
        box-shadow: 0 10px 20px rgba(0,0,0,0.19), 0 6px 6px rgba(0,0,0,0.23);
        margin: 25px 0;
        width:28vw;
        border-radius: 10px;
        text-align: center;
    }
</style>