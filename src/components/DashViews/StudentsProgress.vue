<template>
  <v-jumbotron>
    <v-container fill-height>
      <v-layout align-center>
        <v-flex>
            <v-spacer></v-spacer>
          <v-text-field
            v-model="search"
            append-icon="search"
            label="Search"
            single-line
            hide-details>
            </v-text-field><br>
            
            <v-flex xs12 sm6 offset-sm3>
            <v-card v-for="item in items" :key="item.date">
                 <v-card-text class="px-12">
                     <h4 class="font-weight-bold">Student</h4>
                    <div>
                        {{item.reg_no}}
                    </div>
                    <h4 class="font-weight-bold">Progress Report</h4>
                    <div>
                        {{item.files}}
                    </div>
                     <h4 class="font-weight-bold">Submit date</h4>
                      <div>
                        {{item.date}}
                    </div>
                    <v-divider class="my-3"></v-divider>
                </v-card-text>
            </v-card>
            </v-flex>
         
        </v-flex>
      </v-layout>
    </v-container>
  </v-jumbotron>
</template>

<script>
export default {
    data(){
        return{

            items:[
            {
                reg_no:'1234',
                files:'xxxxx',
                date:'12/12/12'
            }
        ]

        }
        
    }
}
</script>