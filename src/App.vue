<template>
  <v-app>
    <v-navigation-drawer
      temporary
      v-model="showDrawer"
      fixed
      app
      width="250"
      class="nav"
    >
      <v-list>
        <v-list-tile class="nav-list-avatar">
          <v-avatar size="60" @click="go('/')" class="avatar-ripple">
            <img src="../static/img/avatar.jpg" alt="avatar">
          </v-avatar>
        </v-list-tile>
        <v-list-tile ripple :to="{path: '/'}" class="nav-list-item">
          <v-list-tile-action>
            <v-icon>home</v-icon>
          </v-list-tile-action>
          <v-list-tile-title>主页</v-list-tile-title>
        </v-list-tile>
        <v-list-tile ripple :to="{path: '/archives'}" class="nav-list-item">
          <v-list-tile-action>
            <v-icon>archive</v-icon>
          </v-list-tile-action>
          <v-list-tile-title>归档</v-list-tile-title>
        </v-list-tile>
        <v-list-tile ripple :to="{path: '/category'}" class="nav-list-item">
          <v-list-tile-action>
            <v-icon>category</v-icon>
          </v-list-tile-action>
          <v-list-tile-title>分类</v-list-tile-title>
        </v-list-tile>
        <v-list-tile ripple :to="{path: '/person'}" class="nav-list-item">
          <v-list-tile-action>
            <v-icon>person</v-icon>
          </v-list-tile-action>
          <v-list-tile-title>关于我</v-list-tile-title>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar-side-icon @click.stop="showDrawer = !showDrawer" fixed class="toolbar-icon"></v-toolbar-side-icon>
    <v-content>
      <router-view/>
    </v-content>
    <v-footer :fixed="fixed" app>
      <span class="footer">&copy; 2018 by Courtier</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      drawer: true,
      fixed: false,
      items: [{
        icon: 'bubble_chart',
        title: 'Inspire'
      }],
      miniVariant: false,
      showDrawer: false,
      title: 'Vuetify.js'
    }
  },
  name: 'App',
  methods: {
    go(url) {
      this.$router.push({ path: url });
    }
  }
}
</script>

<style scoped>
.nav {
  transition: transform .6s ease-in-out;
}
.nav-list-avatar {
  height: 180px;
  padding-top: 10px;
  margin-top: -8px;
  margin-bottom: 10px;
  border-bottom: 1px solid #d1d1d1;
  background-color: #d1d1d1;
  background-image: url(../static/img/bg-avatar.jpg);
  background-size: 100%;
}
.avatar-ripple {
  position: relative;
  cursor: pointer;
}
.avatar-ripple>img {
  z-index: 2;
}
.avatar-ripple:hover::after {
content:' ';
position: absolute;
left: 50%;
top: 50%;
transform: translate(-50%, -50%);
z-index: 1;
width: 10px;
height: 10px;
background-color: #ddd;
border-radius: 50%;
box-shadow: 0 0 10px rgba(0, 0, 0, .3);
animation: ripple 1s ease;
}
@keyframes ripple {
  0% {
    opcity:75;
    width:0;
    height:0;
  }
  100% {
    opacity: 0;
    width: 150px;
    height: 150px;
  }
}
.toolbar-icon {
  top: 30px;
  left: 15px;
}
.footer {
  text-align: center;
}
</style>
