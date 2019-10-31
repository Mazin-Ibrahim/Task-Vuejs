<template>
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
          />
        </div>
      </div>
</template>

<script>
export default {
    
    props:['Tweets','Twiter','search','error','showTwit'],

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
    }

  },
}
</script>