<template>
  <div id = "header">
      <ul>
      <center>
        <li><router-link to="/datafile"> <button :style="styleOfButton" > Datafile</button> </router-link>
        <router-link to="/table"><button :style="styleOfButton" >Table</button></router-link>
        <router-link to="/eventmethod"><button :style="styleOfButton" >EventMethod</button></router-link>
        <router-link to="/"><button :style="styleOfButton" >Home</button></router-link>
        <router-link to="/form"><button :style="styleOfButton" >Form</button></router-link></li>
      </center>
    </ul>
  </div>
</template>

<script>
export default {
    name: "Header",
    data() {
        return {
            styleOfButton:{
                fontWeight: '900',
                color: 'grey',
                fontFamily: 'Open Sans',
                fontSize: '30px',
                margin: '20px',
                padding: '10px',
                paddingRight:'30px',
                paddingLeft:'30px',
                borderRadius: '20px',
            }
        }
    },

}
</script>

<style scoped>
@import url(//fonts.googleapis.com/css?family=Open+Sans);


</style>