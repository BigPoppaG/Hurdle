<template>
  <div class="common-error text-sm-left">
    <div v-if='"description" in error'>{{error.description}}</div>
    <div v-if='"image" in error'>
        <img v-bind:src="error.image">
    </div>    
    <div v-if='"videoLink" in error'>
        <iframe 
            :src="error.videoLink + '? autoplay=0&rel=0'"
            width="560" 
            height="315"
            frameborder="0" 
            allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" 
            allowfullscreen
            >
            Video Unavalable
        </iframe>
    </div>      
  </div>
</template>

<script>
export default {
    name: 'CommonError',
    props: {
      error: Object
    },
}
</script>

<style>

</style>