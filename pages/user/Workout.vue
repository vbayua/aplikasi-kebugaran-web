<template>
  <div id="wrapper">
    <app-sidebar />
    <div id="content-wrapper" class="d-flex flex-column">
      <div id="content">
        <app-navbartop />
        <app-card :workouts="workouts" />
      </div>
      <footer class="sticky-footer bg-white">
        <div class="container my-auto">
          <div class="copyright text-center my-auto">
            <span>Copyright &copy; AksiKalistenik 2021</span>
          </div>
        </div>
      </footer>
    </div>
  </div>
</template>
<script>
import Sidebar from '@/components/Dashboard/Sidebar.vue'
import NavbarTop from '@/components/Dashboard/NavbarTop.vue'
import Card from '~/components/Dashboard/Workouts/Card.vue'

export default {
  components: {
    'app-sidebar': Sidebar,
    'app-navbartop': NavbarTop,
    'app-card': Card
  },

  async asyncData (context) {
    const { data } = await context.$axios.get('/api/workout-data')
    return {
      workouts: data
    }
  }
}
</script>
