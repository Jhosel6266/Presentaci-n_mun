<template>
  <div>
    <div class="row">
      <div class="col-12">
        <card type="chart">
          <template slot="header">
            <div class="row">
              <div class="col-sm-6" :class="isRTL ? 'text-right' : 'text-left'">
                <h5 class="card-category">{{$t('dashboard.totalShipments')}}</h5>
                <h2 class="card-title">{{$t('dashboard.performance')}}</h2>
              </div>
              <div class="col-sm-6">
                <div class="btn-group btn-group-toggle"
                     :class="isRTL ? 'float-left' : 'float-right'"
                     data-toggle="buttons">
                  <label v-for="(option, index) in bigLineChartCategories"
                         :key="option"
                         class="btn btn-sm btn-primary btn-simple"
                         :class="{active: bigLineChart.activeIndex === index}"
                         :id="index">
                    <input type="radio"
                           @click="initBigChart(index)"
                           name="options" autocomplete="off"
                           :checked="bigLineChart.activeIndex === index">
                    {{option}}
                  </label>
                </div>
              </div>
            </div>
          </template>
          <div class="chart-area">
            <line-chart style="height: 100%"
                        ref="bigChart"
                        chart-id="big-line-chart"
                        :chart-data="bigLineChart.chartData"
                        :gradient-colors="bigLineChart.gradientColors"
                        :gradient-stops="bigLineChart.gradientStops"
                        :extra-options="bigLineChart.extraOptions">
            </line-chart>
          </div>
        </card>
      </div>
    </div>
    <div class="row">
      <div class="col-lg-4" :class="{'text-right': isRTL}">
        <card>
  <form>
      <card style="nav-tabs" class="text-center my-7 py-2">
  <div slot="header" class="card-header-primary">
    Speaker List
  </div>
  <h4 class="card-title">When the button is pressed you will be added to the speaker list</h4>
  <p class="card-text">The average time of speaking is from 45 sec to 1 min</p>
  <a href="#" class="btn btn-primary">Send request to be added</a>
  <div slot="footer" class="text-muted">
    <!-- 2 days ago -->
  </div>
</card>    
    </form>
</card> 
      </div>
      
      <div class="col-lg-4" :class="{'text-right': isRTL}">
        <card class="my-7">
          <form>
            <base-button type="Info">Refresh</base-button>
            <card style="nav-tabs" class="text-center">
                <div slot="header" class="card-header-primary">
                  Message from member state: Chile
                </div>
                <span> What do you think about resolution 2048? </span>
              </card>    
              <v-divider />
            <card>
              <div class>
                <div class>
                  <base-button type="success" native-type="button">Approve</base-button>                
                    <base-button type="danger">Reject</base-button>
                  </div>
                </div>
            </card>
          </form>
        </card> 
      </div>


      <div class=" col-lg-4" :class="{'text-right': isRTL}" >
        <card class="my-7 py-3">
          <form>
            <card style="nav-tabs" class="text-center">
                <div slot="header" class="card-header-primary">
                  <blockquote class="blockquote text-center">
                     <p class="mb-0"> Time remaining {{timerCount}}</p>
                    </blockquote>
                </div>
              </card>    
              <v-divider />
            <card class="rounded-xl ml-16 mr-16 mb-16 px-7">
              <div class>
                <div class>
                    <base-button  v-on:click="triggertimer" type="warning">Active Stopwatch</base-button>
                  </div>
                </div>
            </card>
          </form>
        </card> 
      </div>

      <card>
        <ul class="list-group">
  <li class="list-group-item active">Speaker list</li>
  <blockquote class="blockquote">
  <p class="mb-0"><blockquote class="blockquote text-center">Rusia </blockquote> </p>
</blockquote>
<blockquote class="blockquote">
  <p class="mb-0"><blockquote class="blockquote text-center">Mexico </blockquote> </p>
</blockquote>
<blockquote class="blockquote">
  <p class="mb-0"><blockquote class="blockquote text-center">United States </blockquote> </p>
</blockquote>
</ul>
</card>
    </div>
    <div class="row">
      <div class="col-lg-12 col-md-12">
        <card>
  <form>
<!--  -->
<div>
<card class="float-right" style="width: 72rem;" >
 <div>
      <div>
          <textarea class="form-control" type="text" label="Message" placeholder="Your message goes hear"/>
      </div>
      <base-input>
        <base-checkbox>Check me out</base-checkbox>
      </base-input> 
      <base-button type="primary" native-type="Submit">Send</base-button>
      </div>
  </card>
  </div>

  
  <!--  -->
