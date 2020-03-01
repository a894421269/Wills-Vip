<template>
  <div class="add container">
    <h1 class="page-header">添加用户</h1>
    <form @submit="addCustomer">
      <div class="well">
        <div class="form-grounp">
         <br>
          <input type="text" placeholder="name" class="form-control" v-model="customer.name">
        </div>
        <div class="form-grounp">
         <br>
          <input type="text" placeholder="phone" class="form-control" v-model="customer.phone">
        </div>
        <div class="form-grounp">
         <br>
          <input type="text" placeholder="email" class="form-control" v-model="customer.email">
        </div>
        <div class="form-grounp">
         <br>
          <input type="text" placeholder="education" class="form-control" v-model="customer.education">
        </div>
        <div class="form-grounp">
         <br>
          <input type="text" placeholder="school" class="form-control" v-model="customer.school">
        </div>
        <div class="form-grounp">
         <br>
          <input type="text" placeholder="profession" class="form-control" v-model="customer.profession">
        </div>
        <div class="form-grounp">
         <br>
          <textarea placeholder=" your profile" class="form-control" cols="30" rows="10" v-model="customer.profile"></textarea>
        </div>
        <br>
        <button type="submit" class="btn btn-primary">添加</button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: 'add',
  data () {
    return {
     customer:{}
    }
  },
  methods:{
    addCustomer(e){
        console.log(this.customer)
        e.preventDefault()
        if(!this.customer.name || !this.customer.phone || !this.customer.email){
          alert("请添加相对应信息")
        }else{
          e.preventDefault();
          let newCustomer={
            name:this.customer.name,
            phone:this.customer.phone,
            email:this.customer.email,
            education:this.customer.education,
            school:this.customer.school,
            profession:this.customer.profession,
            profile:this.customer.profile
        }
        this.$http.post("http://localhost:3000/users",newCustomer).then((response)=>{
          this.$router.push({path:"/",query:{alert:"添加成功"}})
        })
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
