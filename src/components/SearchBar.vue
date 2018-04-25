<template>

    <div class="search">
        <form @submit.prevent="search">
            <input type="text" v-model="query" />
            <button>Buscar canción</button>
        </form>
    </div>
    
</template>

<script lang="ts">

    import Vue from 'vue';
    import {Component} from 'vue-property-decorator';

    @Component
    export default class SearchBar extends Vue{

        query: string = "";

        search(){
            this.$emit('search', this.query);
        }


    }
</script>

<style scoped>

    form input {
        border-bottom-left-radius: 10px;
        border-top-left-radius: 10px;
        width: 76%;
        border: 1px solid #888;
        padding: 1% 3%;
        height: 20px;
        float: left;
        font-size: 18px;
        color: #444;
    }
    form input:focus {
        outline: none;
    }
    form button {
        border-bottom-right-radius: 10px;
        border-top-right-radius: 10px;
        height: 20px;
        font-size: 15px;
        background: #85B923;
        border: 1px solid #678d1d;
        width: 17.5%;
        text-align: center;
        height: 35px;
    }
    form:after {
        display: block;
        content: " ";
        clear: both;
    }

</style>