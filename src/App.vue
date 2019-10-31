<template>
  <div id="app">
    <div class="container">
      <ul class="nav nav-tabs">
        <li role="presentation" class="active">
          <a href="#">Home</a>
        </li>
        <li role="presentation">
          <a href="#">Profile</a>
        </li>
        <li role="presentation">
          <a href="#">Messages</a>
        </li>
      </ul>
        
        <AppTweets :Tweets="Tweets" :Twiter="Twiter" :search="search" :error="error" :showTwit="showTwit" :showTwitSearch="showTwitSearch"></AppTweets>
      
    </div>
  </div>
</template>
<script>
import Tweets from './Tweets.vue';
export default {
  name: "app",
  data() {
    return {
      Tweets: [{ body: "mazin" }, { body: "ali" }],
      Twiter: "",
      error: "Can not Twitter",
      search: "",
      showTwit: true,
      showTwitSearch: false
    };
  },

 

  

  components: {
    AppTweets:Tweets
  },
  
};
</script>
