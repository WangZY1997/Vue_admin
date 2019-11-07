<template>
  <div class="customers container">
    <Alert v-if="alert" :message="alert"></Alert>
  <h1 class="page-header">用户管理系统</h1>
    <input type="text" class="form-control" placeholder="搜索" v-model="filterInput">
    <br>
    <table class="table table-striped">
      <thead>
      <tr>
        <th>姓名</th>
        <th>电话</th>
        <th>邮箱</th>
        <th></th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="(customer,index) in fliterBy(customers,filterInput)" :key="index">
        <td>{{customer.name}}</td>
        <td>{{customer.phone}}</td>
        <td>{{customer.email}}</td>
        <td><router-link :to="'/customer/'+customer.id" class="btn btn-default">详情</router-link></td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
  import Alert from "./Alert";

    export default {
        name: 'customers',
        data () {
            return {
            customers:[],
                alert:"",
                filterInput:''

            }
        },
        methods:{
            fetchCustomers(){
                    this.$http.get("http://localhost:3000/users").then(function (response) {
                        // console.log(response)
                        if(response .status===200){
                            this.customers = response.body;
                            // console.log(this.customers)
                        }

                    })
            },
            fliterBy(customers,value){
              return customers.filter(function (customer) {
                  return customer.name.match(value)
              })
            }
        },
        created() {
            if(this.$route.query.alert){
                this.alert = this.$route.query.alert
            }
            this.fetchCustomers();

        },
        // updated() {
        //     this.fetchCustomers();
        // },
        components:{
            Alert
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
