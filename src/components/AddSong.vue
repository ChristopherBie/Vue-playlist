<template>
    <div class="panel-block">
        <form @submit.prevent="addNewSong">
            <input type="text" placeholder="Artist" v-model="newArtist">
            <input type="text" placeholder="Title" v-model="newTitle">
            <button type="submit">Add</button>
        </form>
    </div>
</template>

<script>
    export default {
        name: 'AddSong',
        data() {
            return {
                newArtist: '',
                newTitle: ''
            }
        },
        methods: {
            addNewSong() {
                this.$emit('add', {
                    artist: this.newArtist,
                    title: this.newTitle
                });
                this.newArtist = '';
                this.newTitle = '';
                console.log(this.newArtist + ' - ' + this.newTitle);
            }
        }
    }
</script>

<style>

</style>