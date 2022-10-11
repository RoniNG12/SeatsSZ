<template>
  <v-app :style="{'background-color':'#FFEBEE'}">
   
    <div class="d-flex justify-center mt-5">
     
       <v-tooltip left  >
      <template v-slot:activator="{ on, attrs }">
        <v-icon
          color="red"
          large
          dark
          v-bind="attrs"
          v-on="on"
        >
       mdi-help-circle-outline
        </v-icon>
      </template>
      <p dir="rtl">סדרו את אנשי הסגל משמאל לימין (מהשולחן התחתון השמאלי לשולחן התחתון הימני). 
        </p>
        <p dir="rtl"> אם אחד המיקומים יהיה נכון אחרי שתלחצו על הכפתור הוא יצבע בירוק.</p>
    </v-tooltip>
    <v-img  contain max-width="400" max-height="150" 
       src="./assets/e95080b773ddc4ebe3d0b0ed254ffc26.png"/>
     </div>

     
     <SegelChips class="mt-10" :tags.sync="this.tags"  v-on:update:tags="tags = $event" >
      <div class="mr-2">
            <v-btn
              color="error"
              light
              class=" elevation-15"
              x-large
              @click="compareLists"
            >
              SEAT!
            </v-btn>
            </div>

     </SegelChips>
      <v-container width="700" class="mt-5">
    <v-row class="flex-child">
      <v-col cols="4">
            <v-sheet
              class="d-flex elevation-15"
              color="red lighten-3"
              height="200"
            >
              <v-img v-show="ifShow" contain width="100" src='./assets/Almog.jpg'/>
            </v-sheet>
          </v-col>
      <v-col
        class="d-flex"
        cols="12"
        md="4"
      >
        <!-- <v-row > -->
          <v-col cols="6">
            <v-sheet
              class="d-flex  elevation-15"
              color="green lighten-3"
              height="100"
            >
            <v-img v-show="ifShow" contain width="100" src='./assets/Amit.jpg'/>
            </v-sheet>
          </v-col>

          <v-col cols="6">
            <v-sheet
              class="d-flex  elevation-15"
              color="yellow lighten-3"
              height="100"
            >
            <v-img v-show="ifShow" contain width="100" src='./assets/Shelly.jpg'/>
            </v-sheet>
          </v-col>
          <v-col cols="6">
            <v-sheet
              class="d-flex  elevation-15"
              color="teal lighten-3"
              height="100"
            >
            <v-img v-show="ifShow" contain width="100" src='./assets/Roni.jpg'/>
            </v-sheet>
          </v-col>
         
        <!-- </v-row> -->
      </v-col>
      
    </v-row>
    <v-row class="flex-child  justify-space-between">

      <v-col
        cols="6"
        md="2"
      >
        <v-sheet
          class="d-flex  elevation-15"
          color="indigo lighten-3"
          height="100"
        >
        <v-img v-show="ifShow" contain width="100" src='./assets/Bar.jpg'/>
        </v-sheet>
      </v-col>
</v-row>
<v-row class="flex-child  justify-space-between">
  <v-col
        cols="6"
        md="2"
      >
        <v-sheet
          class="d-flex  elevation-15"
          color="pink lighten-3"
          height="100"
        >
        <v-img v-show="ifShow" contain width="100" src='./assets/Eyal.jpg'/>
        </v-sheet>
      </v-col>

      <v-col
        cols="6"
        md="2"
      >
        <v-sheet
          class="d-flex  elevation-15"
          color="lime lighten-3"
          height="100"
        >
        <v-img v-show="ifShow" contain width="100" src='./assets/Shira.jpg'/>
        </v-sheet>
      </v-col>
</v-row>
<v-row class="flex-child justify-space-between">
  <v-col
        cols="6"
        md="2"
      >
        <v-sheet
          class="d-flex  elevation-15"
          color="blue lighten-3"
          height="100"
        >
        <v-img v-show="ifShow" contain width="100" src='./assets/Tamar.jpg'/>
        </v-sheet>
      </v-col>
    
      <v-col
        cols="6"
        md="2"
      >
        <v-sheet
          class="d-flex  elevation-15"
          color="purple lighten-3"
          height="100"
        >
        <v-img v-show="ifShow" contain width="100" src='./assets/Omer.jpg'/>
        </v-sheet>
      </v-col>
</v-row>

  </v-container>
  
  </v-app>
</template>

<script>
/* eslint-disable */

import SegelChips from "./components/SegelChips.vue";
// import Seats from "./components/Seats.vue";
export default( {
  components:{
    SegelChips,
    // Seats
  },
  data: () => ({
    ifShow: false,
    tags: [{
      name: 'Roni',
      status: 'wrong'
    },{
      name: 'Tamar',
      status: 'wrong'
    }, {
      name: 'Omer',
      status: 'wrong'
    }, {
      name: 'Bar',
      status: 'wrong'
    },
    {
      name: 'Amit',
      status: 'wrong'
    },
    {
      name: 'Shira',
      status: 'wrong'
    },
    {
      name: 'Shelly',
      status: 'wrong'
    },
    {
      name: 'Eyal',
      status: 'wrong'
    }
    ],
    answer: [{
      name: 'Tamar',
    },{
      name: 'Eyal',
    }, {
      name: 'Bar',
    }, {
      name: 'Amit'
    },
    {
      name: 'Shelly'
    },
    {
      name: 'Roni'
    },
    {
      name: 'Shira'
    },
    {
      name: 'Omer'
    }
    ]
  }),
  methods:{
    compareLists() {
      let win = true;
      this.tags.forEach((person, index) => {
        if(person.name === this.answer[index].name) {
          person.status = 'correct';
        } else {
          win = false;
        }
      });

      if(win) this.completeGame();
    },
    completeGame() {
      this.$confetti.start();
      setTimeout(() => this.$confetti.stop(), 100000);
      this.ifShow = true;
    }
  }
})
</script>

<style scoped>

</style>