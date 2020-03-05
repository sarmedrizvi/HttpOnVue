<template>
  <div class="container">
    <div class="row">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
        <h1>Http</h1>
        <div class="form-group">
          <label for>Username</label>
          <input type="text" class="form-control" v-model="user.username" />
        </div>
        <div class="form-group">
          <label for>Mail</label>
          <input type="text" class="form-control" v-model="user.mail" />
        </div>
        <button class="btn btn-primary" @click="submit">Submit</button>
        <button class="btn btn-primary" @click="fetchData">FetchData</button>
        <ul class="list-group">
          <li class="list-group-item" v-for="(u,i) in getUser" :key="i">{{u.username}} - {{u.mail}}</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      user: {
        username: "",
        mail: ""
      },
      getUser: []
    };
  },
  methods: {
    submit() {
      console.log(this.user);
      this.$http
        .post("", this.user)
        .then(console.log)
        .catch(console.log);
    },
    fetchData() {
      this.$http
        .get("")
        .then(res => res.json())
        .then(data => {
          for (const key in data) {
            this.getUser = [...this.getUser, data[key]];
          }
        });
    }
  }
};
</script>

<style>
</style>
