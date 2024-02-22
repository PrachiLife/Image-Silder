<template>
  <div class="flex gap-4">
    <div class="inline-block p-1.5 max-h-[500px] overflow-y-scroll hide-scrollbar">
      <div v-for="index in 8" :key="index" class="m-1.5 p-1" @click="scrollCickedImage(index)" :ref="`image${index}`" :class="activeImage==index ? 'border-2' : '' ">   
        <img :src="`/src/assets/image${index}.jpeg`" alt="images" class="w-24 h-24 object-cover cursor-pointer">
      </div>
    </div>
    <div class="flex max-w-[200px] overflow-x-scroll items-center hide-scrollbar">
        <div v-for="index in 8" :key="index" class="min-w-[200px]" :ref="`horizontalImage${index}`">
            <img :src="`/src/assets/image${index}.jpeg`" alt="image" class="w-full h-[200px]">
        </div>
    </div>
  </div>
</template>

<script>
import { defineComponent } from 'vue'
export default defineComponent({
    name:"ImageSilder",
    data(){
        return{
            activeImage:1,
        }
    },
    methods:{
        async scrollCickedImage(index){
            this.activeImage=index;
            const natureImage=this.$refs[`image${index}`][0];
            await natureImage.scrollIntoView({ behavior: "smooth", block: "center", inline: "center" });
            setTimeout(()=>{
                const horizontalNatureImage=this.$refs[`horizontalImage${index}`][0];
                horizontalNatureImage.scrollIntoView({ behavior: "smooth" });
            },200)
        },
    }
})
</script>

<style scoped>
.hide-scrollbar {
    scrollbar-width: none; /* Firefox */
    -ms-overflow-style: none;  /* Internet Explorer 10+ */
}
.hide-scrollbar::-webkit-scrollbar { /* WebKit */
    width: 0;
    height: 0;
}
</style>