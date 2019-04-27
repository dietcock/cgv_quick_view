<template>
  <v-app>
    <v-toolbar app>
      <v-toolbar-title class="headline text-uppercase">
        <h2>CGV QUICK VIEW FOR TIMETABLE</h2>
      </v-toolbar-title>
      <v-spacer></v-spacer>
    </v-toolbar>

    <v-content>
      <TimeTable/>
    </v-content>
  </v-app>
</template>

<script>
import TimeTable from './components/TimeTable'

export default {
  name: 'App',
  components: {
    TimeTable
  },
  data () {
    return {
      //
    }
  }
}
</script>

