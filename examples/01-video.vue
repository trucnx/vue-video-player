<template>
  <md-card>
    <md-card-actions>
      <div class="md-subhead">
        <span>Base Config / 基本示例</span>
      </div>
      <md-button class="md-icon-button"
                 target="_blank"
                 href="https://github.com/trucnx/vue-video-player/tree/master/examples/01-video.vue">
        <md-icon>code</md-icon>
      </md-button>
    </md-card-actions>
    <md-card-media>
      <div class="item">
        <div class="player">
          <video-player  class="vjs-custom-skin"
                         ref="videoPlayer"
                         :options="playerOptions"
                         :playsinline="true"
                         :headers="headers"
                         @play="onPlayerPlay($event)"
                         @pause="onPlayerPause($event)"
                         @ended="onPlayerEnded($event)"
                         @loadeddata="onPlayerLoadeddata($event)"
                         @waiting="onPlayerWaiting($event)"
                         @playing="onPlayerPlaying($event)"
                         @timeupdate="onPlayerTimeupdate($event)"
                         @canplay="onPlayerCanplay($event)"
                         @canplaythrough="onPlayerCanplaythrough($event)"
                         @ready="playerReadied"
                         @statechanged="playerStateChanged($event)">
          </video-player>
        </div>
      </div>
    </md-card-media>
  </md-card>
</template>

<script>
  // custom skin css
  import '../src/custom-theme.css'
  
  export default {
    data() {
      return {
        // videojs options
        headers: {
          'Accept': 'application/json, text/plain, */*',
          'Content-Type': 'application/json;charset=UTF-8',
          'Accept-Language': 'zh-CN,zh;q=0.9,hy;q=0.8,mn;q=0.7',
          'Authorization': 'eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJkYXR0cmFuMTk5M0BnbWFpbC5jb20iLCJyb2xlIjoiMiIsImlhdCI6MTYzMzA0Njg3NiwiZXhwIjoxNjY0NjAzODI4fQ.GWu2OGDAtSfI7oXcP8GXmlroMdGCYYBzd72oNTZ02GKEF_VYVqBm6hJUeidBfWHHz34vLTy9PIcYm8UlRmjMdQ'
        },
        playerOptions: {
          height: '360',
          autoplay: true,
          muted: true,
          language: 'en',
          playbackRates: [0.7, 1.0, 1.5, 2.0],
          sources: [{
            type: "video/mp4",
            // mp4
            src: "https://apilivestream.cf/api/v1/videos/web/6695864314054a5e793b798c5e2555e88ec598cfc75e3ef934541f669513580a_1",
            // webm
            // src: "https://cdn.theguardian.tv/webM/2015/07/20/150716YesMen_synd_768k_vp8.webm"
          }],
          poster: "https://surmon-china.github.io/vue-quill-editor/static/images/surmon-1.jpg",
        }
      }
    },
    mounted() {
      // console.log('this is current player instance object', this.player)
      setTimeout(() => {
        console.log('dynamic change options', this.player)

        // change src
        // this.playerOptions.sources[0].src = 'https://cdn.theguardian.tv/webM/2015/07/20/150716YesMen_synd_768k_vp8.webm';

        // change item
        // this.$set(this.playerOptions.sources, 0, {
        //   type: "video/mp4",
        //   src: 'https://cdn.theguardian.tv/webM/2015/07/20/150716YesMen_synd_768k_vp8.webm',
        // })

        // change array
        // this.playerOptions.sources = [{
        //   type: "video/mp4",
        //   src: 'https://cdn.theguardian.tv/webM/2015/07/20/150716YesMen_synd_768k_vp8.webm',
        // }]
        this.player.muted(false)
      }, 5000)
    },
    computed: {
      player() {
        return this.$refs.videoPlayer.player
      }
    },
    methods: {
      // listen event
      onPlayerPlay(player) {
        // console.log('player play!', player)
      },
      onPlayerPause(player) {
        // console.log('player pause!', player)
      },
      onPlayerEnded(player) {
        // console.log('player ended!', player)
      },
      onPlayerLoadeddata(player) {
        // console.log('player Loadeddata!', player)
      },
      onPlayerWaiting(player) {
        // console.log('player Waiting!', player)
      },
      onPlayerPlaying(player) {
        // console.log('player Playing!', player)
      },
      onPlayerTimeupdate(player) {
        // console.log('player Timeupdate!', player.currentTime())
      },
      onPlayerCanplay(player) {
        // console.log('player Canplay!', player)
      },
      onPlayerCanplaythrough(player) {
        // console.log('player Canplaythrough!', player)
      },

      // or listen state event
      playerStateChanged(playerCurrentState) {
        // console.log('player current update state', playerCurrentState)
      },

      // player is ready
      playerReadied(player) {
        // seek to 10s
        console.log('example player 1 readied', player)
        player.currentTime(10)
        // console.log('example 01: the player is readied', player)
      }
    }
  }
</script>

