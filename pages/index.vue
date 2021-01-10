<template>
  <div class="fullPage">
    <div class="application">
      <h1>All Mail</h1>
      <p>Here are all the pieces of mail you've received at your Stable address.</p>
      <div class="mailCards">
        <b-row>
          <b-col v-for="mailItem in displayedData" class="gridItemContainer">
            <MailCard
              :mailData="mailItem"
              />
          </b-col>
        </b-row>
      </div>
      <span class="navigation">
        <p class="left" ><b>{{displayedData.length}}</b> mail items</p>
        <b-button variant="outline-secondary" class="right"
          v-if="displayedData.length<6" disabled>Next</b-button>
        <b-button variant="outline-secondary" class="right" @click="nextPage"
          v-if="displayedData.length>=6">Next</b-button>
        <b-button
          variant="outline-secondary" class="right" v-if="page<=0"
          disabled>Previous</b-button>
        <b-button variant="outline-secondary" class="right" @click="prevPage"
          v-if="page>0">Previous</b-button>
      </span>
    </div>
  </div>
</template>

<script>
// importing the json mail data, in a real app I'd do a db lookup/api call.
import mailData from '~/assets/data.json'
import MailCard from '~/components/MailCard.vue'

// In vue this is where you manage an individual page's state.
// In an actual app I would use the vuex store (same idea as redux), but since
// this is just a demo and I can keep track of the state easily, I will just
// pass data through to
export default {
  components: { MailCard },
  data () {
    return {
      page: 0,
      mailData,
    }
  },
  computed: {
    // displays 6 items at a time (a very hacky demonstrative way to do this)
    displayedData() {
      return mailData.slice(this.page * 6, this.page * 6 + 6)
    },
  },
  methods: {
    prevPage() {
      // likely an api call in a real app, but for demo purposes I'll just decrement
      // the page counter
      this.page -= 1
    },
    nextPage() {
      // likely an api call in a real app, but for demo purposes I'll just increment
      // the page counter
      this.page += 1
    },
  }
}
</script>

<style>

.fullPage {
  padding-top: 2rem;
  margin-top: 0;
}

.gridItemContainer {
  height: 25rem;
  min-width: 20rem;
  margin: 20px;
}

.application {
  margin-left: 15%;
  margin-right: 15%;
}

.left {
  margin-left: 5px; margin-right: 5px;
  display: inline-block;
  float: left;
}

.right {
  margin-left: 5px; margin-right: 5px;
  display: inline-block;
  float: right;
}

</style>
