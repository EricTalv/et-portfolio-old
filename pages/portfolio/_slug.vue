<template>
  <div>
    <nuxt-content :document="page"></nuxt-content>
  </div>
</template>

<script>
 export default {
   async asyncData({ $content, params }) {
     const page = await $content('portfolio', params.slug).fetch()

     return {
       page
     }
   }
 }
</script>
