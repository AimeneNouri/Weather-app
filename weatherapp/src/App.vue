<template>
  <div id="app">
  <h1>Weather App</h1>
  <div class="container">
  <div class="search-box">
		<input 
      type="text" 
      placeholder="Tape City Name" 
      class="search-bar" 
      v-model="requete"
      @keypress="fetchTheWeather"
    /></div> 
  </div>
  
    <section class="location">
      <div class="city">Casablanca, MA</div>
      <div class="date">Saturday</div>
    </section>
    <div class="current">
      <div class="temperature">15<span>°c</span></div>
      <div class="weather">Sunny</div>
      <div class="high-low">13°c / 16°c</div>
    </div>
  <footer class="page-footer">
    <small>Made with <span>❤</span> by <a href="https://github.com/AimeneNouri" target="_blank">Aimene Nouri</a>
    </small>
  </footer>
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
        fetch(`${this.url_base}weather?q=${this.query}&units=metric&APPID=${this.api_key}`)
        .then(response => {
          return response.json();
        }).then(this.SetResultat);
      }
    },
    SetResultat(res){
      this.weather = res;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: rgb(44, 62, 80);
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
}
.container {
  position: relative;
  margin: calc(5px + 2vh + 2vw) auto 0 auto;
  padding: 0;
  width: 90%;
  max-width: 840px;
}
/* SEARCH-box
–––––––––––––––––––––––––––––––––––––––––––––––––– */
.search-box
{
  width: 100%;
  margin-bottom: 30px;
}

.search-box .search-bar{
  width: 90%;
  padding: 15px;
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
  margin-bottom: 5px;
}

.location .date{
  font-size: 20px;
}

.current .temperature{
  color: #ffffff;
  font-size: 102px;
  font-weight: 900;
  text-shadow: 4px 8px rgba(44, 62, 80, 0.6); 
}
/* FOOTER
–––––––––––––––––––––––––––––––––––––––––––––––––– */
.page-footer {
  color: #ffffff;
  text-align: center;
  font-size: 22px;
  position: absolute;
  margin-left: 5px;
  margin-bottom: 5px;
  bottom: 0;
}

.page-footer span {
  color: rgb(255, 0, 0);
}
.page-footer a {
  text-decoration: none;
  color: #ffffff;
  position: relative;
   bottom: 0;
  left: 0;
  right: 0;
  }
.page-footer a:after {
  content: "";
  position: absolute;
  z-index: 1;
  top: 60%;
  left: -0.01em;
  right: -0.01em;
  bottom: 0;
  transition: top 200ms cubic-bezier(0, .8, .13, 1);
  background-color: #ff000085;
}
.page-footer a:hover:after {
  top: 0%;
}
</style>
