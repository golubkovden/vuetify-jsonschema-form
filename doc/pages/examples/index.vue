<template>
  <v-container class="examples-container">
    <example-wrapper v-for="example in examples.filter(e => !e.id.startsWith('_'))" :key="example.key" :params="example" />
  </v-container>
</template>

<script>
import ExampleWrapper from '~/components/example-wrapper'
import { examples } from '~/examples'
import { scrollToHash } from '~/app/router.scrollBehavior.js'

export default {
  components: { ExampleWrapper },
  data: () => ({ examples }),
  mounted() {
    if (this.$route.hash) {
      location.hash = this.$route.hash
      scrollToHash(this.$route.hash, false)
    }
  },
  head() {
    return {
      title: 'vjsf - Examples'
    }
  }
}
</script>

<style lang="css" scoped>
.example-wrapper:last-child {
  height: 100vh;
}
</style>
