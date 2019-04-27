<template>
  <v-container fluid grid-list-md>
    <v-data-iterator
      :items="timeTables"
      :rows-per-page-items="rowsPerPageItems"
      :pagination.sync="pagination"
      content-tag="v-layout"
      row
      wrap
    >
      <template v-slot:item="props">
        <v-flex
          xs12
          sm6
          md4
          lg3
        >
          <v-card>
            <v-card-title><h4>{{ props.item.cinemaHallName }}</h4></v-card-title>
            <v-divider></v-divider>
            <v-list dense>
              <v-list-tile>
                <v-list-tile-content>Movie Time:</v-list-tile-content>
                <v-list-tile-content class="align-end">{{ props.item.movieTime }}</v-list-tile-content>
              </v-list-tile>
              <v-list-tile>
                <v-list-tile-content>Remain Sit:</v-list-tile-content>
                <v-list-tile-content class="align-end">
                  {{ props.item.remain }}
                </v-list-tile-content>
              </v-list-tile>
              <v-list-tile>
                <v-list-tile-content>Date:</v-list-tile-content>
                <v-list-tile-content class="align-end">{{ props.item.targetDate }}</v-list-tile-content>
              </v-list-tile>
            </v-list>
          </v-card>
        </v-flex>
      </template>
    </v-data-iterator>
  </v-container>

</template>

<script>
  import axios from "axios"

  export default {
    data() {
      return {
        timeTables: [],
        rowsPerPageItems: [4, 8, 12],
        pagination: {
          rowsPerPage: 4
        },
      }
    },
    mounted() {
      this.theaterList()
    },
    methods: {
      theaterList() {
        const url = "http://localhost:3000/timeTables"

        axios.get(url)
          .then((res) => {
            this.timeTables = res.data
          })
          // .catch((e) => {
          // })
      }, 
      theaterTimeTable() {

      }
    }
  }
</script>

<style scoped>
  .cqv-element {
    background-color: lightblue
  }
</style>
