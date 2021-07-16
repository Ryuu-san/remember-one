<template>
  <div>
      <button v-if="!responseTime && !game" @click="startGame">Старт</button>
      <p v-if="game">{{number}}</p>
      <input type="text" v-if="responseTime" v-model="userResponse">
      <button v-if="responseTime" @click="response">Ответить</button>
      <p v-if="victory && victory!== ''">Правильно</p>
      <p v-else-if="!victory && victory!== ''">Неправильно</p>
  </div>
</template>

<script>
export default {
  props:['parameters'],
  data(){
      return{
          game:false,
          responseTime:false,
          number: '',
          userResponse:'',
          victory:''
      }
  },
  methods:{
      startGame(){
          let randomNumber = (Math.random() * 256 + '').replace(/\./g, "").substr(0, this.parameters.size)
          this.number = randomNumber
          this.game = true
          setTimeout(()=>{
              this.game = false
              this.responseTime = true
          },(this.parameters.time * 1000))
      },
      response(){
          if(this.userResponse === this.number) this.victory = true, this.responseTime = false, this.userResponse = '', setTimeout(()=>{this.victory=''},(300))
          else this.victory = false, this.responseTime = false, this.userResponse = '', setTimeout(()=>{this.victory=''},(300))
      }
  }
}
</script>
