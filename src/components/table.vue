<template>
  <v-container>
    <v-simple-table>
      <template v-slot:default>
        <thead>
          <tr class="text-center">
            <th>Id</th>
            <th>titr</th>
            <th>Contenue</th>
          </tr>
        </thead>
        <tbody>
           <tr v-for="post in posts" :key="post.id ">
            <td>{{ post.id }}</td>
            <td>{{ post.title }}</td>
            <td>{{ post.body }}</td>
          </tr> 
        </tbody>
      </template>
    </v-simple-table>
    <div class="text-center mt-4">
      <v-pagination v-model="pagination.currentpage" 
                     :total-visible="5"
                    :length="pagination.totalpages"
                    @input="getvalue"
                    circle>
              
      </v-pagination>
    </div>
  </v-container>
</template>

<script>
import axios from 'axios'
export default {
  name: "TablE",
  data() {
    return {
      pagination:{
        currentpage: 1,
        totalpages:10,
      },
      posts:[],
    };
  },
  mounted(){
    // this.getfilmsaxios()
    this.getpostsaxios()
  },
  methods:{
    getvalue()
    {
      this.getpostsaxios()
    },
     getpostsaxios()
    {
      axios.get('https://jsonplaceholder.typicode.com/posts?_page='+ this.pagination.currentpage)
        .then((response) => {
          console.log(response.data)
          this.posts=response.data
          
        })
        .catch((error =>
        {
          console.log(error)
        }))
    },

    getpostsasync()
    {
      fetch('https://jsonplaceholder.typicode.com/posts/?_start=0&_limit=10')
      .then(async response =>{
        const link = response.get
        const json = await response.json()
        console.log(link, json)
        this.posts= json
      })
    }
  }
};
</script>
