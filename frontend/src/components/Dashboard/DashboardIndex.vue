<template>
    <div class="col-12 mt-4 mt-md-3">

        <div class="row stats_area mb-5">
            <div class="col-4">
                <span class="font-6 font-weight-bold d-block">{{$store.getters.services.length}}</span>
                <span class="font-2">Total Services</span>
            </div>
            <div class="col-4">
                <span class="font-6 font-weight-bold d-block">{{failuresLast24Hours()}}</span>
                <span class="font-2">Failures last 24 Hours</span>
            </div>
            <div class="col-4">
                <span class="font-6 font-weight-bold d-block">{{$store.getters.onlineServices(true).length}}</span>
                <span class="font-2">Online Services</span>
            </div>
        </div>

        <div v-for="(service, index) in $store.getters.services" v-bind:key="index">
            <ServiceInfo :service=service />
        </div>
    </div>
</template>

<script>
  import ServiceInfo from "../Service/ServiceInfo";

  export default {
      name: 'DashboardIndex',
      components: {
          ServiceInfo
      },
      methods: {
          failuresLast24Hours() {
              let total = 0;
              this.$store.getters.services.map((s) => {
                  total += s.failures_24_hours
              })
              return total
          },

      }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
