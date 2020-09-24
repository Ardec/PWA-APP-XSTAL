<template>
  <v-app id="inspire">
    <v-navigation-drawer
      v-model="drawer"
      app
    >
      <v-list dense>

        <v-img src="../src/assets/logocz.jpg" aspect-ratio="4" contain="true" class="mb-6 mt-4"></v-img>
        <v-list-item link>
          <v-list-item-action>
            <v-icon>mdi-home</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title class="font-weight-light">Start</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item link>
          <v-list-item-action>
            <v-icon>mdi-home</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title  class="font-weight-light">Ogrodzenia panelowe</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item link>
          <v-list-item-action>
            <v-icon>mdi-home</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title  class="font-weight-light">Bramy przesuwne</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item link>
          <v-list-item-action>
            <v-icon>mdi-email</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title class="font-weight-light">Kontakt</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar
      app
      color="indigo"
      dark
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar-title class="text-uppercase">centrum ogrodzeń</v-toolbar-title>
    </v-app-bar>

    <v-main>
     <v-img src="../src/assets/img3399.jpg" aspect-ratio="4">
     </v-img>
      <p class="mt-10 titletop text-h2 text-uppercase font-weight-bold">Wolność i Bezpieczeństwo</p>
     <h2 class="font-weight-light pl-4 pt-4">Zabezpiecz swoją posesję</h2>
     <p class="font-weight-light pl-4 mt-4">od 1992 roku pomagamy w naszym klientom w doborze najkorzystniejszych rozwiązań Lorem ipsum dolor sit amet consectetur adipisicing elit. Tempore nesciunt tempora porro fugiat unde beatae veniam, temporibus esse distinctio, dolorum hic. Odit deserunt, exercitationem rerum cupiditate non illum impedit nisi? Lorem ipsum dolor sit amet consectetur adipisicing elit. Labore reprehenderit tempore sint omnis ex culpa odio officiis, cumque dolore quis quisquam voluptas. Fuga, ad voluptatibus quas expedita officiis qui repellendus! Lorem ipsum dolor sit amet consectetur adipisicing elit. Excepturi voluptatem totam a? Atque voluptate incidunt fuga quibusdam esse quisquam nam, eligendi optio quis excepturi voluptates deserunt, ipsa, unde sequi cupiditate?</p>
      <v-container
        class="fill-height"
        fluid
      >
        <v-row
          align="center"
          justify="center"
        >
          <v-col class="text-center">
            <v-tooltip left>
              <template v-slot:activator="{ on }">
                <v-btn
                  :href="source"
                  icon
                  large
                  target="_blank"
                  v-on="on"
                >
                  <v-icon large>mdi-code-tags</v-icon>

                </v-btn>
              </template>
              <span>Source</span>
            </v-tooltip>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
    <v-footer
      color="indigo"
      app
    >
      <span class="white--text">&copy; {{ new Date().getFullYear() }}</span>
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

<style>

.titletop{
color:white;
position: absolute;
top: 80px;
z-index: 1000;
padding-left: 80px;
}

</style>