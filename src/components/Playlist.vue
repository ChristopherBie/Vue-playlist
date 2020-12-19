<template>
    <div><!-- https://bulma.io/documentation/components/panel/ -->
        <nav class="panel is-success">
            <p class="panel-heading">
                Playlist ({{ songCount }})
            </p>
            <a class="panel-block is-active" 
                v-for="(song, index) in songs" 
                :key="index"
                @click="removeFromPlaylist(index)">
                <span class="panel-icon">
                    <i class="fas fa-times" aria-hidden="true"></i>
                </span>
                {{ song.artist }} - {{ song.title }}
            </a>
        </nav>
    </div>
</template>

<script>
    export default {
        name: 'Playlist',
        props: {
            songs: Array
        },
        computed: {
            // this computed property returns the current song count and is displayed in the panel head
            songCount() {
                return this.songs.length;
            }
        },
        methods: {
            // $emit a custom event to let the parent component know we'd like to remove an item from its playlistSongs data
            removeFromPlaylist(index) {
                this.$emit('remove', index);
            }
        }
    }
</script>

<style scoped>

</style>