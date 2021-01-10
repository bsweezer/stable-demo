<template>
  <b-card
    :title="mailData.from"
    :img-src="mailData.imageUrl"
    footer-tag="footer"
    img-alt="Image"
    img-top
    style="height: 25rem; max-width: 20rem;"
    class="overflow-hidden mb-3" >
    <div class="recipientLine" v-if="mailData.businessRecipient">
      <img
        src="https://s3-us-west-2.amazonaws.com/usestable.com-assets/icons/company.svg"
        alt="business recipient"
        class="icon"
        />
      <label>{{mailData.businessRecipient}}</label>
    </div>
    <div class="recipientLine" v-if="mailData.individualRecipient">
      <img
        src="https://s3-us-west-2.amazonaws.com/usestable.com-assets/icons/recipient.svg"
        alt="individual recipient"
        class="icon"
        />
      <label>{{mailData.individualRecipient}}</label>
    </div>
    <div class="scanLine" v-if="mailData.scan">
      <span v-if="mailData.scan.status === 'processing'">
        <img
          src="https://s3-us-west-2.amazonaws.com/usestable.com-assets/icons/processing.svg"
          alt="scan processing"
          class="icon"
          />
        <label>Scan processing</label>
      </span>
      <span v-else-if="mailData.scan.status === 'completed'">
        <img
          src="https://s3-us-west-2.amazonaws.com/usestable.com-assets/icons/scan.svg"
          alt="scanned"
          class="icon"
          />
        <label>Scanned</label>
      </span>
    </div>
    <div class="shredLine" v-if="mailData.shred">
      <span v-if="mailData.shred.status === 'processing'">
        <img
          src="https://s3-us-west-2.amazonaws.com/usestable.com-assets/icons/processing.svg"
          alt="shred processing"
          class="icon"
          />
        <label>Shred processing</label>
      </span>
      <span v-else-if="mailData.shred.status === 'completed'">
        <img
          src="https://s3-us-west-2.amazonaws.com/usestable.com-assets/icons/shred.svg"
          alt="shredded"
          class="icon"
          />
        <label>Shredded</label>
      </span>
    </div>
    <div class="forwardLine" v-if="mailData.forward">
      <span v-if="mailData.forward.status === 'processing'">
        <img
          src="https://s3-us-west-2.amazonaws.com/usestable.com-assets/icons/processing.svg"
          alt="forward processing"
          class="icon"
          />
        <label>Forward processing</label>
      </span>
      <span v-else-if="mailData.forward.status === 'completed'">
        <img
          src="https://s3-us-west-2.amazonaws.com/usestable.com-assets/icons/forward.svg"
          alt="forwarded"
          class="icon"
          />
        <label>Forwarded</label>
      </span>
    </div>
    <template #footer class="footer">
      <label class="footerDate">
        {{humanDate(mailData.timestamp)}}
      </label>
    </template>
  </b-card>
</template>

<script>
// I used moment because I couldn't be bothered to manually parse a timestamp
// and make it look pretty
import moment from 'moment'

// props = the stuff you pass in from the parent
export default {
  props: ['mailData'],
  methods: {
    humanDate(timestamp) {
      return moment(timestamp).format('LL')
    }
  }
}
</script>

<style>
.icon {
  height: 30px;
  width: 30px;
}

label {
  color: gray;
}

.footer {
  background-color: white;
}
.footerDate {
  float: right;
}
</style>