<template>

    <div class="results">
        <a class="song" v-for="song in playlist" @click="$emit('playSong', song)">
            <span>{{song.name}}</span>
            <span>{{song.album.name}}</span>
            <span>{{song.artists[0].name}}</span>
        </a>
    </div>
    
</template>

<script lang="ts">

    import Vue from 'vue';
    import {Component, Prop} from 'vue-property-decorator';

    @Component
    export default class TracksList extends Vue {

        @Prop() playlist: any[] = [];

        updated(){
            console.log(this.playlist);
        }

    }


</script>

<style scoped>

    .results {
        font-size: 9px;
        width: 50%;
        float: left;
        color: #a3a3a3;
        height: 400px;
        overflow: auto;
    }

    .song {
        cursor: pointer;
        display: block;
        padding: 10px;
        border-bottom: 1px solid #666;
    }
    .results .song span {
        display: block;
        font-size: 14px;
    }
    .results .song span.title {
        font-size: 16px;
        color: #FFFFFF;
    }
    .results .song:last-child {
        border: none;
    }

</style>