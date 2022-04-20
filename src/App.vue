<template>
  <div id="app">
    <div id="nav">
       <router-link to="/" class="navbar-brand" href="https://www.besalcoinmobiliaria.cl">
                <img src="https://www.besalcoinmobiliaria.cl/wp-content/uploads/2020/11/logo_75.png" alt="" /></router-link>

    </div>
    <router-view/>
  </div>
</template>

<style>
#app {
 background-color: #0e1a38;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #0e1a38;
}

#nav a.router-link-exact-active {
  color: #42b983;
}

 .modal-backdrop {
   display :none;
   color: #2c3e50;
}

.modal-content {
    position: relative;
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-orient: vertical;
    -webkit-box-direction: normal;
    -ms-flex-direction: column;
    flex-direction: column;
    width: 1200px;
    height: 750px;
    right: 350px;
   
    pointer-events: auto;
    background-color: #0e1a38 !important;
    color: #FFF;
  
border: 1px solid #69AAE6;
  
    
}

@media (max-width: 900px) {
  .modal-content {
    position: relative;
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-orient: vertical;
    -webkit-box-direction: normal;
    -ms-flex-direction: column;
    flex-direction: column;
    width: 100%;

    right: -10px;
   
    pointer-events: auto;
    background-color: #2c3e50 !important;
    color: #FFF;
    opacity: 95%;
border: 1px solid #69AAE6;
   
  }
}

</style>
