<template>
  <div class="main-container">
    <audio
      src="/audio/audio1.mp3" autoplay>
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
      title: 'Wawan & Dheta'
    }
  }
}
</script>
