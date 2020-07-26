<template>
  <div>
    <div class="w-full">
      <div class="pb-2 px-2 md:pb-3 md:px-3 lg:pb-4 lg:px-4">
        <AtomTitle tag="h1" content="Valoraciones del producto" />
        <AtomText
          text="Aquí puedes consultar las últimas valoraciones que los usuarios han hecho sobre este producto."
        />
      </div>
      <div class="divide-y-3 divide-grey-500">
        <OrganismReviewList
          class="py-3 px-1"
          :reviews="list"
          @vote-review="handleVoteReview"
        />
      </div>
    </div>
  </div>
</template>

<script>
import { mapState, mapMutations, mapActions } from 'vuex'

// TODO: Connect with store, in the meanwhile the code is commented
export default {
  layout: 'mainLayout',
  components: {},
  // computed: {
  //   ...mapState('modules/reviews', ['list']),
  // },
  data() {
    return {
      list: [],
    }
  },
  created() {
    this.getAllReviews()
  },
  methods: {
    async getAllReviews() {
      const result = await this.$axios.get('/reviews.json')
      this.list = result.data.reviews
    },
    // ...mapMutations({
    //   voteReview: 'modules/reviews/voteReview',
    // }),
    // ...mapActions({
    //   getAllReviews: 'modules/reviews/getAllReviews',
    // }),
    handleVoteReview(review) {
      // this.voteReview(review)
    },
  },
}
</script>
