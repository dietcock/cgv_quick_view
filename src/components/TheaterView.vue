<template>
  <div> 
    <!-- 영화고나 목록 -->
    <div>
      <v-content>
        <!-- 시간표 정보 -->
        <TimeTable/>
      </v-content>
    </div>
  </div>

</template>

<script>
import TimeTable from './components/TimeTable'

export default {
  data() {
    return {
      regionList: [],
      theaterList: []
    }
  },
  components: {
    TimeTable
  },
  mounted() {
    // this.theaterList()
  },
  method: {
    theaterList() {

    }
  }
}
</script>

