<template>
  <div id="timer">
      <h1>Hello this is timer {{minute}}:{{second}}</h1>
  </div>

</template>

<script>
export default {
    name: "timer",
    data() {
        return {
            minute: 30,
            second: 60
            
        }
    },
    methods: {
    },
    mounted() {
        setInterval(() => {
            this.second--
            if(this.second <= 0){
                this.minute--
                this.second = 60
            }
            
        }, 1000);
    },


}
</script>

<style>

</style>