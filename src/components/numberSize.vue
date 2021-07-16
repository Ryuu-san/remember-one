<template>
  <div>
      <p>Размер числа: {{size}}</p>
      <input type="range" min="2" max="5" step="1" v-model=size @change="$emit('receivingData', [size, 'size'])">
  </div>
</template>

<script>
export default {
  data(){
    return{
      size:2
    }
  }
}
</script>

