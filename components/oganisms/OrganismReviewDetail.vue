<template>
  <div class="flex flex-wrap items-stretch md:-mr-4">
    <MoleculeCard class="w-full h-full cursor-pointer relative">
      <div class="flex flex-col h-full justify-between">
        <div class="flex flex-col">
          <MoleculeRating :score="review.rating" class="mb-3" />
          <AtomSubtitle :text="reviewTime" />
          <AtomText :text="review.comment" class="mb-4" />
        </div>
        <div class="flex items-center">
          <AtomButton
            variant="primary"
            @click-button="handleVote(review)"
            class="mr-3"
          >
            <MoleculeIcon icon-name="hand" icon-color="white" class="mr-1"
              ><AtomIconHand
            /></MoleculeIcon>
            <span class="text-xs p-0">Es útil</span>
          </AtomButton>
          <AtomText :text="peopleLikes" class="text-gray-600 text-xs" />
        </div>
      </div>
    </MoleculeCard>
  </div>
</template>

<script>
import moment from 'moment'

export default {
  name: 'OrganismReviewDetail',
  props: ['review'],
  computed: {
    reviewTime() {
      return this.review.author + ' el ' + this.formatDate(this.review.date)
    },
    peopleLikes() {
      // TODO: It could also be: " personas créeis que es útil"
      return this.review.useful_count + ' personas creen que es útil'
    },
  },
  methods: {
    formatDate(value) {
      // TODO: Use proper date format as following:
      // "Cristina el lunes, 12 de agosto de 2018"
      return moment(String(value)).format('e[,] DD [de] MMM [de] YYYY')
    },
    handleVote(review) {
      this.$emit('vote-review', review)
    },
  },
}
</script>
