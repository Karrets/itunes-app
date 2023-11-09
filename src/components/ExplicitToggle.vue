<script>
import $ from 'jquery'
import tooltip from "bootstrap/js/src/tooltip";

export default {
  name: "ExplicitToggle",

  props: {
    modelValue: Boolean
  },
  emits: ['update:modelValue'],

  methods: {
    emit(value) {
      this.$emit('update:modelValue', value);
    },

    buttonAction() {
      return this.modelValue ? 'Enable Safe-Search' : 'Disable Safe-Search';
    }
  },

  mounted() {
    tooltip.getOrCreateInstance($('#safe-search-toggle'), {
      title: this.buttonAction
    });
  }
}
</script>

<template>
  <div @click="emit(!modelValue)">
    <input :value="modelValue" ref="ss-check" hidden type="checkbox" id="safe-search" name="safe-search" checked>
    <button id="safe-search-toggle" type="button" data-bs-toggle="tooltip"
            :class="{'btn': true, 'btn-outline-secondary': modelValue, 'btn-secondary': !modelValue}">
      <i v-if="modelValue" class="bi bi-explicit-fill"></i>
      <i v-else class="bi bi-explicit"></i>
    </button>
  </div>
</template>

<style scoped>
</style>