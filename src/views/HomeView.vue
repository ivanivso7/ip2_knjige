<template>
  <v-container>
        <v-row>
          <v-col
            v-for="book in books"
            :key="book.title"
            cols="4"
          >
            <v-card height="200">
              <h3>{{ book.title }}</h3>
              <h5>{{ book.author }}</h5>
              
            </v-card>
          </v-col>
        </v-row>
      </v-container>
</template>

<script>
  
  //import HelloWorld from '@/components/HelloWorld.vue';
  export default {
    name: 'HomeView',

     data(){
      return {
        test: 'Testna varijabla',
        books: []
      }
     },

     created(){
      this.getData()
     },

     methods: {
      getData(){
        let api = "https://api.nytimes.com/svc/books/v3/lists/overview.json"
        this.axios.get(api, {
          params: {
            'api-key': '25VAonJPnYzWwJNTNC0LE7wddvtBWjY0Ae6nUgOTQnyHYQDT'
          }
        }).then((response) => {
          console.log(response.data)
          this.books = response.data.results.lists[0].books
        })
      }
     }
  }
</script>
