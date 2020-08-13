<template>
<!--content -->
    <div class="container">
      <div class="row">
        <div class="col-md-4"></div>
        <div class="col-md-4 col-xs-12">
          <h3 style="margin-top: 50px"> Login Form </h3>
          
            <div class="form-group">
              <label for="exampleInputEmail1">Username</label>
              <input type="username" class="form-control" placeholder="Username" v-model="username" required>
            </div>
            <div class="form-group">
              <label for="exampleInputPassword1">Password</label>
              <input type="password" class="form-control" placeholder="Password" v-model="password" required>
            </div>
            <button class="btn btn-primary" @click="Auth">Login</button>
          
        </div>
      </div>
      <p>{{employees}}</p>
    </div>
</template>

<script>
export default {
  name: 'API',
  data(){
    return {
    url_base: 'https://dummy-api.cm.edu/employees',
    username: '',
    password: '',
    employees: {}
    }
  },
  methods:{

    Auth(){
        const headers = new Headers();
        headers.append(
          "Authorization",
          "Basic "  + btoa(this.username+":"+this.password) //Convert.ToBase64String(Encoding.Default.GetBytes(this.username+":"+this.password))
        );
        const request = new Request(
          this.url_base,
          {
            method: "GET",
            headers,
            mode: "cors",
            cache: "default"
          }
        );
        fetch(request)
        .then(res => {
          return res.json();
        }).then(this.setResults);
    },
    setResults (results) {
      this.employees = results;
    },

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
