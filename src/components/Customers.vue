<template>
  <div class="customers container">
    
    <Alert v-if="alert" :message="alert"></Alert>
    <h1 class="page-header">会员信息</h1>
    <table class="table table-striped">
      <thead>
        <tr>
          <th>姓名</th>
          <th>邮箱</th>
          <th>电话</th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="customer in customers">
          <th>{{customer.name}}</th>
          <th>{{customer.eamil}}</th>
          <th>{{customer.phone}}</th>
          <th></th>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'customers',
  data () {
    return {
     customers:[],
     alert:""
    }
  },
  methods:{
    fetchCustomer(){
      this.$http.get("http://localhost:3000/users").then(function(response){
        console.log(response.body)
        this.customers=response.body
      })
    }
  },
  created(){
    this.fetchCustomer()
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
