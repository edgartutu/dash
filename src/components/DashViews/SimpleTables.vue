<template>
  <v-container
    fill-height
    fluid
    grid-list-xl
  >
    <v-layout
      justify-center
      wrap
    >

      <v-flex
        md12
      >

        <material-card 
        >
          <v-btn
            @click="exportdb()"
            color="red"
            dark
            class="mb-2" >Export To Excel</v-btn>
            <v-layout column style="height: 50vh">       
            <v-flex md12 style="overflow: auto">   
          <v-data-table
            :headers="headers"
            :items="items"
            hide-actions
          >
            <template
              slot="headerCell"
              slot-scope="{ header }"
            >
              <span
                class="subheading font-weight-light text-general text--darken-3"
                v-text="header.text"
              />
            </template>
            <template slot="items"
                      slot-scope="{ item,index }">
                <td>{{ item.id }}</td>
                <td>{{ item.reg_no }}</td>
                <td>{{ item.title }}</td>
                <td>{{ item.problem_statement }}</td>
                <td>{{ item.methodology }}</td>
                <td>{{ item.proposal_uploadfile }}</td>
                <td>{{ item.status }}</td>
                <v-btn class="flat green" @click="download(index)">Download</v-btn>
            </template>
          </v-data-table>
          </v-flex>
          </v-layout>
        </material-card>
      </v-flex>

     
    </v-layout>
  </v-container>
</template>

<script>
import axios from 'axios'
export default {
  data: () => ({
      headers: [
      {
        sortable: true,
        text: 'Project Id',
        value: 'id'
      },
      {
        sortable: true,
        text: 'Reg No',
        value: 'reg_no'
      },
      {
        sortable: true,
        text: 'Title',
        value: 'title'
      },
      {
        sortable: false,
        text: 'Problem Statment',
        value: 'problem_statment'
      },
      {
        sortable: false,
        text: 'Methodology',
        value: 'methodology',
      },
      {
        sortable: false,
        text: 'File',
        value: 'file',
      },
      {
        sortable: false,
        text: 'Status',
        value: 'status',
      },

        ],
        items: [],
        reg_no: '',

        }),
        mounted() {
          
            axios.get("http://127.0.0.1:5000/approved").then(response => {
                this.items = response.data
            })
          
        },
        methods: {
            exportdb() {
                axios.post("http://127.0.0.1:5000/excelexport").then(response => {
                    console.log(response)
                })
            },
            download(index) {
                this.reg_no = this.items[index].reg_no
                axios.post("http://127.0.0.1:5000/pendingfiles", {'reg_no':this.reg_no}).then(response => {
                    console.log(this.reg_no)
                })
            }
        }
}
</script>
