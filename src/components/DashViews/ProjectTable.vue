
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
            <td class="datatable-cell-wrapper"><div>{{ props.item.problem_statement }}</div></td>
            <td class="datatable-cell-wrapper">{{ props.item.abstract }}</td>
               <td class="datatable-cell-wrapper">{{ props.item.status}}</td>
            <td class="datatable-cell-wrapper">{{ props.item.proposal_uploadfile }}</td>
            <td class="datatable-cell-wrapper">{{ props.item.student_pair }}</td>
          
            <td class="datatable-cell-wrapper">{{ props.item.supervisor }}</td>
            <td class="datatable-cell-wrapper">{{ props.item.email }}</td>
             <td class="datatable-cell-wrapper">{{ props.item.comment }}</td>
              
             <td class="datatable-cell-wrapper"></td>
            
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
    
        
      headers: [
       
         { text: 'Reg_no', value: 'reg_no' },
        { text: 'Title', value: 'title' },
        { text: 'Problem_statement', value: 'problem_statement' },
        { text: 'Abstract', value: 'abstract' },
        { text: 'Status', value: 'status' },
        { text: 'file', value: 'proposal_uploadfile' },
        { text: 'Supervisor', value: 'supervisor' },
        { text: 'Student', value: 'student_pair' },
        { text: 'email', value: 'email' },
        { text: 'Comment', value: 'comment' },
      ],
      items: [

       
      ]

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
}
  }
</script>
Expandable Table