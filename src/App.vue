<template>
  <div id="nav">
    <div class="title">
      <h3>DODGY TWEET</h3>
      <small>- 怪しいTwitterアカウント共有サイト -</small>
    </div>
    <div class="container-fluid">
      <div class="row">
        <div class="side-bar col-0 col-md-3 d-none d-md-block">
          <router-link to="/all_list">
            <img src="./assets/home.png" class="mini-icon">
            ホーム
          </router-link>
          <br>
          <br>
          <router-link to="/all_list">
            <img src="./assets/all_account.png" class="mini-icon">
            アカウント一覧
          </router-link>
          <br>
          <br>
          <router-link to="/report">
            <img src="./assets/report.png" class="mini-icon">
            通報フォーム
          </router-link>
          <br>
          <br>
          <router-link to="/about">
            <img src="./assets/about.png" class="mini-icon">
            使い方
          </router-link>
        </div>

        <div class="side-bar col-2 col-md-0 d-block d-md-none">
          <router-link to="/">
            <img src="./assets/home.png" class="side-icon">
          </router-link>
          <br>
          <br>
          <router-link to="/all_list">
            <img src="./assets/all_account.png" class="side-icon">
          </router-link>
          <br>
          <br>
          <router-link to="/report">
            <img src="./assets/report.png" class="side-icon">
          </router-link>
          <br>
          <br>
          <router-link to="/about">
            <img src="./assets/about.png" class="side-icon">
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
  text-align: left;
}

#nav {
  padding: 10px;
  /* background-color: rgb(0, 172, 238); */
  /* border-bottom: none; */
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

.mini-icon{
  width: 30px;
  margin: 5px;
  vertical-align: -15px;
}
</style>
