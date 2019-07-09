<template>
  <v-container
    fill-height
    fluid
  >
    <v-layout
      justify-center
      align-center
    >
      <v-flex xs12>
        <material-card
          color="general"
          title="Projects"  
        >
        <v-card-text>
              <v-flex
          md12
        >
          <material-card
            color="green"
            title="Table"
            
          >
            <v-data-table
              :headers="headers"
              :items="items.slice(0, 10)"
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
                slot="items"
                slot-scope="{ item }"
              >
                <td>{{ item.title }}</td>
                <td>{{ item.comments}}</td>
      
              </template>
            </v-data-table>
          </material-card>
        </v-flex>
      
      </v-card-text>
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
                    sortable: false,
                    text: 'Title',
                    value: 'name'
                },
                {
                    sortable: false,
                    text: 'Comment',
                    value: 'country'
                }

            ],
            items: []

        }),
        mounted() {
            axios.get("http://127.0.0.1:5000/adminviewprojects").then(response => {
                this.items = response.data
            })
        }
    }

</script>

<style lang="scss">
  .tim-note {
    bottom: 10px;
    color: #c0c1c2;
    display: block;
    font-weight: 400;
    font-size: 13px;
    line-height: 13px;
    left: 0;
    margin-left: 20px;
    width: 260px;
  }
</style>
