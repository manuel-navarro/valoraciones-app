<template>
  <div
    @click="handleClick"
    class="p-6 border border-grey-500 shadow-xs hover:shadow-lg rounded-md transition ease-in-out duration-500"
  >
    <slot></slot>
  </div>
</template>

<script>
import AtomTitle from '@/components/atoms/AtomTitle'
import AtomText from '@/components/atoms/AtomText'

export default {
  name: 'MoleculeCard',
  props: {
    card: {
      type: Object,
      default() {
        return { title: '', text: '' }
      },
    },
  },
  components: {
    AtomTitle,
    AtomText,
  },
  methods: {
    handleClick(e) {
      this.$emit('click')
    },
  },
}
</script>
