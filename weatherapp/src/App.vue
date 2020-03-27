<template>
  <div id="app">
    <h1>Weather App</h1>
    <footer class="page-footer">
  <div class="container">
    <small>Made with <span>❤</span> by <a href="#" target="_blank">Aimene Nouri</a>
    </small>
  </div>
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
}
/* FOOTER
–––––––––––––––––––––––––––––––––––––––––––––––––– */
.page-footer {
  text-align: center;
  font-size: 22px;
  margin-top: 650px;
  bottom: 0;
}

.page-footer span {
  color: red;
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
  background-color: rgba(19, 187, 181, 0.502);
}
.page-footer a:hover:after {
  top: 0%;
}
</style>
