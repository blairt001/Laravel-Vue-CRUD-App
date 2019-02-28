<template>
  <div>
    <h1>Create A Quote</h1>
    <form @submit.preventDefault="addPost">
      <div class="row">
        <div class="col-md-6">
          <div class="form-group">
            <label>Author:</label>
            <input type="text" class="form-control" v-model="post.title">
          </div>
        </div>
        </div>
        <div class="row">
          <div class="col-md-6">
            <div class="form-group">
              <label>Quote:</label>
              <textarea class="form-control" v-model="post.body" rows="5"></textarea>
            </div>
          </div>
        </div><br />
        <div class="form-group">
          <button class="btn btn-primary">Create</button>
        </div>
    </form>
  </div>
</template>

<script>
    export default {
        data(){
        return {
          post:{}
        }
    },
    methods: {
      addPost(){
        let uri = '/api/post/create';
        this.axios.post(uri, this.post).then((response) => {
          this.$router.push({name: 'posts'});
        });
      }
    }
  }
</script>
