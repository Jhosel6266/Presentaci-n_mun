<template>
  <nav class="navbar navbar-expand-lg navbar-absolute"
       :class="{'bg-white': showMenu, 'navbar-transparent': !showMenu}">
    <div class="container-fluid">
      <div class="navbar-wrapper">
        <div class="navbar-toggle d-inline" :class="{toggled: $sidebar.showSidebar}">
          <button type="button"
                  class="navbar-toggler"
                  aria-label="Navbar toggle button"
                  @click="toggleSidebar">
            <span class="navbar-toggler-bar bar1"></span>
            <span class="navbar-toggler-bar bar2"></span>
            <span class="navbar-toggler-bar bar3"></span>
          </button>
        </div>
        <a class="navbar-brand" href="#pablo">Tecnologico de monterrey</a>
        <!-- aqui se cambia lo que  pasa en la ruta de ariiba  -->
      </div>
      <button class="navbar-toggler" type="button"
              @click="toggleMenu"
              data-toggle="collapse"
              data-target="#navigation"
              aria-controls="navigation-index"
              aria-label="Toggle navigation">
        <span class="navbar-toggler-bar navbar-kebab"></span>
        <span class="navbar-toggler-bar navbar-kebab"></span>
        <span class="navbar-toggler-bar navbar-kebab"></span>
      </button>

      <collapse-transition>
        <div class="collapse navbar-collapse show" v-show="showMenu">
          <ul class="navbar-nav" :class="$rtl.isRTL ? 'mr-auto' : 'ml-auto'">
            <div class="search-bar input-group" @click="searchModalVisible = true">

            </div>
            <base-dropdown tag="li"
                           :menu-on-right="!$rtl.isRTL"
                           title-tag="a" class="nav-item">
              <a slot="title" href="#" class="dropdown-toggle nav-link" data-toggle="dropdown" aria-expanded="true">
                <div class="notification d-none d-lg-block d-xl-block"></div>
                <i class="tim-icons icon-sound-wave"></i>
                <p class="d-lg-none">
                  New Notifications
                </p>
              </a>
              <li class="nav-link">
                <a href="#" class="nav-item dropdown-item">Mike John responded to your email</a>
              </li>
              <li class="nav-link">
                <a href="#" class="nav-item dropdown-item">You have 5 more tasks</a>
              </li>
              <li class="nav-link">
                <a href="#" class="nav-item dropdown-item">Your friend Michael is in town</a>
              </li>
              <li class="nav-link">
                <a href="#" class="nav-item dropdown-item">Another notification</a>
              </li>
              <li class="nav-link">
                <a href="#" class="nav-item dropdown-item">Another one</a>
              </li>
            </base-dropdown>
            <!-- -->
            <!-- -->
            <!-- -->
            <!-- -->
            <div class="btn-group">
              <base-dropdown tag="li"
                           title-tag="a"
                           menu-classes="dropdown-black">
              <a slot="title" href="#" class="dropdown-toggle nav-link" data-toggle="dropdown" aria-expanded="true">
                <base-button type="danger"><img src="https://lh3.google.com/u/0/d/1VKBjn78uMAvMT_c_xgYeVNg4jOXN-k6W=w2880-h1605-iv1" /> Log in
                </base-button >
              </a>
              <li>
               <base-input v-model="user" @click.native.capture.stop required="true" label="Usuario"
                  type="email"
                  placeholder="Matricula">
              </base-input>
              <base-input v-model="password" @click.native.capture.stop required="true" label="Contraseña"
                  type="password"
                  placeholder="Matricula">
              </base-input>
              </li>
              <div class="dropdown-divider" ></div>
              <li>
                <base-button native-type="submit" type="primary" v-on:click="login">Submit</base-button>
              </li>
              </base-dropdown>
          </div>

            <!-- -->
          </ul>
        </div>
      </collapse-transition>
    </div>
  </nav>
</template>
<script>
/* eslint-disable */
  import { CollapseTransition } from 'vue2-transitions';
  import Modal from '@/components/Modal';
  import axios from 'axios';
  export default {
    components: {
      CollapseTransition,
      Modal
    },
    computed: {
      routeName() {
        const { name } = this.$route;
        return this.capitalizeFirstLetter(name);
      },
      isRTL() {
        return this.$rtl.isRTL;
      }
    },
    data() {
      return {
        activeNotifications: false,
        showMenu: false,
        searchModalVisible: false,
        searchQuery: '',
        user:'',
        password: '',
        url: 'https://restapi-mun.herokuapp.com/user/1'
      };
    },
    methods: {
      login(){
       var vueInstance = this;
        if(this.user && this.password){
          sessionStorage.setItem('email', this.user);
          sessionStorage.setItem('password', this.password);
          
          axios({
          method: 'POST',
          url: this.url,
          headers: {
            'Content-Type': 'application/json',
          },
          data: {
            password: this.password,
            email: this.user
          }
        })
        .then(function (response) {
          var token = (`Bearer ${response.data.token}`)
          sessionStorage.setItem('token', token);     

        axios({
        method: 'GET',
        url: "https://restapi-mun.herokuapp.com/user/committee",

        headers: {Authorization: token,
              'Content-Type': 'application/json'}
            })

        .then(function (response) {
        sessionStorage.setItem('countries', JSON.stringify(response.data))
           })
        })
        .catch(function (error) {
            sessionStorage.clear();
        })
        }else{
          return sessionStorage.clear();
        }
      },
      getauth(){
        var vueInstance = this;
      },
      capitalizeFirstLetter(string) {
        return string.charAt(0).toUpperCase() + string.slice(1);
      },
      toggleNotificationDropDown() {
        this.activeNotifications = !this.activeNotifications;
      },
      closeDropDown() {
        this.activeNotifications = false;
      },
      toggleSidebar() {
        this.$sidebar.displaySidebar(!this.$sidebar.showSidebar);
      },
      hideSidebar() {
        this.$sidebar.displaySidebar(false);
      },
      toggleMenu() {
        this.showMenu = !this.showMenu;
      }
    }
  };
</script>
<style>
</style>
