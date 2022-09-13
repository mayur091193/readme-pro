<template>
  <q-layout view="lHh Lpr lFf" style="min-height: unset ;">
<!--    <q-header elevated>-->
<!--      <q-toolbar>-->
<!--        <q-btn-->
<!--          flat-->
<!--          dense-->
<!--          round-->
<!--          icon="menu"-->
<!--          aria-label="Menu"-->
<!--          @click="toggleLeftDrawer"-->
<!--        />-->

<!--        <q-toolbar-title>-->
<!--          Quasar App-->
<!--        </q-toolbar-title>-->

<!--        <div>Quasar v{{ $q.version }}</div>-->
<!--      </q-toolbar>-->
<!--    </q-header>-->






<!--<div class="mx-auto max-w-7xl q-my-sm  md:flex md:items-center md:justify-between md:space-x-5" style="height: 64px !important;">-->
<!--    <div class="flex items-start space-x-5">-->
<!--      <div class="flex-shrink-0">-->
<!--        <div class="relative q-ml-xs cursor-pointer" @click="$router.push({ path: '/' })">-->
<!--          <img class="h-20 q-ml-md q-mt-sm" src="../assets/logo.png" alt="" />-->
<!--        </div>-->
<!--      </div>-->
<!--      &lt;!&ndash;-->
<!--        Use vertical padding to simulate center alignment when both lines of text are one line,-->
<!--        but preserve the same layout if the text wraps without making the image jump around.-->
<!--      &ndash;&gt;-->
<!--      <div class="pt-1.5">-->
<!--&lt;!&ndash;        <h1 class="text-2xl font-bold text-gray-900">Ricardo Cooper</h1>&ndash;&gt;-->
<!--&lt;!&ndash;        <p class="text-sm font-medium text-gray-500">Applied for <a href="#" class="text-gray-900">Front End Developer</a> on <time datetime="2020-08-25">August 25, 2020</time></p>&ndash;&gt;-->
<!--      </div>-->
<!--    </div>-->
<!--    <div class="justify-stretch mt-6 flex flex-col-reverse space-y-4 space-y-reverse sm:flex-row-reverse sm:justify-end sm:space-y-0 sm:space-x-3 sm:space-x-reverse md:mt-0 md:flex-row md:space-x-3">-->
<!--&lt;!&ndash;      <button type="button" class="inline-flex items-center justify-center rounded-md border border-gray-300 bg-white px-4 py-2 text-sm font-medium text-gray-700 shadow-sm hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2 focus:ring-offset-gray-100">Disqualify</button>&ndash;&gt;-->
<!--&lt;!&ndash;      <button type="button" class="inline-flex items-center justify-center rounded-md border border-transparent bg-indigo-600 px-4 py-2 text-sm font-medium text-white shadow-sm hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2 focus:ring-offset-gray-100">Advance to offer</button>&ndash;&gt;-->
<!--          <div class="border-r-2 q-pr-lg inline-flex items-center justify-center"><a class="text-weight-bold text-h6 text-indigo-600 hover:text-indigo-500" target="_blank" href="https://github.com/mayur091193/q-google-map" style="text-decoration: none;">Report Issue</a></div>-->
<!--          <div class="border-r-2 q-pr-lg q-pl-md inline-flex items-center justify-center"><a class="text-weight-bold text-h6 text-indigo-600 hover:text-indigo-500" target="_blank" href="https://github.com/sponsors/mayur091193" style="text-decoration: none;">Donate</a></div>-->
<!--          <div class="q-pl-md inline-flex items-center justify-center"><a target="_blank" href="https://github.com/mayur091193/q-google-map" class="text-h6 text-indigo-600 hover:text-indigo-500" style="text-decoration: none; "><i aria-hidden="true" role="presentation" class="cursor-pointer fab fa-github q-icon notranslate" style="font-size: 25px;"> &lt;!&ndash;&ndash;&gt;</i></a></div>-->
<!--    </div>-->
<!--  </div>-->
    <q-page-container>
      <router-view />
    </q-page-container>

  </q-layout>
</template>

<script>
import EssentialLink from 'components/EssentialLink.vue'

const linksList = [
  {
    title: 'Docs',
    caption: 'quasar.dev',
    icon: 'school',
    link: 'https://quasar.dev'
  },
  {
    title: 'Github',
    caption: 'github.com/quasarframework',
    icon: 'code',
    link: 'https://github.com/quasarframework'
  },
  {
    title: 'Discord Chat Channel',
    caption: 'chat.quasar.dev',
    icon: 'chat',
    link: 'https://chat.quasar.dev'
  },
  {
    title: 'Forum',
    caption: 'forum.quasar.dev',
    icon: 'record_voice_over',
    link: 'https://forum.quasar.dev'
  },
  {
    title: 'Twitter',
    caption: '@quasarframework',
    icon: 'rss_feed',
    link: 'https://twitter.quasar.dev'
  },
  {
    title: 'Facebook',
    caption: '@QuasarFramework',
    icon: 'public',
    link: 'https://facebook.quasar.dev'
  },
  {
    title: 'Quasar Awesome',
    caption: 'Community Quasar projects',
    icon: 'favorite',
    link: 'https://awesome.quasar.dev'
  }
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