<!-- <div>
  
    <div class="List" style="display:block; overflow-y: auto: hight: 1rem;" v-for="contact in Contactos" 
    :key= "contact.Contacto">
       <div class style="display:block; padding-top:1rem padding-bottom:1rem">
         <div class="item">{{contact.nombre}}</div>
      <div class="Item">
       <card class="text-center" style="width: 20rem;">
         
        <h4 class="card-title">{{contact.nombre}}</h4>
        <p class="card-text"><img v-bind:src="contact.URL" v-bind:alt="pic"></p>
        <a href="#" class="btn btn-primary">Send msg</a>        
      </card>
       </div>
      </div>
    
  
    
  
    </div>
</div> -->
<div class="btn-group">
  <base-dropdown>
    <template slot="title-container" slot-scope="{isOpen}">
     <base-button type="danger"><img src="https://lh3.google.com/u/0/d/1VKBjn78uMAvMT_c_xgYeVNg4jOXN-k6W=w2880-h1605-iv1" /> Countries
     </base-button>
    </template>
    <div v-for="contact in Contactos"
    :key= "contact.Contacto">
     <li>
          <a class="dropdown-item" href="#">
            <img v-bind:src="contact.URL" v-bind:alt="pic"> {{contact.nombre}}
          </a>
      </li>
  </div>
  </base-dropdown>
</div>
<!--  -->



<!--  -->
    </form>
    
</card> 
  
  <!-- <div v-for="contact in Contactos"
    :key= "contact.Contacto">
     <div>
  <card class="text-center" style="width: 20rem;">
    
        <h4 class="card-title">{{contact.nombre}}</h4>
        <p class="card-text"><img
              src="https://upload.wikimedia.org/wikipedia/en/a/a4/Flag_of_the_United_States.svg"
              alt="mun"></p>
        <a href="#" class="btn btn-primary">Send msg</a>
  </card>
</div>
  </div> -->
      </div>
    </div>
    
  </div>
