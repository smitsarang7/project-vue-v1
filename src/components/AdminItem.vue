<template>
  <div>
    <mdb-tbl responsiveSm>
      {{directory}}
      
    </mdb-tbl>

    <mdb-tbl responsiveMd>
      <table class="table table-striped mt-4">
      <thead>
      <tr>
        <th scope="col">name</th>
        <th scope="col">title</th>
        <th scope="col">city</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="input in directory.edges" :key="input.id">
        <td>{{ input.node.itemName }}</td>
        <td>{{ input.node.itemPrice }}</td>
        <td>{{ input.node.itemCategory.categoryName }}</td>
      </tr>
      </tbody>
    </table>    
    </mdb-tbl>

    <mdb-tbl responsiveLg>
      ...
    </mdb-tbl>

    <mdb-tbl responsiveXl>
      ...
    </mdb-tbl>
  </div>
</template>
<script>
 import { mdbTbl } from 'mdbvue';
 import axios from 'axios';
 export default {
    name: 'AdminItem',
    components: {
     mdbTbl
    },
    data(){
      return {
          city:'',
          directory:[]
      }
    },
    async mounted () {
      try {
          var result = await axios({
            method: 'POST',
            url: 'http://127.0.0.1:8000/graphql/',
            data: {
            query: `
            {
                allItems{
                    edges{
                        node{
                            id,
                            itemName,
                            itemPrice,
                            itemCategory{
                            categoryName
                            }
                        }
                    }
                }
            }
            `
            }
        })
        this.directory = result.data.data.allItems
        } catch (error) {
          console.log(error)
      }
      }
    }
  </script>

<style scoped>
</style>