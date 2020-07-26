<template>
  <div class="flex flex-wrap items-stretch md:-mr-4">
    <div
      class="w-full pb-2 px-2 md:w-1/2 md:pr-4 md:pb-3 md:px-3 lg:w-1/3 lg:pb-4 lg:px-4"
      v-for="review in reviews"
      :key="review.id"
    >
      <OrganismReviewDetail
        class="h-full cursor-pointer relative"
        :review="review"
        @vote-review="handleVote"
      >
      </OrganismReviewDetail>
    </div>
  </div>
</template>

<script>
export default {
  name: 'OrganismReviewList',
  props: ['reviews'],
  computed: {},
  methods: {
    handleVote(review) {
      this.$emit('vote-review', review)
    },
  },
}
</script>
