<template>
  <v-card
    class="mx-auto overflow-hidden"
    height="1000"
  >
    <v-app id="inspire">
      <v-app-bar
        app
        clipped-right
        dark
        src="https://i.picsum.photos/id/283/1920/1080.jpg?hmac=VZ2X9gUoyGt_QHQvSkxka5LvnUxGA-apDHwcfIiLHAM"
      >
        <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
        <v-toolbar-title><h3>찜 List</h3></v-toolbar-title>
        <v-spacer></v-spacer>
          <v-btn icon color="red">
            <v-icon>mdi-heart</v-icon>
          </v-btn>
          <v-menu
            bottom
            left
          >
          </v-menu>
        <slot name="menubar"></slot>
      </v-app-bar>
      <v-navigation-drawer
        v-model="drawer"
        app
      >
        <v-list dense>
          <v-list-item @click.stop="left = !left">
            <v-list-item-action>
              <v-icon>mdi-home</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title @click="home">홈으로 이동</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
        <v-list dense>
          <v-list-item @click.stop="left = !left">
            <v-list-item-action>
              <v-icon>mdi-cart</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title @click="cart">찜</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-navigation-drawer>
      <v-container>
        <v-content id="content">
          <slot name="content" class="font">
          </slot>
        </v-content>
      </v-container>
      <v-footer
        app
        color="brown lighten-3"
        class="white--text"
        shrink-on-scroll
      >
        <v-spacer></v-spacer>
        <span>&copy; Bank it</span>
      </v-footer>
    </v-app>
  </v-card>
</template>

<script>
import router from '../router'

export default {
  name: 'VuetifyBoardListPage',
  components: {
  },
  data: () => ({
    pageArray: [],
    tab: null,
    BoardItems: [
      { tab1: '찜' }
    ],
    components: { },
    drawer: false,
    left: false
  }),
  methods: {
    home () {
      (window.location.pathname !== '/Bank') ? router.push('/Bank') : router.go(0)
    },
    cart () {
      (window.location.pathname !== '/BankCart') ? router.push('/BankCart') : router.go(0)
    }
  }
}
</script>
