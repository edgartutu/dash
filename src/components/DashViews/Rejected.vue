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
        title="Rejected Projects"
        color="red"
        >
          <v-btn
            color="black"
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
              <td>{{ item.problem_statment }}</td>
               <td>{{ item.abstract }}</td>
                <td>{{ item.file }}</td>
                 <td>{{ item.status }}</td>
            </template>
          </v-data-table>
        </material-card>
      </v-flex>

     
    </v-layout>
  </v-container>
</template>

<script>
export default {
  data: () => ({
    headers: [
      {
        sortable: true,
        text: 'Reg_no',
        value: 'reg_no'
      },
      {
        sortable: true,
        text: 'Title',
        value: 'title'
      },
      {
        sortable: false,
        text: 'Problem_statment',
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
    items: [
      {
        reg_no: '14/U/2425/PSA ',
        title: 'Energy Saving System for Corporate Computers and Lighting System By Using PIR Sensor ',
        problem_statment: 'what is wron with the government',
        abstract: 'think sbout it',
       file: 'coming....',
       status: 'Rejected'
      },
      {
        reg_no: '16/U/32435/EVE',
        title: 'Automatic Intelligent Streetlight Controlling System Based on High Power LED',
        problem_statment: 'PROBLEMS',
        abstract: 'too many problems',
       file: '.........',
       status: 'Rejected'
      }
    ]
  })
}
</script>
