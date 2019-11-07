<template>
  <div class="detail container">
    <router-link to="/" class="btn btn-default">返回</router-link>
   <h1 class="page-header">{{customer.name}}
    <span class="pull-right">
      <router-link class="btn btn-primary" :to="'/edit/'+customer.id">编辑</router-link>
      <button class="btn btn-danger" @click="deleteCustomer(customer.id)">
        删除
      </button>
    </span>
   </h1>
    <ul class="list-group">
      <li class="list-group-item"><span class="glyphicon glyphicon-asterisk"> {{customer.phone}}</span></li>
      <li class="list-group-item"><span class="glyphicon glyphicon-plus"> {{customer.email}}</span></li>
    </ul>
    <ul class="list-group">
      <li class="list-group-item"><span class="glyphicon glyphicon-asterisk"> {{customer.education}}</span></li>
      <li class="list-group-item"><span class="glyphicon glyphicon-plus"> {{customer.graduationschool}}</span></li>
    </ul>
    <ul class="list-group">
      <li class="list-group-item"><span class="glyphicon glyphicon-asterisk"> {{customer.profession}}</span></li>
      <li class="list-group-item"><span class="glyphicon glyphicon-plus"> {{customer.profile}}</span></li>
    </ul>
  </div>
</template>

<script>
    export default {
        name: 'detail',
        data () {
            return {
                customer:""
            }
        },
        created(){
            //一进页面得到点击的id值
            this.fetchCustomers(this.$route.params.id)
        },
        methods:{
            fetchCustomers(id){
                this.$http.get("http://localhost:3000/users/"+id).then(response=> {
                    console.log(response)
                    if(response.status===200){
                        this.customer = response.body;
                    }

                })
            },
            deleteCustomer(id){
                console.log(id);
                this.$http.delete("http://localhost:3000/users/"+id).then(response=>{
                    this.$router.push({path:'/',query:{alert:'用户删除成功'}})
                })
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
