<template>
  <button
    :class="{
      'bg-grey-600 hover:bg-grey-400 border-b-4 border-grey-700 hover:border-grey-500':
        variant === 'default',
      'bg-green-600 hover:bg-green-400 border-b-4 border-green-700 hover:border-green-500':
        variant === 'primary',
      'opacity-50 cursor-not-allowed': disabled || variant === 'disabled',
    }"
    class="text-white font-bold py-1 px-1 rounded"
    :disabled="disabled"
    type="button"
    @click="handleClick"
  >
    <slot></slot>
  </button>
</template>

<script>
export default {
  props: {
    variant: {
      type: String,
      default() {
        return 'default'
      },
    },
    disabled: {
      type: Boolean,
      default() {
        return false
      },
    },
  },
  computed: {},
  methods: {
    handleClick(e) {
      this.$emit('click-button')
    },
  },
}
</script>
