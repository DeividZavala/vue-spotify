<template>

    <div class="song-detail">
        <div class="header">
            <img :src="song.album ? song.album.images[0].url : ''" alt="">
            <span class="titulo">{{song ? song.name: 'No disponible'}}</span>
            <span>Album: {{song.album ? song.album.name : 'No disponible'}}</span>
            <span>Duracion: {{song ? song.duration_ms : 'No hay mijo'}}</span>
            <span></span>
        </div>
    </div>

</template>

<script lang="ts">

    import Vue from 'vue';
    import {Component, Prop} from 'vue-property-decorator';

    @Component
    export default class TrackDetail extends Vue{
        @Prop() song: any;

    }

</script>

<style scoped>

    .song-detail {
        float: left;
        padding: 2%;
        width: 46%;
        font-size: 10px;
        color: white;
    }
    .song-detail .header img {
        margin-right: 10px;
        float: left;
        max-height: 250px;
        max-width: 250px;
    }
    .song-detail .header span {
        color: #999;
        font-size: 17px;
        display: block;
    }
    .song-detail .header span.title {
        color: #FFF;
        font-size: 20px;
    }

</style>