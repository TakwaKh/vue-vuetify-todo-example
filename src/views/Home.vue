<template>
  <div class="home">
    <h1 class="text-h6 grey--text">Dashboard </h1>
    
    <v-container>
      <v-row>
        <v-col>
          <v-tooltip top>
      <template v-slot:activator="{ on, attrs }">
       
        <v-btn rounded depressed class="grey--text" @click="sortBy('title')" v-bind="attrs" v-on="on">  
            <v-icon left>mdi-folder</v-icon>
            <span >By project name</span>
          </v-btn>
      </template>
      <span>Sort by project name</span>
    </v-tooltip>
         <v-tooltip top>
      <template v-slot:activator="{ on, attrs }">
       
         <v-btn rounded depressed class="grey--text" @click="sortBy('person')" v-bind="attrs" v-on="on">  
            <v-icon left>mdi-account</v-icon>
            <span >By person</span>
          </v-btn>
      </template>
      <span>Sort by person </span>
    </v-tooltip>
          
        </v-col>
       
      </v-row>
      <v-card flat class="mb-2" v-for="project in projects" :key="project.index"> 
        <v-row :class="`pa-3 mx-0 project ${project.status}`">
          <v-col cols="12" md="6">
            <h6 class="text-caption grey--text">project Title</h6>
            <div class=""> {{project.title}}</div>
          </v-col>
           <v-col cols="4" md="2">
             <h6 class="text-caption grey--text">Person</h6>
            <div class=""> {{project.person}}</div>
          </v-col>
           <v-col cols="4" md="2">
             <h6 class="text-caption grey--text">Due By</h6>
            <div class=""> {{project.due}}</div>
          </v-col>
           <v-col cols="4" md="2">
             <!-- <h6 class="text-caption grey--text">Status</h6> -->
             <div class="text-right">
               <v-chip :class="`text-caption white--text my-2 ${project.status}` ">{{project.status}}</v-chip>
             </div>
             
            
          </v-col>
        </v-row>
      </v-card>
    </v-container>
  </div>
</template>

<script>
// @ is an alias to /src


export default {
  name: 'Home',
  components: {
    
  },
  data() {
    return {
      projects: [
        { title: 'Design a new website', person: 'The Net Ninja', due: '1st Jan 2019', status: 'ongoing', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'},
        { title: 'Code up the homepage', person: 'Chun Li', due: '10th Jan 2019', status: 'complete', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'},
        { title: 'Design video thumbnails', person: 'Ryu', due: '20th Dec 2018', status: 'complete', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'},
        { title: 'Create a community forum', person: 'Gouken', due: '20th Oct 2018', status: 'overdue', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'},
      ]
    }
  },
  methods: {
    sortBy(prop){
      this.projects.sort((a,b) => a[prop] < b[prop] ? -1:1)
    }
  }
}
</script>
<style>
.project.complete {
  border-left: 5px solid #3cd1c2;
}
.project.ongoing {
  border-left: 5px solid orange;
}
.project.overdue {
  border-left: 5px solid tomato;
}
.theme--light.v-chip:not(.v-chip--active).complete {
  background:  #3cd1c2;
}
.theme--light.v-chip:not(.v-chip--active).ongoing {
  background:orange;
}
.theme--light.v-chip:not(.v-chip--active).overdue {
  background: tomato;
}
</style>