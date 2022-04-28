<template>
  <label  class="form-label h2">Max Price (${{modelValue}})</label>
  <div class="badge bg-success ml-3">results: {{products.length}}</div>

  <input type="number" class="form-control" min="0" max="130" :value="modelValue" @input="$emit('update:modelValue', $event.target.value)">
</template>

<script>
export default {
  name: "RangeSelector",
  props:["products","modelValue"]
}
</script>

<style scoped>

</style>