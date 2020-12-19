<template>
    <div id="playlistManager">
        <h1 class="title">Playlist Manager</h1>
        <section>
            <songlist :songs="songs" @add="moveToPlaylist"></songlist>
            <playlist :songs="playlistSongs" @remove="moveToSonglist"></playlist>
        </section>
    </div>
</template>

<script>
    import Playlist from './Playlist';
    import Songlist from './Songlist';

    export default {
        name: 'PlaylistManager',
        components: { Playlist, Songlist },
        data() {
            return {
                playlistSongs: [],  // this array will hold on to songs that have been added to the playlist
                songs: [
                    { artist: 'Deftones, Mike Shinoda', title: 'Passenger - Mike Shinoda Remix' },
                    { artist: 'Polyphia', title: 'G.O.A.T.' },
                    { artist: 'Guggenz', title: 'Moonwalker' },
                    { artist: 'Jaytech', title: 'Obelisk' },
                    { artist: 'Devin Townsend', title: 'Offer Your Light' },
                    { artist: 'Andy Mineo, Lecrae', title: 'Coming In Hot' },
                    { artist: 'Parov Stelar', title: 'Booty Swing' },
                    { artist: 'Kygo, Whitney Houston', title: 'Higher Love' }
                ]
            }
        },
        methods: {
            moveToPlaylist(index) {
                // splice the song out of songs and into playlistSongs
                let song = this.songs.splice(index, 1)[0];
                this.playlistSongs.splice(0, 0, song);
            },
            moveToSonglist(index) {
                // splice the song out of playlistSongs and into songs
                let song = this.playlistSongs.splice(index, 1)[0];
                this.songs.splice(0, 0, song);
            }
        }
    }
</script>

<style scoped>
    #playlistManager > section {
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-gap: 1rem;
        padding: 1rem;
    }
</style>