<template>
  <div class="flex items-center">
    <div v-for="star in stars" :key="star.score">
      <MoleculeIcon
        icon-name="star"
        :icon-color="star.filled ? '#FECF46' : 'white'"
        ><AtomIconStar
      /></MoleculeIcon>
    </div>
    <AtomText :text="ratingText" class="text-gray-600 text-sm ml-2" />
  </div>
</template>

<script>
export default {
  name: 'MoleculeRating',
  props: {
    score: {
      type: Number,
      default() {
        return 0
      },
    },
  },
  computed: {
    ratingText() {
      return this.score.toFixed(1)
    },
    stars() {
      const result = []
      for (let index = 1; index <= 5; index++) {
        result.push({
          score: index,
          filled: index <= this.score,
        })
      }
      console.log(result)
      return result
    },
  },
  methods: {
    handleClick(e) {
      this.$emit('click')
    },
  },
}
</script>
