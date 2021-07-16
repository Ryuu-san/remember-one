<template>
  <div>
    <number-size
        @receivingData="receivingData"
    />
    <show-time
        @receivingData="receivingData"
    />
    <Output
        :parameters="parameters"
    />
  </div>
</template>

<script>
import NumberSize from './numberSize'
import ShowTime from './showTime'
import Output from './output'
export default {
  name: 'App',
  data(){
    return{
      parameters:{
          size:'2',
          time:'0.2'
      }
    }
  },
  components: {
    NumberSize,
    ShowTime,
    Output
  },
   methods:{
    receivingData(data){
        if(data[1] === 'size') this.parameters.size = data[0]
        if(data[1] === 'time') this.parameters.time = data[0]
    }
  }
}
</script>