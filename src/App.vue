<template>
  <div id="nav">
    <div class="title">
      <h3>DODGY TWEET</h3>
      <small>- 怪しいTwitterアカウントのまとめサイト -</small>
    </div>
    <div class="container-fluid">
      <div class="row">
        <div class="side-bar col-0 col-md-3 d-none d-md-block">
          <router-link to="/">一覧ページ</router-link>
          <br>
          <br>
          <router-link to="/about">このサイトについて</router-link>
        </div>

        <div class="side-bar col-2 col-md-0 d-block d-md-none">
          <router-link to="/">
            <img src="./assets/logo.png" class="side-icon">
          </router-link>
          <br>
          <br>
          <router-link to="/about">
            <img src="./assets/logo.png" class="side-icon">
          </router-link>
        </div>

        <router-view class="col col-md-9"/>
      </div>
    </div>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.title{
  text-align: left;
  border-bottom: solid 3px whitesmoke;
  padding: 10px;
}

.side-bar{
  border-right: solid 3px whitesmoke;
  height: 100vh;
  padding-top: 20px;
  text-align: center;
}

#nav {
  padding: 10px;
  /* background-color: rgb(0, 172, 238); */
  /* border-bottom: none; */
}

.side-bar ul li{
  list-style: none;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}

.side-icon{
  width: 10vw;
}
</style>