</template>
<script>
/* eslint-disable */
  import LineChart from '@/components/Charts/LineChart';
  import BarChart from '@/components/Charts/BarChart';
  import * as chartConfigs from '@/components/Charts/config';
  import TaskList from './Dashboard/TaskList';
  import UserTable from './Dashboard/UserTable';
  import config from '@/config';
  import {SidebarPlugin} from 'bootstrap-vue';
  import PerfectScrollbar from 'perfect-scrollbar';

  export default {
    components: {
      LineChart,
      BarChart,
      TaskList,
      UserTable,
      name: 'InlineMethodCallComponent'
    },
    data() {
      return {
        timerCount: "",
       selected:"delegación",
        Contactos: [{nombre:"Canada", URL:"https://demos.creative-tim.com/argon-design-system/assets/img/icons/flags/CA.png"},
        {nombre:"Venezuela", URL:"https://demos.creative-tim.com/argon-design-system/assets/img/icons/flags/VE.png"},
        {nombre:"United States", URL:"https://demos.creative-tim.com/argon-design-system/assets/img/icons/flags/US.png"},
        {nombre:"Mexico", URL:"https://demos.creative-tim.com/argon-design-system/assets/img/icons/flags/MX.png"}, 
        {nombre:"Germany", URL:"https://demos.creative-tim.com/argon-design-system/assets/img/icons/flags/DE.png"}], 
        bigLineChart: {
          allData: [
            [20, 33, 14, 70, 40, 36, 31, 44, 39, 22, 29, 10],
            [80, 120, 105, 110, 95, 105, 90, 100, 80, 95, 70, 120],
            [60, 80, 65, 130, 80, 105, 90, 130, 70, 115, 60, 130]
          ],
          activeIndex: 0,
          chartData: {
            datasets: [{ }],
            labels: ['JAN', 'FEB', 'MAR', 'APR', 'MAY', 'JUN', 'JUL', 'AUG', 'SEP', 'OCT', 'NOV', 'DEC'],
          },
          extraOptions: chartConfigs.purpleChartOptions,
          gradientColors: config.colors.primaryGradient,
          gradientStops: [1, 0.4, 0],
          categories: []
        },
        purpleLineChart: {
          extraOptions: chartConfigs.purpleChartOptions,
          chartData: {
            labels: ['JUL', 'AUG', 'SEP', 'OCT', 'NOV', 'DEC'],
            datasets: [{
              label: "Data",
              fill: true,
              borderColor: config.colors.primary,
              borderWidth: 2,
              borderDash: [],
              borderDashOffset: 0.0,
              pointBackgroundColor: config.colors.primary,
              pointBorderColor: 'rgba(255,255,255,0)',
              pointHoverBackgroundColor: config.colors.primary,
              pointBorderWidth: 20,
              pointHoverRadius: 4,
              pointHoverBorderWidth: 15,
              pointRadius: 4,
              data: [80, 100, 70, 80, 120, 80],
            }]
          },
          gradientColors: config.colors.primaryGradient,
          gradientStops: [1, 0.2, 0],
        },
        greenLineChart: {
          extraOptions: chartConfigs.greenChartOptions,
          chartData: {
            labels: ['JUL', 'AUG', 'SEP', 'OCT', 'NOV'],
            datasets: [{
              label: "My First dataset",
              fill: true,
              borderColor: config.colors.danger,
              borderWidth: 2,
              borderDash: [],
              borderDashOffset: 0.0,
              pointBackgroundColor: config.colors.danger,
              pointBorderColor: 'rgba(255,255,255,0)',
              pointHoverBackgroundColor: config.colors.danger,
              pointBorderWidth: 20,
              pointHoverRadius: 4,
              pointHoverBorderWidth: 15,
              pointRadius: 4,
              data: [90, 27, 60, 12, 80],
            }]
          },
          gradientColors: ['rgba(66,134,121,0.15)', 'rgba(66,134,121,0.0)', 'rgba(66,134,121,0)'],
          gradientStops: [1, 0.4, 0],
        },
        blueBarChart: {
          extraOptions: chartConfigs.barChartOptions,
          chartData: {
            labels: ['USA', 'GER', 'AUS', 'UK', 'RO', 'BR'],
            datasets: [{
              label: "Countries",
              fill: true,
              borderColor: config.colors.info,
              borderWidth: 2,
              borderDash: [],
              borderDashOffset: 0.0,
              data: [53, 20, 10, 80, 100, 45],
            }]
          },
          gradientColors: config.colors.primaryGradient,
          gradientStops: [1, 0.4, 0],
        }
      }
      
    },
    watch: {

            timerCount: {
                handler(value) {

                    if (value > 0) {
                        setTimeout(() => {
                            this.timerCount--;
                        }, 1000);
                    }

                },
                immediate: true 
            }

        }
    ,
    computed: {
      enableRTL() {
        return this.$route.query.enableRTL;
      },
      isRTL() {
        return this.$rtl.isRTL;
      },
      bigLineChartCategories() {
        return this.$t('dashboard.chartCategories');
      }
    }, 
    methods: {
      triggertimer (){
        this.timerCount = 60;
      },
      log(msg, event) {
      console.log(event.target.tagName, msg);
    },
    delegation_name(){
        try {
           var countries_data = sessionStorage.getItem("countries");
        if (countries_data){
          var X = JSON.parse(countries_data);
          
            for (var i = 0; i < X.count; i++) {
              console.log(i)
              if (X.delegations[i].delegation_name){
                console.log("perro")
                this.Contactos.push({nombre:X.delegations[i].delegation_name, URL:X.delegations[i].url});
                
               } else {
            console.log("else")
            this.yo.push({me:X.delegations[i].me, URL:X.delegations[i].url_me})
            }}
          
           
      }
        } catch (error) {
          console.log(error)
        }
       },
      initBigChart(index) {
        let chartData = {
          datasets: [{
            fill: true,
            borderColor: config.colors.primary,
            borderWidth: 2,
            borderDash: [],
            borderDashOffset: 0.0,
            pointBackgroundColor: config.colors.primary,
            pointBorderColor: 'rgba(255,255,255,0)',
            pointHoverBackgroundColor: config.colors.primary,
            pointBorderWidth: 20,
            pointHoverRadius: 4,
            pointHoverBorderWidth: 15,
            pointRadius: 4,
            data: this.bigLineChart.allData[index]
          }],
          labels: ['1st session', '2nd session', '3rd session', '4th session', '5th session', '6th session', '7th session', '8th session', '9th session', '10th session'],
        }
        this.$refs.bigChart.updateGradients(chartData);
        this.bigLineChart.chartData = chartData;
        this.bigLineChart.activeIndex = index;
      }
    },
    mounted() {
      this.i18n = this.$i18n;
      if (this.enableRTL) {
        this.i18n.locale = 'ar';
        this.$rtl.enableRTL();
      }
      this.initBigChart(0);
    },
    beforeDestroy() {
      if (this.$rtl.isRTL) {
        this.i18n.locale = 'en';
        this.$rtl.disableRTL();
      }
    }
  };
</script>
<style>
</style>
