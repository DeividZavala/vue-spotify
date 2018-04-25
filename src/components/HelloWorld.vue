<template>
  <div class="hello">

    <div class="spotify-player">

      <SearchBar @search="search($event)" ></SearchBar>

      <div class="player">

        <TracksList :playlist="playlist" @playSong="playSong($event)"></TracksList>

        <TrackDetail :song="current_song"></TrackDetail>

      </div>

    </div>

  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import SearchBar from './SearchBar.vue';
import TrackDetail from './TrackDetail.vue';
import TracksList from './TracksList.vue';

@Component({
    components: {
        SearchBar,
        TrackDetail,
        TracksList
    }
})
export default class HelloWorld extends Vue {

    playlist: any[] = [];
    player = new Audio;
    current_song: any = {};
    token = 'BQCCNN3pDGMoXGn7gnO5asxewsAwzVfB55OVIyCIl5dceMeT8Uhtq-d1T0kzrCnn4YiVWcRQlSkbzWP2Y5VyEt_xA5R6zaKkq1_IIW6qbrHwGWngIyNt1izTFdybDjRlp9NXoLt3VVz-dyZu8_DVMt0m4ODySmIqZ2I'

    search(query: string){
        console.log(query);
        fetch(`https://api.spotify.com/v1/search?q=${query}&type=track%2Cartist&limit=20`,{
            headers:{
                'Authorization': `Bearer ${this.token}`
            }
        })
            .then(res=>{
                return res.json();
            })
            .then(data=>{
                this.playlist = data.tracks.items;
            })
    }

    playSong(song: any){
        this.current_song = song;
        this.player.src = song.preview_url;
        this.player.play();
    }


}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
