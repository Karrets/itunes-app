<script>
export default {
  name: "ExplicitToggle",

  props: {
    modelValue: Boolean
  },
  emits: ['update:modelValue'],

  methods: {
    emit(value) {
      console.log('test')
      this.$emit('update:modelValue', value);
    }
  }
}
</script>

<template>
  <div @click="emit(!modelValue)">
    <input :value="modelValue" ref="ss-check" hidden type="checkbox" id="safe-search" name="safe-search" checked>
    <i v-if="modelValue" class="bi bi-explicit sfw-toggle"></i>
    <i v-else class="bi bi-explicit-fill sfw-toggle"></i>
  </div>
</template>

<style scoped>

.sfw-toggle {
  font-size: 2rem;
}
</style>