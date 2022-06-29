<template>
  <div class="main-container">
    <iframe src="/audio/silence.mp3" allow="autoplay" style="display: none;" frameborder="0"></iframe>
    <audio
      id="bg_audio"
      autoplay
      loop
      src="/audio/audio1.mp3" ref="bg_audio_ref">
      Your browser does not support the
      <code>audio</code> element.
    </audio>
    <Cover/>
    <Content/>
  </div>
</template>

<script>
import Cover from "../components/Cover.vue"
import Content from "../components/Content.vue"
export default {
  name: 'IndexPage',
  component: {
    Cover,
    Content
  },
  head() {
    return {
      title: 'Wawan & Dheta',
      meta: [
        {
          hid: 'og:title', property: 'og:title', content: 'Undangan Pernikahan Wawan & Dheta'
        },
        {
          hid: 'og:image', property: 'og:image', content: '/img/pra-wedding1.png'
        },
      ]
    }
  },
  mounted() {
    window.addEventListener('scroll', () => {
      this.initBgAudio()
    })
  },
  methods: {
    initBgAudio() {
      this.$refs.bg_audio_ref.play()
    }
  }
}
</script>
