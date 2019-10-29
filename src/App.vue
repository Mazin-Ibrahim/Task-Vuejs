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

      <div class="row" style="margin-top: 25px;font-family: 'Cairo', sans-serif;">
        <div class="col-md-3 col-md-offset-3">
          <div v-if="Twiter.length >40" class="alert alert-danger">{{errorMesg()}}</div>
          <ul v-for="(twit,i) in filteredTweets" :key="i" class="list-group">
            <li class="list-group-item">{{twit.body}}</li>
          </ul>
          <textarea cols="30" rows="10" v-model="Twiter" class="form-control"></textarea>
          <button class="btn btn-info" @click="AddTwiter" style="margin-top: 25px">تغريده جديده</button>
        </div>
        <div class="col-md-3">
          <input
            type="text"
            class="form-control"
            placeholder="أبحث عن تغريده"
            v-model="search"
            @input="setting($event)"
          />
        </div>
      </div>
    </div>
  </div>
</template>
<script>
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

  computed: {
    filteredTweets() {
      {
        if (this.search) {
          return this.Tweets.filter(item => {
            return item.body.indexOf(this.search.toLowerCase())>-1
          });
        } else {
          return this.Tweets;
        }
      }
    }
  },

  methods: {
    AddTwiter: function() {
      if (this.Twiter.length > 40) {
        return errorMesg();
      }

      var body = this.Twiter.trim();
      if (body) {
        this.Tweets.push({ body: body });
      }

      this.Twiter = "";
    },
    errorMesg: function() {
      return this.error;
    },

    // setting($event) {
    //   if (event.target.value) {
    //     this.showTwit = false;
    //     this.showTwitSearch = true;
    //   } else {
    //     this.showTwit = true;
    //     this.showTwitSearch = false;
    //   }
    // }
  }
};
</script>
