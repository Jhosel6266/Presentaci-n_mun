<template>
  <div class="wrapper">
    <side-bar>
      <template slot="links">
        <!-- <sidebar-link to="/dashboard" :name="$t('sidebar.dashboard')" icon="tim-icons icon-chart-pie-36"/> -->
          <!-- <sidebar-link to="/Protocolo" :name="$t('sidebar.PROTOCOLO')" icon="tim-icons icon-map-big"/> -->
        <br>
        <br>
        <br>
        <br>
        <br>
        <br>
        <sidebar-link to="/foto" :name="$t('sidebar.foto')" <img
              src="https://riversideeddy.ca/wp-content/uploads/2017/10/united-nations-day-2012_241012.jpg"
              alt="mun">
        <!--aqui se aagregan coasa del menu de la izquierda  -->
        
      </template>
    </side-bar>
    <div class="main-panel">
      <top-navbar></top-navbar>

      <dashboard-content @click.native="toggleSidebar">

      </dashboard-content>

      <content-footer></content-footer>
    </div>
  </div>
</template>
<style lang="scss">
</style>
<script>
import TopNavbar from "./TopNavbar.vue";
import ContentFooter from "./ContentFooter.vue";
import DashboardContent from "./Content.vue";
import MobileMenu from "./MobileMenu";
export default {
  components: {
    TopNavbar,
    ContentFooter,
    DashboardContent,
    MobileMenu
  },
  methods: {
    toggleSidebar() {
      if (this.$sidebar.showSidebar) {
        this.$sidebar.displaySidebar(false);
      }
    }
  }
};
</script>
