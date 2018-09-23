<template>
  <div class="keys">
    <div v-for="key in keys" class="key" :class="{ 'playing': key.pressing }">
      <kbd>{{ key.keyName }}</kbd>
      <span class="sound">{{ key.text }}</span>
    </div>
  </div>

</template>

<script>
    export default {
      data() {
        return {
          keys: [{ keyCode: 65, keyName: 'A', text: "clap", src: "clap.wav", pressing: false },
                 { keyCode: 83, keyName: 'S', text: "hihat", src: "hihat.wav", pressing: false },
                 { keyCode: 68, keyName: 'D', text: "kick", src: "kick.wav", pressing: false },
                 { keyCode: 70, keyName: 'F', text: "openhat", src: "openhat.wav", pressing: false },
                 { keyCode: 71, keyName: 'G', text: "boom", src: "boom.wav", pressing: false },
                 { keyCode: 72, keyName: 'H', text: "ride", src: "ride.wav", pressing: false },
                 { keyCode: 74, keyName: 'J', text: "snare", src: "snare.wav", pressing: false },
                 { keyCode: 75, keyName: 'K', text: "tom", src: "tom.wav", pressing: false },
                 { keyCode: 76, keyName: 'L', text: "tink", src: "tink.wav", pressing: false }]
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
              key.pressing = true;
              setTimeout(() => {
                key.pressing = false;
              }, 300);
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
