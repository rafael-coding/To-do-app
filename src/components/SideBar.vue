<template>
    <header>
        <img src="../assets/logo.png" alt="logo">
    </header>
</template>

<script lang="ts">
    import {defineComponent} from 'vue'

    export default defineComponent({
        name: 'BarraLateral'
    })
</script>

<style scoped>
    header{
        background: #0d3b66;
        width: 100%;
        height: 100vh;
        padding: 1rem;
        display: flex;
    }

    img{
        width: 100px;
        height: 100px;
        margin-inline: auto;
    }

    @media only screen and (max-width: 768px){
        header{
            padding: 2.5rem;
            height: auto;
        }
    }
</style>