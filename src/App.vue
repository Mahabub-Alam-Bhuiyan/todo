<template>
  <nav class="navbar navbar-expand-lg ">
    <div class="container">
        <ul class="navbar-nav ">
          <li class="nav-item">
            <router-link to="/">Home</router-link>
          </li>
          <li class="nav-item">
            <router-link to="/about">Todo</router-link>
          </li>
        </ul>
      </div>
  </nav>

  <router-view/>
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
.navbar{
  padding: 0 !important;
  margin: 0 !important;
  //background-color: #6944ec;
  background-color: #6A5ACD;
}
.nav-item{
padding: 16px 0px;
  list-style: none;
  cursor: pointer;
  a{
    padding: 20px 40px;
    color: white;
    text-decoration: none;
  }
}
.nav-item a:hover{
  //background-color: #7f66ec;
  background-color:	#7B68EE;
}
</style>
