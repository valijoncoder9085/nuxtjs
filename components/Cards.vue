<template>
  <div>
    <v-row>
      <v-col cols="12" md="4" lg="3" sm="6" v-for="item in items" :key="item.id">
        <v-hover
          v-slot="{hover}"
          open-delay="200"
        >
          <v-card :elevation="hover ? 16 : 2" class="rounded-lg" min-height="250px">
            <v-card-title class="pa-0">
              <v-img class="rounded-t-lg" :src="item.url" height="200px"/>
            </v-card-title>
            <v-card-actions>
              {{ item.title | capitalize }}
            </v-card-actions>
            <v-card-text>
              <span class="text--accent-1">21.20.2101</span>
              <v-spacer></v-spacer>
              <span>view: prosmotr</span>
            </v-card-text>
          </v-card>
        </v-hover>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  name: "CardPage",
  data() {
    return {
      items: []
    }
  },
  filters: {
    capitalize(val) {
      return val.toLowerCase()
    }
  },
  async mounted() {
    await this.$axios.get('https://jsonplaceholder.typicode.com/photos?_limit=10')
      .then(res => {
        this.items = res.data
      })
      .catch(({response}) => {
        console.log(response)
      })
  }
}
</script>

<style lang="scss" scoped>

</style>
