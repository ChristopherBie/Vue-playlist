<template>
    <div><!-- https://bulma.io/documentation/components/panel/ -->
        <nav class="panel is-info">
            <p class="panel-heading">
                Songlist ({{ songCount }})
            </p>
            <a class="panel-block is-active" 
                v-for="(song, index) in songs" 
                :key="index"
                @click="addToPlaylist(index)">
                <span class="panel-icon">
                    <i class="fas fa-plus" aria-hidden="true"></i>
                </span>
                {{ song.artist }} - {{ song.title }}
            </a>
            <add-song></add-song>
        </nav>
    </div>
</template>

<script>
    import AddSong from './AddSong.vue'; //delete .vue?

    export default {
        name: 'Songlist',
        props: {
            songs: Array
        },
        components: { AddSong },
        computed: {
            // this computed property returns the current song count and is displayed in the panel head
            songCount() {
                return this.songs.length;
            }
        },
        methods: {
            // $emit a custom event to let the parent component know we'd like to remove an item from its songs data
            addToPlaylist(index) {
                this.$emit('add', index);
            }
        }
    }
</script>

<style scoped>

</style>