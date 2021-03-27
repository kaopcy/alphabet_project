<template>
    <span class="footer" :style="{color:color}">{{title}}</span>
  
</template>

<script>
export default {
    name: "Footer",
    mounted() {
        setInterval(()=>{
            this.$emit('onClock',this.count+=1)
        },100)
    },
    props:{
         title: Number,
         color: String
    },
    data() {
        return {
            count:0,      
        }
    },


}
</script>

<style scoped>
.footer{
    font-size: 50px;
    color:bisque;
    font-family: 'tahoma';
    margin: 50px;
}
</style>>
