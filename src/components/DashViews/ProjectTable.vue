
<template>
  <v-data-table class="fb-table-elem"
      :headers="headers"
      :items="items"
      hide-actions
      item-key="name"
      expand >
        <template slot="items" slot-scope="props" >
         
           
          <tr @click="props.expanded = !props.expanded">
            <td class="datatable-cell-wrapper"><div>{{ props.item.reg_no }}</div></td>
            <td class="datatable-cell-wrapper"><div>{{ props.item.title }}</div></td>
               <td class="datatable-cell-wrapper"><div>{{ props.item.status}}</div></td>
            <td class="datatable-cell-wrapper"><div>{{ props.item.proposal_uploadfile }}</div></td>
            <td class="datatable-cell-wrapper">{{ props.item.student_pair }}</td>
            <td class="datatable-cell-wrapper">{{ props.item.supervisor }}</td>
            <td class="datatable-cell-wrapper">{{ props.item.email }}</td>
            
             <v-dialog
      v-model="dialog"
      width="500"
    >
      <template v-slot:activator="{ on }">
        <v-btn
          small 
          class="pink"
          v-on="on"
        >
          review
        </v-btn>
      </template>

      <v-card>
        <v-card-title
          class="headline grey lighten-2"
          primary-title
        >
         Concept Details
        </v-card-title>

        <v-card-text>
         <v-card >
                <v-card-text class="px-16">
                    <h4 class="font-weight-bold">Students</h4>
                    <div>{{props.item.reg_no}}</div>
                    <h4 class="font-weight-bold">Title</h4>
                    <div>{{props.item.title}}</div>
                    <h4 class="font-weight-bold">Problem statment</h4>
                    <div>{{props.item.problem_statment}}</div>
                    <h4 class="font-weight-bold">Methodology</h4>
                    <div>{{props.item.abstract}}</div>
                    <h4 class="font-weight-bold">File</h4>
                    <div>{{props.item.file}}</div>
                    <div>{{props.item.status}}</div>
                     <v-text-field label="Comment" placeholder="Comment" v-model="comment"></v-text-field>
                </v-card-text>
              </v-card>
        </v-card-text>
        <v-divider></v-divider>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-dialog
           v-model="dialog"
           width="200"
          >
      <template v-slot:activator="{ on }">
        <v-btn
         class="green"       
          v-on="on"
          @click="approve"
        >
          Approve
        </v-btn>
      </template>

      <v-card>
        
        <v-card-text>
        <h4 style="color:green">Successfull</h4> 
        </v-card-text>

       

        <v-card-actions>
          <v-spacer></v-spacer>
         
          <v-spacer></v-spacer>
          
      
        </v-card-actions>
      </v-card>
    </v-dialog>
     <v-spacer></v-spacer>
     <v-dialog
           v-model="dialog"
           width="200"
          >
      <template v-slot:activator="{ on }">
        <v-btn
         class="red"       
          v-on="on"
          @click="rejected"
        >
          Reject
        </v-btn>
      </template>

      <v-card>
        
        <v-card-text>
        
         <h4 style="color:red"> Rejected!</h4>
         
        </v-card-text>

        

        <v-card-actions>
          <v-spacer></v-spacer>
         
        </v-card-actions>
      </v-card>
    </v-dialog>
          
         
        </v-card-actions>
      </v-card>
    </v-dialog>
            
          </tr>
          
        </template>
        <template slot="expand" >
          <v-card flat>
            <v-card flat="flat" color="grey lighten-4">
              <v-container fluid="fluid" grid-list-xl="grid-list-xl">
                <v-layout row="row" wrap="wrap">
                  <v-flex >
                      <user/>
                    
                  </v-flex>
                </v-layout>
              </v-container>
            </v-card>
          </v-card>
        </template>
      </v-data-table>
</template>
<script>
import axios from 'axios'
import user from './UserProfile.vue'
  export default {
      components:{
          user

      },
    
    
    data(){
      return {

                proposals: {},
                supervisor: "",
                email: "",
                comment: "",
               

                

    
        
      headers: [
       
         { text: 'Reg_no', value: 'reg_no' },
        { text: 'Title', value: 'title' },
        { text: 'Student', value: 'student_pair' }, 
        { text: 'Supervisor', value: 'supervisor' }, 
        { text: 'file', value: 'proposal_uploadfile' },
       { text: 'Status', value: 'status' },
    
      
      ],
      items: [

       
      ]
      
    }
    return{
      dialog:false
    }
    },
  
  mounted() {
            axios.get("http://127.0.0.1:5000/proposals").then(response => {
                this.items = response.data
            })
        },
  
  methods: {
  generateRandomNumber () {
    return
  }
},
  created() {
            axios.get("http://127.0.0.1:5000/pendingproposal").then(response => {
                this.proposals = response.data
            })
        },
        methods: {
            approve() {
                axios.post("http://127.0.0.1:5000/approve", {
                    "reg_no": 1236, "supervisor": this.supervisor, "email": this.email,
                    "comment": this.comment, "status": "Approved"
                })
            },
            rejected() {
                axios.post("http://127.0.0.1:5000/approve", {
                    "reg_no": 1234,
                    "comment": this.comment, "status": "Rejected"
                }).then(dialog)
            }
        }
     
  }
</script>
Expandable Table