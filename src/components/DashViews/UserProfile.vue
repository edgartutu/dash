<template>
  <v-container
    fill-height
    fluid
    grid-list-xl
  >
    >
    <v-layout
      justify-center
      wrap
      
    >
      <v-flex 
      md12>
        <materila-card
         color="yellow" >

         <v-card>
          
            <v-expansion-panel popout>
              <v-expansion-panel-content v-for="(proposal,index) in proposals" :key="proposal.reg_no">
                <template v-slot:header>
               <div>{{proposal.title}}</div>
            </template>
                <v-card-text class="px-16">
                    <h4 class="font-weight-bold">Students</h4>
                    <div>{{proposal.reg_no}}</div>
                    <h4 class="font-weight-bold">Title</h4>
                    <div>{{proposal.title}}</div>
                    <h4 class="font-weight-bold">Problem statment</h4>
                    <div>{{proposal.problem_statment}}</div>
                    <h4 class="font-weight-bold">Abstract</h4>
                    <div>{{proposal.abstract}}</div>
                    <h4 class="font-weight-bold">File</h4>
                    <div>{{proposal.file}}</div>
                    <div>{{proposal.status}}</div>
                    <v-text-field label="Supervisor" placeholder="Supervisor" v-model="supervisor"></v-text-field>
                    <v-text-field label="Email" placeholder="Emain" v-model="email"></v-text-field>
                    <v-text-field label="Comment" placeholder="Comment" v-model="comment"></v-text-field>
                    <v-btn class="green" @click="approve(index)">Approve</v-btn><v-spacer></v-spacer>
                    <v-btn class="red" @click="rejected(index)">Reject</v-btn>
                </v-card-text>
          
              </v-expansion-panel-content>
            </v-expansion-panel>
      
      </v-card>
       
        </materila-card>
      </v-flex>
      <v-flex
        xs12
        md4
      >
        
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
import axios from 'axios'
    export default {
        data() {
            return {
                proposals: {},
                supervisor: "",
                email: "",
                comment: "",

            }
        },
        mounted() {
            axios.get("http://127.0.0.1:5000/pendingproposal").then(response => {
                this.proposals = response.data
            })
        },
        methods: {
            approve(index) {
                axios.post("http://127.0.0.1:5000/approve", {
                    "reg_no": this.proposals[index].reg_no, "supervisor": this.supervisor, "email": this.email,
                    "comment": this.comment, "status": "Approved"
                })
            },
            rejected(index) {
                axios.post("http://127.0.0.1:5000/approve", {
                    "reg_no": this.proposals[index].reg_no,
                    "comment": this.comment, "status": "Rejected"
                })
            }
        }
     
    
   
}
</script>
