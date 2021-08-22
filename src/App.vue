<template>
  <v-app id="inspire">
   <div id="nav">
    </div>
    <v-navigation-drawer
      v-model="drawer"
      app
    >
     <v-list dense>
        <v-img src="../src/assets/xstal1.png" aspect-ratio="4" contain="true" class="mb-6 mt-4 logo"></v-img>
        <router-link tag="li" to="/">
        <v-list-item link>
          <v-list-item-action>
            <v-icon color="black">mdi-color-helper</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title class="font-weight-light linkeded"> Start</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
                  </router-link>
                  <router-link tag="li" to="/systemy">
        <v-list-item link>
          <v-list-item-action>
            <v-icon color="black disabled">mdi-view-array</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title  class="font-weight-light disabled">Ogrodzenie frontowe</v-list-item-title>

          </v-list-item-content>
        </v-list-item>
        </router-link>
         <router-link tag="li" to="/kalkulator">
        <v-list-item link>
          <v-list-item-action>
            <v-icon color="black">mdi-set-square</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title  class="font-weight-light">Kalkulator ogrodzeń panelowych</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        </router-link>
        <router-link tag="li" to="/Bramy">
        <v-list-item link>
          <v-list-item-action>
            <v-icon color="black">mdi-view-column-outline</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title  class="font-weight-light">Kreator bram i furtek</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        </router-link>
        <router-link tag="li" to="/montaze">
        <v-list-item link>
          <v-list-item-action>
            <v-icon color="black">mdi-wrench-outline</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title  class="font-weight-light">Informacje i Regulaminy</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        </router-link>
        <router-link tag="li" to="/kontakt">
        <v-list-item link>
          <v-list-item-action>
            <v-icon color="black">mdi-phone-message</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title class="font-weight-light">Kontakt</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        </router-link>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar
      app
      color=#0C6CF0
      dark
      class="color-gr"
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
      <!-- <v-toolbar-title class="text-uppercase">ssddasdsa</v-toolbar-title> -->
      <div class="top-panel">
         <v-btn class="sign-in-btn" disabled depressed outlined small>
      Rejestracja
    </v-btn>
      <v-btn class="sign-in-btn" disabled depressed outlined small>
      Logowanie
    </v-btn>
      </div>
    </v-app-bar>

    <!-- <v-main class="bgdiv pt-0 footer-gr" style="background-image: src('assets/steelbg.jpg');"> -->
    <v-main class="bgdiv pt-0 footer-gr">
      <!-- <p class="mt-10 titletop text-h2 text-uppercase font-weight-bold">Wolność i Bezpieczeństwo</p> -->
                   <router-view/>

    </v-main>
    <v-footer
      class="color-gr"
      color=#0C6CF0
      app
      height="64px"
    >
      <span class="footer-name white--text">&copy; {{ new Date().getFullYear() }} Kamil.Kaczmarczyk.box@gmail.com </span>
    </v-footer>
  </v-app>
</template>

<script>
  export default {
    props: {
      source: String,
    },
    data: () => ({
      drawer: null,
    }),
  }
</script>

<style lang="scss">

body,ul,li {list-style-type: none;}


.v-application--wrap
{
margin-top:-10px;
// background-image: url("assets/steelbg.jpg");
background-color: #CCBEB8;
// background-size: cover;
}

li {
  list-style-type: none!important;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.bgdiv{
height:100%;
// background-color:rgba(255,255,255,0.75);
// background-color:rgb(255, 255, 255);
 background: linear-gradient(
      152.80deg,
      rgba(255, 255, 255, 0.85) 4.58%,
      rgba(255, 255, 255, 0.95) 80.71%,
    )
}


#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
    &.router-link{
      color:red;
    }
  }
}
.disabled{
    color:rgb(163, 163, 163);
  }
  .color-gr{
    background: linear-gradient(
      152.80deg,
      rgba(255, 255, 255, 0.12) 1.58%,
      rgba(255, 255, 255, 0.13) 70.71%,

    )
  }

  .color-gr2{
    background: linear-gradient(
      152.80deg,
      rgba(255, 255, 255, 0.12) 1.58%,
      rgba(255, 255, 255, 0.23) 70.71%,

    )
  }

  .top-panel
  {
    display:flex;
    justify-content: right;
    width:100%;
    flex-direction: row-reverse;
  }


  .footer-name{
    line-height: 2rem;
    font-size:12px;
  }

  .logo{
    margin:0 12%;
  }

  .sign-in-btn{
    margin:0px 10px;
  }

@media screen and (max-width: 840px){
  .sign-in-btn{
    height:20px;
    font-size:10px;
  }
}

.sitemid
{
  display:block;
  line-height:1.2rem;
  font-size: 1.1rem;
  font-weight: 600;
  letter-spacing: 0.05rem;
  text-transform: uppercase;
  padding-bottom: 10px;
}

.sitebot
{
  display:block;
  line-height:1rem;
  font-size: 0.9rem;
  font-weight: 500;
  letter-spacing: 0.05rem;
  text-transform: uppercase;
  padding-bottom: 10px;
}

div .calcsection{
  border-radius: 15px;
  padding:1px 5px;
  margin:10px 0px;
  background-color:#0C6CF0
}


</style>
