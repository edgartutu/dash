<template>

    <v-container  fill-height
    fluid
    grid-list-xl>
      <v-layout justify-center
      wrap>
      <v-flex  md8 >

         <material-card>
        
        
            
          <v-text-field
            v-model="search"
            append-icon="search"
            label="Search"
            single-line
            hide-details>
            </v-text-field><br>
             <v-spacer></v-spacer>
            <v-card v-for="item in items" :key="item.date">
                 <v-card-slide class="px-12">
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
                </v-card-slide>
            </v-card>
           
         </material-card>
      </v-flex>
      </v-layout>
    </v-container>
 
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
            },
            {
                reg_no:'9876',
                files:'xxxxx',
                date:'12/12/12'
            }
        ]

        }
        
    }
}
</script>