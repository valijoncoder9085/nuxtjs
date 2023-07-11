<template>
  <div>
    <v-app-bar
      :clipped-left="clipped"
      fixed
      app
      elevation="1"
    >
      <v-toolbar-title>
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
      <v-spacer/>
      <div class="lang-div">
        <v-btn class="mr-4" elevation="0" @click="lang_isActive = !lang_isActive">
          <v-img width="20px" class="px-0 mr-2" :src="lang_item[0].icon + '.svg'"></v-img>
          {{ lang_item[0].title }}
        </v-btn>
        <div
          id="ref_lang"
          :class="lang_isActive ? 'active_lang' : '' "
          class="lang_hidden-div elevation-1 rounded-lg"
        >
          <div v-for="(item, idx) in lang_item" :key="idx" @click="clickFunc(item.id)"
               class="d-flex justify-space-between align-center">
          <span>
            <v-img width="20px" :src="'/'+ item.icon + '.svg'"></v-img>
          </span>
            <span>{{ item.title }}</span>
          </div>
        </div>
      </div>
      <v-text-field
        outlined
        style="max-width: 150px;"
        dense
        filled
        placeholder="Search..."
        hide-details
        class="rounded-lg"
        prepend-inner-icon="mdi-magnify"
      />
    </v-app-bar>
    <v-main class="mb-2">
      <v-container>
        <Nuxt/>
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
      lang_isActive: false,
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
      title: 'QQ - Qanday Qilib',
      lang_item: [
        {
          id: 1,
          title: 'UZ',
          icon: 'uz'
        },
        {
          id: 2,
          title: "RU",
          icon: "ru"
        },
        {
          id: 3,
          title: "EN",
          icon: "en"
        }
      ]
    }
  },

  methods: {
    clickFunc(item) {
      console.log(item)
    },
  }
}
</script>

<style lang="scss">
.active_lang-div {
}

.lang-div {
  position: relative;
}

.lang_hidden-div {
  position: absolute;
  width: 80px;
  padding: 10px;
  top: 60px;
  transform: translateX(50px);
  background-color: white;
  opacity: 0;
  transition: all .5s ease-out;
}

.active_lang {
  opacity: 1;
  position: absolute;
  display: block !important;
  background-color: white;
  transform: translateX(0);
}

.active_lang:hover {
  cursor: pointer;
}

li {
  list-style: none;
}
</style>
