<template>
  <div>
    <v-app-bar
      :clipped-left="clipped"
      fixed
      app
      elevation="1"
    >
      <v-toolbar-title class="container">
        {{ title }}
      </v-toolbar-title>
      <v-spacer/>
      <v-list class="d-flex">
        <v-list-item
          v-for="(item, idx) in items"
          :key="idx"
        >
          <v-list-item-content>
            <NuxtLink :to="item.to">{{ item.title }}</NuxtLink>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-app-bar>
    <v-main>
      <v-container>
        <v-card class="my-3 pa-3 elevation-0 rounded-lg" min-height="1000px" color="#ECEFF1">
          <v-card-title>
            <Nuxt/>
          </v-card-title>
        </v-card>
      </v-container>
    </v-main>
    <v-footer
      dark
      absolute
      app
      min-height="100px"
    >
      <v-spacer/>
      <h1>Footer</h1>
      <v-spacer/>
    </v-footer>
  </div>
</template>

<script>
import('~/assets/sidebar.scss')
export default {
  name: "SidebarPage",
  data() {
    return {
      clipped: false,
      items: [
        {
          title: 'Home',
          to: '/home'
        },
        {
          title: 'About',
          to: '/about'
        }
      ],
      title: 'QQ - Qanday Qilib'
    }
  }
}
</script>

<style lang="scss">
</style>
