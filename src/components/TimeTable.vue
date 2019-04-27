<template>
  <div>
    <div class="cqv-theaterElement">
        <!-- 영화관리스트 -->
        <div v-if="theaterList.length > 0" class="cqv-theaterPadding">
          
        </div>
    </div>
    <div class="cqv-element cqv-detailPadding" v-if="isShowTimeTable">
      <div v-for="(item, index) in timeTables" v-bind:key="index">
        <strong> {{ item.movieName }} </strong> <br/>

        <strong> {{ item.cinemaHallName }} </strong> <br/>

        <span v-if="item.remain === '매진'"> 
          <del> 
            <span class="cqv-canNotBook"> {{ item.movieTime }} </span> 
          </del> <br/>
          <del> 
            <span class="cqv-canNotBook"> {{ item.remain }} </span>
          </del>
        </span>

        <span v-else-if="item.remain === '마감'">
          <del>
            <span class="cqv-endMovie"> {{ item.movieTime }} </span> <br/>
          </del>
          <del>
            <span class="cqv-endMovie"> {{ item.remain }} </span>
          </del>
        </span>

        <span v-else>
          <span class="cqv-avail"> {{ item.movieTime }} </span> <br/>
          <strong class="cqv-avail"> {{ item.remain }} </strong>
        </span>
        <p/>
      </div>
    </div>
  </div>

</template>

<script>
  import axios from "axios"

  export default {
    data() {
      return {
        theaterList: [],
        timeTables: [],
        isShowTimeTable: false,
      }
    },
    mounted() {
      this.theaterTimeTable()
    },
    methods: {
      theaterList() {

      },
      theaterTimeTable() {
        const url = "http://localhost:3000/timeTables"

        axios.get(url)
          .then((res) => {
            this.timeTables = res.data
          })
      } 
    }
  }
</script>

<style scoped>
  .cqv-theaterElement{
    background-color: lightgray
  }
  .cqv-element {
    background-color: lightblue
  }
  .cqv-canNotBook {
    color: sandybrown
  }
  .cqv-endMovie {
    color: red
  }
  .cqv-avail {
    color: blue
  }
  .cqv-theaterPadding {
    padding: 5% 5% 5% 5%
  }
  .cqv-detailPadding {
    padding: 10% 5% 5% 5%
  }
</style>
