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
            color="red"
            dark
            class="mb-2" >Edit</v-btn>
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
            <template
              slot="items"
              slot-scope="{ item }"
            >
             <td>{{ item.reg_no }}</td>
              <td>{{ item.title }}</td>
              <td>{{ item.problem_statement }}</td>
               <td>{{ item.abstract }}</td>
                <td>{{ item.proposal_uploadfile }}</td>
                 <td>{{ item.status }}</td>
            </template>
          </v-data-table>
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
        text: 'Abstract',
        value: 'abstract',
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
        items: []

        }),
        mounted() {
            axios.get("http://127.0.0.1:5000/pendingproposal").then(response => {
                this.items = response.data
            })
        }
}
</script>
