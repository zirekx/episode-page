<template>
  <div>
<div id="wrapper">
 <div id='player_wrapper'>
  <video
  ref = "videoPlayer"
  id='video_player'>
   <source src='@/assets/filmik.mp4' type='video/mp4'>
  </video>
  <div id='player_controls'>

   <input v-if="isPlaying" type="image" 
   :src="pauseButtonImage" 
   @click="toggle_vid" id="play_button">
   <input v-else type="image" 
   :src="playButtonImage" 
   @click="toggle_vid" id="play_button">
  
   <img src="images/volume.png" id="vol_img">
   <input ref = "volumePlayer" type="range" id="change_vol" @click="change_volume" step="0.05" min="0" max="1" value="1">
  </div>
 </div>
</div>
  </div>

</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return{
      isPlaying: false,
      playButtonImage: require('@/assets/play.png'),
      pauseButtonImage: require('@/assets/pause.png'),
      currentTime: 0
      
    }
  },
  methods: {
    toggle_vid(){
      if(this.$refs.videoPlayer.paused)
       {
        this.isPlaying = true;
        this.$refs.videoPlayer.play();
       }
       else{
        this.$refs.videoPlayer.pause();
        this.isPlaying = false;
       }

    },
    change_volume(){
      this.$refs.videoPlayer.volume= this.$refs.valuePlayer;
    },
    stop_video(){
      this.$refs.videoPlayer.pause();
      this.currentTime = 0;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
#wrapper
{
 text-align:center;
 margin:0 auto;
 padding:0px;
 width:995px;
}
#player_wrapper
{
 position:relative;
 width:400px;
 margin-left:300px;
}
#video_player
{
 width:400px;
}
#player_controls
{
 top:98%;
 position:absolute;
 background-color:black;
 width:100%;
 padding:5px;
 box-sizing:border-box;
}
input[type="image"]
{
 float:left;
 height:20px;
 margin-left:2px;
 margin-right:5px;
 margin-top:2px;
}
#vol_img
{
 margin-left:150px;
 width:20px;
}
</style>
