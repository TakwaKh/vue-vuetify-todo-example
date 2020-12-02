<template>
  <div class="projects">
    <h1 class="text-h6 grey--text">Team</h1>
    <v-container>
      <v-row wrap>
        <v-col cols="12" md="4" v-for="person in team" :key="person.index">
          <v-card flat class="py-5 text-center"> 
              <v-responsive >
                <v-avatar size="100">
                <v-img
                  :src="person.img" 
                  :alt="person.name"
                  
                ></v-img>
              </v-avatar>
              </v-responsive>
              <v-card-text>
                <div class="text-subheading">{{person.name}}</div>
                <div class="grey--text">{{person.role}}</div>
              </v-card-text>
              <v-card-actions>
                <v-btn depressed small class="grey--text">
                  <v-icon left>mdi-message-text</v-icon>
                  <span>Message</span>
                </v-btn>
              </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>
<script>

export default {
  name: 'Team',
  components: {
    
  },
  
  data() {
    return {
      team: [
        { name: 'The Net Ninja', role: 'Web developer', img: 'https://images.unsplash.com/photo-1506085452766-c330853bea50?ixlib=rb-0.3.5&q=80&fm=jpg&crop=faces&fit=crop&h=200&w=200&s=3e378252a934e660f231666b51bd269a' },
        { name: 'Ryu', role: 'Graphic designer', img: 'https://uifaces.co/our-content/donated/KtCFjlD4.jpg' },
        { name: 'Chun Li', role: 'Web developer', img: 'https://randomuser.me/api/portraits/men/46.jpg' },
        { name: 'Gouken', role: 'Social media maverick', img: 'https://uifaces.co/our-content/donated/bUkmHPKs.jpg' },
        { name: 'Yoshi', role: 'Sales guru', img: 'https://images.unsplash.com/photo-1520813792240-56fc4a3765a7?ixlib=rb-1.2.1&q=80&fm=jpg&crop=faces&fit=crop&h=200&w=200&ixid=eyJhcHBfaWQiOjE3Nzg0fQ'}
      ]
    }
  },
  methods: {

     getData(){
      fetch('https://jsonplaceholder.typicode.com/todos/1')
  .then(response => response.json())
  .then(json => console.log(json))

    }

    
    

  }
}
</script>