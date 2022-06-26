<template>
  <div class="main-container">
    <Cover/>
    <Content/>
  </div>
</template>

<script>
import Cover from "../components/Cover.vue"
import Content from "../components/Content.vue"
export default {
  title: 'Tes',
  name: 'IndexPage',
  component: {
    Cover,
    Content
  }
}
</script>
