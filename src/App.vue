<template>
  <div class="keys">
    <div v-for="key in keys" class="key">
      <kbd>{{ key.keyName }}</kbd>
      <span class="sound">{{ key.text }}</span>
    </div>
  </div>

</template>

<script>
    export default {
      data() {
        return {
          keys: [{ keyCode: 65, keyName: 'A', text: "clap", src: "clap.wav" },
                 { keyCode: 83, keyName: 'S', text: "hihat", src: "hihat.wav" },
                 { keyCode: 68, keyName: 'D', text: "kick", src: "kick.wav" },
                 { keyCode: 70, keyName: 'F', text: "openhat", src: "openhat.wav" },
                 { keyCode: 71, keyName: 'G', text: "boom", src: "boom.wav" },
                 { keyCode: 72, keyName: 'H', text: "ride", src: "ride.wav" },
                 { keyCode: 74, keyName: 'J', text: "snare", src: "snare.wav" },
                 { keyCode: 75, keyName: 'K', text: "tom", src: "tom.wav" },
                 { keyCode: 76, keyName: 'L', text: "tink", src: "tink.wav" }]
        }
      },
      methods: {
        playSound: function(e) {
          this.keys.forEach(function(key) {
            if(key.keyCode !== e.keyCode) {
              return;
            }
            else {
              const audio = new Audio(`./src/assets/${key.src}`);
              audio.play();
            }
          });
        }
      },
      mounted: function() {
        window.addEventListener('keydown', this.playSound);
      }
    }
</script>

<style>
</style>
