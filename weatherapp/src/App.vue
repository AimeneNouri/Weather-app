<template>
  <div id="app">
    <h1>Weather App</h1>
  <div class="container">
  <div class="search-box">
				<input type="text" placeholder="Search" class="search-bar" autocomplete="off">
	</div> 
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
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  align-items: center;
}
body{
  background: #ced6dd;
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
  box-shadow: 0px 0px 6px rgba(70, 70, 70, 0.75);
  outline: none;
  background: none;
  background-color: rgba(255,255,255,0.5);
  border-radius: 0px 30px 0px 30px;
  transition: 0.4s;
}
/* FOOTER
–––––––––––––––––––––––––––––––––––––––––––––––––– */
.page-footer {
  text-align: center;
  font-size: 22px;
  margin-top: 550px;
}

.page-footer span {
  color: rgb(255, 0, 0);
}
.page-footer a {
  text-decoration: none;
  color: #2c3e50;
  position: relative;
   bottom: 0;
  left: 0;
  right: 0;
  }
.page-footer a:after {
  content: "";
  position: absolute;
  z-index: -1;
  top: 60%;
  left: -0.1em;
  right: -0.1em;
  bottom: 0;
  transition: top 200ms cubic-bezier(0, .8, .13, 1);
  background-color: rgba(255, 0, 0, 0.52);
}
.page-footer a:hover:after {
  top: 0%;
}
</style>
