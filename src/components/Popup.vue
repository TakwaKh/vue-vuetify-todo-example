<template>
  <div class="popup">
  <v-dialog
      v-model="dialog"
      width="500"
    >
      <template v-slot:activator="{ on, attrs }">
       
        <v-btn depressed color="indigo" dark  v-bind="attrs" v-on="on" >
                  Add New Project
        </v-btn>
      </template>

      <v-card>
        <v-card-title class="" >
          Add new Project
        </v-card-title>
         <v-form v-model="valid" ref="form">
        <v-card-text>
            <v-container>
                <v-row>
                    <v-col>
                    <v-text-field
                        v-model="projectTitle"
                        :rules="inputRules"
                        :counter="200"
                        label="Project Title"
                        required
                        color="indigo"
                        filled
                        prepend-inner-icon="mdi-folder"
                    ></v-text-field>
                    </v-col>
                </v-row>
                <v-row>
                    <v-col>
                        <v-textarea
                            filled
                            name="input-7-4"
                            :rules="inputRules"
                            label="Project Information"
                            value=""
                            color="indigo"
                            v-model="projectInfo"
                            prepend-inner-icon="mdi-lead-pencil"
                            ></v-textarea>
                    </v-col>
                </v-row>
                <v-row>
                    <v-col>
                        <v-menu
                            ref="menu"
                            v-model="menu"
                            :close-on-content-click="false"
                            :return-value.sync="date"
                            transition="scale-transition"
                            offset-y
                            min-width="290px"
                        >
                            <template v-slot:activator="{ on, attrs }">
                            <v-text-field
                                v-model="date"
                                label="Picker in menu"
                                prepend-inner-icon="mdi-calendar"
                                readonly
                                v-bind="attrs"
                                v-on="on"
                                filled
                                
                                
                            ></v-text-field>
                            </template>
                            <v-date-picker
                            v-model="date"
                            no-title
                            scrollable
                            >
                            <v-spacer></v-spacer>
                            <v-btn
                                text
                                color="primary"
                                @click="menu = false"
                            >
                                Cancel
                            </v-btn>
                            <v-btn
                                text
                                color="primary"
                                @click="$refs.menu.save(date)"
                            >
                                OK
                            </v-btn>
                            </v-date-picker>
                        </v-menu>
                    </v-col>
                </v-row> 
            </v-container>
        </v-card-text>
        <v-card-actions>
            <v-container>
                <v-btn class="success" depressed @click="submit" > Submit</v-btn>
            </v-container>
        </v-card-actions>
        </v-form>
      </v-card>
    </v-dialog>
  </div>
</template>
<script>

import format from 'date-fns/format'

export default {
  name: 'Popup',
  components: {
    
  },
  data() {
      return {
        date: new Date().toISOString().substr(0, 10),
        menu: false,
        modal: false,
        projectTitle:'',
        projectInfo:'',
        dialog: false,
        valid: false,
        inputRules: [
              v => v.length >= 3 || 'minimum length is 3 charachters'
          ]
      }
  },
  methods: {
      submit(){
          if(this.$refs.form.validate()){
               console.log(this.projectTitle, this.projectInfo , this.date)
          }
         
      }
  },
  computed: {
    formattedDate() {
        return this.date ? format(this.date, 'Do MMM YYYY') : ''
    }

  }
}
</script>
