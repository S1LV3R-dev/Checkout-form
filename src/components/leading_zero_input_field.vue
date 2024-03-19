<script setup>
import { ref } from 'vue'

const props = defineProps({
  class: {
    type: String
  },
  placeholder: {
    type: String
  },
  len: {
    type: Number,
    default: 2
  },
  max: {
    type: Number,
    default: NaN
  },
  min: {
    type: Number,
    default: NaN
  },
  id: {
    type: String,
    required: true
  }
})
const max = ref(props.max)
const [model, modifiers] = defineModel({
  set(value) {
    if (modifiers.leadingZero) {
      if (value) return ('0' + value).slice(-2)
      else return ''
    }
    return value
  }
})
const mask = ref('#'.repeat(props.len))
</script>

<template>
  <input
    :id="props.id"
    :class="props.class"
    type="text"
    v-model="model"
    v-mask="mask"
    :max="max"
    :min="props.min"
    :placeholder="props.placeholder"
  />
</template>
