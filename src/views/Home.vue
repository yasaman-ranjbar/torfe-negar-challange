<template>
  <v-card flat class="wrapper">
      <v-row no-gutters>
      <v-col cols="4">
        <CityList 
        :items="items" 
        @selectCity="selectCity($event)"
          />
      </v-col>
      <v-col cols="8">
        <TempCity 
        :city="city" 
        :temp="temp" 
        :days="days"
        :forecast="forecast"
          />
      </v-col>
    </v-row>
  </v-card>
</template>

<script>
import axios from "axios";
import CityList from "../components/CityList.vue";
import TempCity from "../components/TempCity.vue";
export default {
  name: "Home",

  components: { CityList, TempCity },

  data() {
    return {
     forecast: [],
      items: [
        {
          avatar:"https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQB_pY-xVknMrZlr2R-eNFVHDUO90_Cxq91AA&usqp=CAU",
          title: "Tehran",
          latitude: 35, 
          longitude: 51,
        },
        { divider: true, inset: true },
        {
          avatar:"https://images.pexels.com/photos/1797161/pexels-photo-1797161.jpeg?auto=compress&cs=tinysrgb&dpr=1&w=500",
          title: "Rome",
          latitude: 41, 
          longitude: 12,
        },
        { divider: true, inset: true },
        {
          avatar:"https://a.cdn-hotels.com/gdcs/production27/d274/43014cca-c88c-4061-ace8-58edc24531ee.jpg?impolicy=fcrop&w=800&h=533&q=medium",
          title: "London",
          latitude: 51, 
          longitude: -0.2,
        },
        { divider: true, inset: true },
        {
          avatar:"https://images.pexels.com/photos/1549326/pexels-photo-1549326.jpeg?auto=compress&cs=tinysrgb&dpr=1&w=500",
          title: "Istanbul",
          latitude: 41, 
          longitude: 28,
        },
        { divider: true, inset: true },
        {
          avatar:"https://d3opmws30bxnoy.cloudfront.net/wp-content/uploads/2017/08/burjalarab.jpg",
          title: "Dubai",
          latitude: 25, 
          longitude: 55,
        },
      ],

      app_key: "4148eba9fcabd4c276eccc1b25bf33cc",
      api: "https://api.openweathermap.org/data/2.5",
      city: "Rome",
      temp: 0,
      days: [],
      lat: '',
      lon: '',
     
    };
  },

  methods: {
    selectCity(event) {
         const cityName = this.items.find( x => x.title == event)
         this.city = cityName.title;
         this.lat = cityName.latitude;
         this.lon = cityName.longitude;

         axios
        .get(`${this.api}/forecast?lat=${this.lat}&lon=${this.lon}&appid=${this.app_key}`)
        .then((res) => {
          this.forecast = res.data.list
          console.log(res);
        });
    },

    created() {
    console.log(window);
  },

    


  },
};
</script>

<style scoped>
.wrapper {
  margin-top: -7rem;
}
</style>


