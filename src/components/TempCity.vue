<template>
  <v-card class="mx-auto bg" height="524" flat>
    <v-toolbar color="#f0f2f5">
      <v-toolbar-title>Weather of City</v-toolbar-title>
    </v-toolbar>

      <v-card-text>
        <v-row align="center">
          <v-col class="text-h2" cols="12"> 
                {{ city }}
          </v-col>
          <v-col class="body-2 teal accent-4" cols="12">
              {{ dateBuilder() }}
          </v-col>
 
        </v-row>
      </v-card-text>


      <v-list class="transparent">
        <v-list-item v-for="item in forecast" :key="item.day">
          <v-list-item-title>{{ item.dt_txt }}</v-list-item-title>

          <v-list-item-icon>
            <v-icon>{{item.weather[0].main === 'Clouds' ? 'mdi-cloud' : 'mdi-white-balance-sunny'}}</v-icon>
          </v-list-item-icon>

          <v-list-item-subtitle class="text-right">
            {{ Math.floor(item.main.temp) - 273 }}&deg;C
          </v-list-item-subtitle>   
        </v-list-item>
      </v-list>
    
  </v-card>
</template>

<script>
export default {
    props: {
        city: {
            type: String,
            default: "",
        },
        temp: {
            type: Number,
            default: 0,
        },
        days: {
            type: Array,
            default: []
        },

        forecast: {
            type: Array,
            default: []
        }

    },

  data() {
    return {
 

    };
  },

  

  methods: {
   dateBuilder() {
      let d = new Date() 
      let daysName = ["Sunday" , "Monday" , "Tuesday" , "Wednesday" , "Thursday" , "Friday" , "Saturday"];
      let months = ["January","February","March","April","May","June","July","August","September","October","November","December"];
      let day = daysName[d.getDay()]
      let date = d.getDay()
      let month = months[d.getMonth()]
      let year = d.getFullYear() 

      return `${day} ${date} ${month} ${year}`
    },

    
  }
};
</script>

<style scoped>
.bg {
    background:url('https://cdn.wallpapersafari.com/27/32/jt4AoG.jpg') ;
    overflow: scroll;
}

</style>