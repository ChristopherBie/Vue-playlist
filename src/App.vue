<template>
    <div id="app">
        <playlist-manager></playlist-manager>
    </div>
</template>

<script>
    import PlaylistManager from './components/PlaylistManager.vue'

    export default {
        name: 'App',
        components: {
            PlaylistManager
        }
    }
</script>

<style>
    #app {
        text-align: center;
        margin-top: 60px;
    }
</style>
