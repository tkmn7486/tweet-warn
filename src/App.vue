<template>
  <div id="nav">
    <div class="title">
      <h3>DODGY TWEET</h3>
      <small>- 怪しいTwitterアカウント共有サイト -</small>
    </div>
    <div class="container-fluid">
      <div class="row">
        <div class="side-bar col-0 col-md-3 d-none d-md-block">
          <div class="menu-item">
            <router-link to="/">
              <img src="./assets/home.png" class="mini-icon">
              ホーム
            </router-link>
          </div>
          <div class="menu-item">
            <router-link to="/all_list">
              <img src="./assets/all_account.png" class="mini-icon">
              アカウント一覧
            </router-link>
          </div>
          <div class="menu-item">
            <router-link to="/report">
              <img src="./assets/report.png" class="mini-icon">
              通報フォーム
            </router-link>
          </div>
          <div class="menu-item">
            <router-link to="/about">
              <img src="./assets/about.png" class="mini-icon">
              使い方
            </router-link>
          </div>
        </div>

        <div class="side-bar col-2 col-md-0 d-block d-md-none">
          <div class="menu-item-mobile">
            <router-link to="/">
              <img src="./assets/home.png" class="side-icon">
            </router-link>
          </div>
          <div class="menu-item-mobile">
            <router-link to="/all_list">
              <img src="./assets/all_account.png" class="side-icon">
            </router-link>
          </div>
          <div class="menu-item-mobile">
            <router-link to="/report">
              <img src="./assets/report.png" class="side-icon">
            </router-link>
          </div>
          <div class="menu-item-mobile">
            <router-link to="/about">
              <img src="./assets/about.png" class="side-icon">
            </router-link>
          </div>
        </div>
        <div class="col col-md-9">
          <router-view />
        </div>
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
  color: #4B4B4B;
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
  color: #696969;;
  text-decoration: none;
}

#nav a.router-link-exact-active {
  color: #4B4B4B;
}

.menu-item{
  margin: 15px 0px;
}

.menu-item-mobile{
  margin-bottom: 30px;
}

.side-icon{
  width: 10vw;
}

.side-icon{
  filter: invert(100%) sepia(0%) saturate(11%) hue-rotate(143deg) brightness(101%) contrast(93%);
}

.router-link-exact-active .side-icon{
  filter: none;
}

.router-link-exact-active .mini-icon{
  filter: none;
}

.mini-icon{
  width: 30px;
  margin: 5px;
  vertical-align: -15px;
  filter: invert(100%) sepia(0%) saturate(11%) hue-rotate(143deg) brightness(101%) contrast(93%);
}
</style>
