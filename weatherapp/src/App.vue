<template>
  <div id="app">
  <h1>Weather App</h1>
  <div class="container">
  <div class="search-box">
		<input 
      type="text" 
      placeholder="City Name" 
      class="search-bar" 
      v-model="requete"
      @keypress="fetchTheWeather"
    /></div> 
  </div>
  <div class="weter" v-if="typeof weather.main != 'undefined'">
    <section class="location">
      <div class="city">{{  weather.name  }}, {{  weather.sys.country  }}</div>
      <div class="date">{{ ladate() }}</div>
    </section>
    <div class="weather-wrap">
      <div class="temperature">{{  Math.round(weather.main.temp).toFixed(0)  }}<span>°c</span></div>
      <div class="weather">{{ weather.weather[0].main }}</div>
      <div class="high-low">{{ weather.main.temp_min }}°c / {{ weather.main.temp_max }}°c</div>
      <div class="humidity">Humidity: {{ weather.main.humidity }}%</div>
   </div>
  </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      api_key: '486c4f64c4a03c69e3d934323ede1cba',
      url_base: 'https://api.openweathermap.org/data/2.5/',
      requete: '',
      weather: {}
    }
  },
  methods:{
    fetchTheWeather(i){
      if (i.key == "Enter")
      {
        fetch(`${this.url_base}weather?q=${this.requete}&units=metric&APPID=${this.api_key}`)
        .then(response => {
          return response.json();
        }).then(this.SetResultat);
      }
    },
    SetResultat(res){
      this.weather = res;
    },
    ladate() {
      let i = new Date();
      let lesmois = ["January","February","March","April","May","June","July","August","September","October","November","December"];
      let jourSemaine = ["Sunday","Monday","Tuesday","Wednesday","Thursday","Friday","Saturday"];
    
      let jour = jourSemaine[i.getDay()];
      let date = i.getDate();
      let mois = lesmois[i.getMonth()];
      let annee = i.getFullYear();

      //date in string
      return `${jour} ${date} ${mois} ${annee}`;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  align-items: center;
}
html, body{
  background-image: url('./assets/m.jpg');
  background-size: cover;
  background-position: center center;
  background-attachment: fixed;
  background-repeat: no-repeat;
  padding: 0;
  margin: 0;
}
h1{
  font-weight: bold;
  font-size: 40px;
}
.container {
  margin: calc(0px + 2vh + 0vw) auto 0 auto;
  padding: 0;
  width: 90%;
  max-width: 840px;
}
/* SEARCH-box
–––––––––––––––––––––––––––––––––––––––––––––––––– */
.search-box
{
  width: 100%;
  margin-bottom: 10px;
}

.search-box .search-bar{
  width: 90%;
  padding: 13px;
  color: rgb(70, 68, 68);
  font-size: 20px;
  appearance: none;
  border: none;
  box-shadow: 0px 0px 8px rgba(56, 56, 56, 0.75);
  outline: none;
  background: none;
  background-color: rgba(255,255,255,0.5);
  border-radius: 30px;
  transition: 0.4s;
  border-bottom: 4px solid #2c3e50;
}
.search-box .search-bar:focus{
  box-shadow: 0px 0px 20px rgba(70, 70, 70, 0.75);
  background-color: #f0f0f080;
}

/* Main
–––––––––––––––––––––––––––––––––––––––––––––––––– */
.location .city{
  font-size: 32px;
  font-weight: 500;
}

.location .date{
  font-size: 20px;
}

.weather-wrap .temperature{
  color: #ffffff;
  font-size: 102px;
  font-weight: 900;
  text-shadow: 2px 6px rgba(49, 71, 90, 0.6); 
}

.weather-wrap .temperature span{
  font-weight: 550;
}

.weather-wrap .weather{
  color: #f1eeee;
  font-size: 30px;
  font-weight: 900;
  font-style: italic;
  text-shadow: 2px 6px 3px rgba(38, 49, 59, 0.75);
}
.weather-wrap .high-low{
  color: #f1eeee;
  font-size: 30px;
  font-weight: 900;
  text-shadow: 2px 6px 3px rgba(38, 49, 59, 0.75);
}
.weather-wrap .humidity{
  color: #f1eeee;
  font-size: 24px;
  font-weight: 900;
  text-shadow: 2px 6px 3px rgba(38, 49, 59, 0.75);
}

</style>
