<template>
<div style="display: inline-flex; position: relative;">
<div class="inputDiv">
  <div v-if="changeType">
  <input type="text" class="input" name="name" placeholder="Your Name..." v-model="name">
  <input type="text" class="input" name="lastName" placeholder="Your Last Name..." v-model="lastName">
  <input type="text" class="input" name="age" placeholder="Yuor Age..." v-model="age">
  </div>
  <button class="input" @click="enterInfo" v-if="test.length == 0">Generation</button>
  <button class="input" @click="changeTypeFunction">changeType</button>

  {{ name }}
  {{lastName}}
  {{age}}
</div>
<div class="div2">
  <input type="number" class="num" placeholder="Min-8, Max-20" min="8" max="20" v-model="arrayNum"/>
  <br>
  <br>
  <br>
  <p v-if="test.length != 0">Password- {{test}}</p>
  <br>
  <br>
  <button v-if="test.length != 0" @click="resetButton">Reset</button>
</div>
</div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return {
      name: "",
      lastName: "",
      age: "",
      splitsName: "",
      splitsArrayName:[],
      splitslastName: "",
      splitsArraylastName:[],
      splitsAge: "",
      splitsArrayAge:[],
      arrayNum: null,
      randomNum: 0,
      testAll: [],
      test:[],
      changeType: false
    }
  },
 methods:{
   changeTypeFunction(){
     this.changeType  = !this.changeType
   },
   enterInfo(){
     if(this.changeType){
     if(this.splitsArrayName.length == 0)
    for(var i = 0; i < this.name.length; i++){
      this.splitsName = this.name.charAt(i)
      this.splitsArrayName.push(this.splitsName)
    }if(this.splitsArraylastName.length == 0){
    for(var j = 0; j < this.lastName.length; j++){
      this.splitslastName = this.lastName.charAt(j)
      this.splitsArraylastName.push(this.splitslastName)
    }
    }
    if( this.splitsArrayAge.length == 0){
    for(var k = 0; k < this.age.length; k++){
      this.splitsAge = this.age.charAt(k)
      this.splitsArrayAge.push(this.splitsAge)
    }
    }
   
        this.generation()
   }else{
     this.testAll = ["a","b","c","d","e","f","j","h","i","g","k","l","m","n","o","p","q","r","s","t","w","x","y","z",1,2,3,4,5,6,7,8,9,0,'!','@','#','$','%','^','&','*','(',')','<','>','?','+','-','*','/']
    for(var t = 0; t<Math.round(this.arrayNum); t++){
       this.randomNum = Math.floor(Math.random()*(this.testAll.length));
       this.test.push(this.testAll[this.randomNum])
   }
   this.test= this.test.join("")
   }
   },
   generation(){
     for(var i = 0; i<Math.round(this.arrayNum/3); i++){
       this.randomNum = Math.floor(Math.random()*(this.splitsArrayName.length));
       this.test.push(this.splitsArrayName[this.randomNum])
     }
      for(var j = 0; j<Math.round(this.arrayNum/3); j++){
       this.randomNum = Math.floor(Math.random()*(this.splitsArraylastName.length));
       this.test.push(this.splitsArraylastName[this.randomNum])
     }
      for(var k = 0; k<Math.round(this.arrayNum/3); k++){
       this.randomNum = Math.floor(Math.random()*(this.splitsArrayAge.length));
       this.test.push(this.splitsArrayAge[this.randomNum])
     }
     this.test= this.test.join("")
   },
   resetButton(){
     return this.test = [],
     this.enterInfo()
   }

  },
  mounted(){
    alert("We used your info to generation password, mixed an randomiz Only letter")
  }
}


</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.inputDiv{
  position: relative;
  display: inline-block;
  margin: 0;
  padding: 0;
  left: 15vw;
  top: 15vh;
  background-color: aqua;
}
.input{
  position: relative;
  display: block;
  width: 15vw;
  padding: 20px;
  margin: 50px;
}
.num{
  position: relative;
  display: inline-block;
  margin: 50px;
  width: 10vw;
  height: 8vh;
}
.div2{
  position: relative;
  display: block;
  margin: 0;
  padding: 0;
  left: 35vw;
  top: 15vh;
  background-color: aqua;
  text-align: center;
  align-content: center;
}
p{
  color: red;
  background-color: white;
  height: 10vh;
  text-align: center;
  padding: 30px;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  font-style: italic;
}
</style>
