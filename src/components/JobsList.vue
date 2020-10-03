<template>
   <div class="container">
       <div class="row">
           <div class="col-12">
            <p class="display-3">Jobs List</p>
            </div>
       </div>
       <table border="1px">
           <tr>
               <td>Job Title</td>
               <td>Job Description</td>
            </tr>
             <tr v-for="item in list" v-bind:key="item.i"> 
               <td>{{item.title}}</td>
               <td>{{item.desc}}</td>
               <button @click='applyJobs(item.id)' class="btn btn-outline-info">Apply</button>
            </tr>
        </table>
    </div> 
</template>

<script>
import Vue from 'vue';
import axios from 'axios';
import VueAxios from 'vue-axios'
Vue.use(VueAxios, axios)
export default {
    name:"JobsList",
    data(){
        return {list: undefined,
                resp_message: undefined    
            }

    },
    methods:{
        applyJobs(jobId){
            Vue.axios.post('http://localhost:8000/jobs/'+jobId+'/apply')
            .then((resp)=>{
                this.resp_message = resp.data.response_message 
                // console.warn(resp)
            })
            return this.resp_message
        }
    },
    mounted()
    {
        Vue.axios.get('http://localhost:8000/jobs')
        .then((resp)=>{
            this.list = resp.data.data
            // console.warn(resp.data.data)
        })
    }
}
</script>

<style>
    .btn{
       background-color: blueviolet 
    }
</style>