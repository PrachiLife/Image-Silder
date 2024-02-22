<script>
import {defineComponent} from 'vue'
import ImageSilder from './components/ImageSlider.vue'
export default defineComponent({
  name:"App",
  components:{
    ImageSilder,
  }
})
</script>

<template>
  <div>
   <image-silder/>
  </div>
</template>

<style scoped>

</style>
