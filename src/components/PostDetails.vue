<template>
  <loading v-model:active="isLoading" :is-full-page="fullPage" />
  <div class="content-container">
    <div class="content-author">
       <h3>By {{author}}</h3>
    <span> {{post != undefined ? '   ' + moment(post.date_gmt).fromNow(): " "}}</span>
    <!-- <span>{{ moment().fromNow()}}</span> -->
    </div>
     <!-- <h1 v-html="post !=  undefined ? post.title.rendered : ' '"></h1>
    <p v-html="post != undefined ? post.content.rendered : ' '"></p> -->
  </div>
</template>

<script>
import axios from 'axios';
import moment from 'moment';
import Loading from 'vue-loading-overlay';
import 'vue-loading-overlay/dist/vue-loading.css';

export default {
  name: "PostDetails",
  props: {
    id: String
  },
  components: {
    Loading
  },
  data() {
    return {
      post: {},
      author: '',
      isLoading: false,
      fullPage: true,
    }
  },
   created: function () {
    this.moment = moment;
  },
  async mounted() {
    try {
      this.isLoading = true;
      await axios
        .get(`https://techcrunch.com/wp-json/wp/v2/posts/${this.id}`)
        .then((response) => {
          this.post = response.data,
          console.log(response.data)
        })
      await axios
        .get(`https://techcrunch.com/wp-json/tc/v1/users/${this.post.author}`)
        .then((response) => {
          this.author = response.data.name,
          this.isLoading = false
        })
    } catch (error) {
      console.log(error)
    }

  },
  methods: {
    // moment: function () {
    //   return moment();
    // },
    
  }

}
</script>

<style>

</style>