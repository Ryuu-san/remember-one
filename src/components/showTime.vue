<template>
  <div>
      <p>Время показа: {{time}} сек</p>
      <input type="range" min="0.2" max="2" step="0.2"
      v-model=time @change="$emit('receivingData', [time, 'time'])">
  </div>
</template>

<script>
export default {
  data(){
    return{
      time:0.2
    }
  }
}
</script>