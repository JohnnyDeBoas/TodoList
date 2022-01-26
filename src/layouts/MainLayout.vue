<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title>
          Todo List 
        </q-toolbar-title>
      <div>João Lucas</div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      bordered
    >
      <q-list>
        <q-item-label
          header
        >
          Menu
        </q-item-label>

        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import EssentialLink from 'components/EssentialLink.vue'

const linksList = [
  {
    title: 'Linkedin',
    caption: 'João Lucas',
    icon: 'fab fa-linkedin',
    link: 'https://www.linkedin.com/in/joao-lucas-johnnydeboas/'
  },
  {
    title: 'Github',
    caption: 'github.com/JohnnyDeBoas',
    icon: 'fab fa-github',
    link: 'https://github.com/JohnnyDeBoas'
  },
  {
    title: 'Whatsapp',
    caption: '(12) 99795-7774',
    color: 'green',
    icon: 'fab fa-whatsapp',
    link: 'https://api.whatsapp.com/send?phone=5512997957774'
  },
  
];

import { defineComponent, ref } from 'vue'

export default defineComponent({
  name: 'MainLayout',

  components: {
    EssentialLink
  },

  setup () {
    const leftDrawerOpen = ref(false)

    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  }
})
</script>
