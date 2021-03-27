<template>
  <div>
    <div>
      <timer/>
      <button @click="playSound();continuePlay();" >Click to play</button>
    </div>
    
    <p id="para" class="logo-1">{{coloredString}}</p>
    
  </div>
</template>

<script>
import json from "@/assets/letter/letter.json"
import timer from "@/components/layout/timer.vue"


export default {
  name: "app",
  components: {
    timer
  },
  
  data() {
    return {
      myTrack: new Audio(),
      letter: json.letters,
      i:0,
      j:0,
      stop:false,
      thisString:[],
      coloredString:[],
      isPlay:false,
      currentSound:"",
    };
  },
  methods: {
    testEvent() {
      document.getElementById("testEvent").innerHTML = " hello test is work !";
    },
    clear() {
      
    },
    onClock(value){
        this.time = value
    },
    playSound(){
      this.makeString()
      console.log(this.stop)
      if(this.letter[this.j][this.i].source !== ""){

        this.myTrack = new Audio()
        this.myTrack.src = this.letter[this.j][this.i].source
        this.myTrack.play()
        this.myTrack.addEventListener('ended',function() {
          this.i++
              if(this.i > this.letter[this.j].length-1){
                this.i = 0
                this.j++
                this.thisString =[]
                this.coloredString = []
                this.stop = true
              }
              if(!this.stop)
              this.playSound()
        }.bind(this))
      }
      else{
        this.i++
        if(!this.stop)
              this.playSound()
      }
    
      
    },
    continuePlay(){
      if(this.stop){
        this.stop = false;
      }
    },
    makeString :function()  
    {
      var para =document.getElementById("para")
      var lastString = [];
      if(this.letter[this.j][this.i].swap === "0"){
        if(this.letter[this.j][this.i].char !== ''){
          this.thisString.push(this.letter[this.j][this.i].char)
          this.coloredString.push(this.letter[this.j][this.i].color)
        }
       }
       else if(this.letter[this.j][this.i].swap !== "0"){
         if(this.letter[this.j][this.i].char !== ''){

           this.thisString = this.swap(this.thisString, this.letter[this.j][this.i].char , this.letter[this.j][this.i].swap )
           this.coloredString = this.swap(this.coloredString, this.letter[this.j][this.i].color , this.letter[this.j][this.i].swap )
         }
       }
       for(let index = 0;index < this.thisString.length;index++){

            if( this.coloredString[index] == 'blue'){
              let lastStrings = "<sup style='color: " + this.coloredString[index] + ";'>" + this.thisString[index] + "</sup>"
              lastString.push(lastStrings)
            }
            else if (this.coloredString[index] == 'green'){
              let lastStrings = "<span style='color: " + this.coloredString[index] + ";'>" + this.thisString[index] + "</span>"
              lastString.push(lastStrings)
            }
            else{
            let lastStrings = "<strong style='text-align:center; color: " + this.coloredString[index] + ";'>" + this.thisString[index] + "</strong>"
            lastString.push(lastStrings)

            }
          }
    
       
       console.log(this.coloredString)
       console.log(this.thisString)
       para.innerHTML = lastString.join("")

    },
      swap(thisstring , character , num){
        thisstring.splice(thisstring.length-num , 0 , character);
        return thisstring
     },
     
     

},
  mounted: function() {
    this.i = 0

  },
};
</script>

<style>

.error_template {
  
  background-color: gainsboro;
  color: darkmagenta;
  font-size: 50px;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}
.error_template2 {
  font-weight: 900;
  background-image: url(https://images2.alphacoders.com/994/thumb-1920-994016.png);
  
}
.content-wrapper{
  margin: 24px;
  padding: 24px;
  border-width: 3px;
  border-color: blanchedalmond;
  border-style: dashed;    
}
:root {
  --shadow-color: rgba(255, 238, 0, 0.548);
  --shadow-color-light: white;
  color: lightseagreen;
}

* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

body {
  font-family: "Archivo", sans-serif;
  background-color: #192824;
}

p {
 
  font-size: 400px;
  text-transform: uppercase;
  font-family: "Archivo Black", "Archivo", sans-serif;
  font-weight: normal;
  display: block;
  height: auto;
  text-align: center
}

.logo-1 {
  color: white;
  animation: neon 1s infinite;
  transition: .5s;
  margin: 0;
  
  
}

@keyframes neon {
  0% {
    text-shadow: -1px -1px 1px var(--shadow-color-light), -1px 1px 1px var(--shadow-color-light), 1px -1px 1px var(--shadow-color-light), 1px 1px 1px var(--shadow-color-light),
    0 0 3px var(--shadow-color-light), 0 0 10px var(--shadow-color-light), 0 0 20px var(--shadow-color-light),
    0 0 30px var(--shadow-color), 0 0 40px var(--shadow-color), 0 0 50px var(--shadow-color), 0 0 70px var(--shadow-color), 0 0 100px var(--shadow-color), 0 0 200px var(--shadow-color);
  }
  50% {
    text-shadow: -1px -1px 1px var(--shadow-color-light), -1px 1px 1px var(--shadow-color-light), 1px -1px 1px var(--shadow-color-light), 1px 1px 1px var(--shadow-color-light),
    0 0 5px var(--shadow-color-light), 0 0 15px var(--shadow-color-light), 0 0 25px var(--shadow-color-light),
    0 0 40px var(--shadow-color), 0 0 50px var(--shadow-color), 0 0 60px var(--shadow-color), 0 0 80px var(--shadow-color), 0 0 110px var(--shadow-color), 0 0 210px var(--shadow-color);
  }
  100% {
    text-shadow: -1px -1px 1px var(--shadow-color-light), -1px 1px 1px var(--shadow-color-light), 1px -1px 1px var(--shadow-color-light), 1px 1px 1px var(--shadow-color-light),
    0 0 3px var(--shadow-color-light), 0 0 10px var(--shadow-color-light), 0 0 20px var(--shadow-color-light),
    0 0 30px var(--shadow-color), 0 0 40px var(--shadow-color), 0 0 50px var(--shadow-color), 0 0 70px var(--shadow-color), 0 0 100px var(--shadow-color), 0 0 200px var(--shadow-color);
  }
}
</style>
