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
          color="green"
          title="Registered Students"
        
        >
          <v-data-table
            :headers="headers"
            :itemz="itemz"
            hide-actions
          >
            <template
              slot="headerCell"
              slot-scope="{ header }"
            >
              <span
                class="subheading font-weight-light text-success text--darken-3"
                v-text="header.text"
              />
            </template>
            <template
              slot="itemz"
              slot-scope="{ itemm }"
            >
              <td>{{ itemm.reg_no }}</td>
              <td>{{ itemm.student1 }}</td>
              <td>{{ itemm.contact1 }}</td>
               <td>{{ itemm.reg_no1 }}</td>
                <td>{{ itemm.student2 }}</td>
                 <td>{{ itemm.contact2 }}</td>
          
            </template>
          </v-data-table>
        </material-card>
      </v-flex>
      <v-flex
        md12
      >
        <material-card
          color="green"
          flat
          full-width
          title="Registered Lecturers"
         
        >
          <v-data-table
            :headers="header"
            :items="items.slice(0, 7)"
            hide-actions
          >
            <template
              slot="headerCell"
              slot-scope="{ header }"
            >
              <span
                class="subheading font-weight-light text--darken-3"
                v-text="header.text"
              />
            </template>
            <template
              slot="items"
              slot-scope="{ item }"
            >
              <td>{{ item.name }}</td>
              <td>{{ item.email }}</td>
              <td>{{ item.contact }}</td>
              
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
        sortable: false,
        text: 'Reg_no',
        value: 'reg_no'
      },
      {
        sortable: false,
        text: 'Student1',
        value: 'student1'
      },
      {
        sortable: false,
        text: 'Contact',
        value: 'contact1'
      },
      {
        sortable: false,
        text: 'Reg_no1',
        value: 'reg_no1',
        
      },
      {
        sortable: false,
        text: 'Student2',
        value: 'student2',
       
      },
      {
        sortable: false,
        text: 'Contact2',
        value: 'contact2',
       
      },
      
    ],
    items: [
      {
        name: 'Dakota Rice',
        email: 'Niger',
        contact: 'Oud-Tunrhout',
        
      }
    ],
     itemz: [
      {
        reg_no: 'Dakota Rice',
        student1: 'Niger',
        contact1: 'Oud-Tunrhout',
        reg_no1: '$35,738',
        student2: 'Oud-Tunrhout',
        contact2: '$35,738'
      }
    ],

    header: [
      {
        sortable: false,
        text: 'Name',
        value: 'name'
      },
      {
        sortable: false,
        text: 'Email',
        value: 'email'
      },
      {
        sortable: false,
        text: 'Contact',
        value: 'contact'
      }
      
    ],
  })
}
</script>
