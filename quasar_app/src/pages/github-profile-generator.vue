<template>

  <!--
  This example requires Tailwind CSS v2.0+

  This example requires some changes to your config:

  ```
  // tailwind.config.js
  module.exports = {
    // ...
    plugins: [
      // ...
      require('@tailwindcss/forms'),
    ],
  }
  ```
-->
  <div class="min-h-screen bg-gray-100">
    <!--
      When the mobile menu is open, add `overflow-hidden` to the `body` element to prevent double scrollbars

      Open: "fixed inset-0 z-40 overflow-y-auto", Closed: ""
    -->
    <header class="bg-white shadow-sm lg:static lg:overflow-y-visible">
      <div class="mx-auto q-px-xl">
        <div class="relative flex justify-between lg:gap-8 xl:grid xl:grid-cols-12">
          <div class="flex md:absolute md:inset-y-0 md:left-0 lg:static xl:col-span-2">
            <div class="flex flex-shrink-0 items-center">
              <a href="#">
                <img class="" style="height: 45px;" src="../assets/logo.png" alt=""/>
              </a>
            </div>
          </div>
          <div class="min-w-0 flex-1 md:px-8 lg:px-0 xl:col-span-1">
            <div class="flex items-center px-6 py-4 md:mx-auto md:max-w-3xl lg:mx-0 lg:max-w-none xl:px-0">
              <div class="w-full">
                <label for="search" class="sr-only">Search</label>
                <div class="relative">
                  <div class="pointer-events-none absolute inset-y-0 left-0 flex items-center pl-3 invisible">
                    <!-- Heroicon name: mini/magnifying-glass -->
                    <svg class="h-5 w-5 text-gray-400" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"
                         fill="currentColor" aria-hidden="true">
                      <path fill-rule="evenodd"
                            d="M9 3.5a5.5 5.5 0 100 11 5.5 5.5 0 000-11zM2 9a7 7 0 1112.452 4.391l3.328 3.329a.75.75 0 11-1.06 1.06l-3.329-3.328A7 7 0 012 9z"
                            clip-rule="evenodd"/>
                    </svg>
                  </div>
                  <input id="search" name="search"
                         class="block invisible w-full rounded-md border border-gray-300 bg-white py-2 pl-10 pr-3 text-sm placeholder-gray-500 focus:border-indigo-500 focus:text-gray-900 focus:placeholder-gray-400 focus:outline-none focus:ring-1 focus:ring-indigo-500 sm:text-sm"
                         placeholder="Search" type="search">
                </div>
              </div>
            </div>
          </div>

          <div class=" lg:flex lg:items-center lg:justify-end xl:col-span-9">

            <!-- Profile dropdown -->
            <div class="border-r-2 q-pr-md cursor-pointer"><a
              class="text-weight-bold text-body1 text-indigo-600 hover:text-indigo-500" target="_blank"
              @click="$router.push({ path: '/main' })" style="text-decoration: none;">
              Readme Generator</a></div>
            <div class="border-r-2 q-pl-md q-pr-md ">
              <a
                class="text-weight-bold text-body1 text-indigo-600 hover:text-indigo-500" target="_blank"
                href="https://github.com/mayur091193/readme-pro" style="text-decoration: none;">
                <q-icon name="star" color="yellow-10" size="23px" class="q-mr-xs q-mb-xs"/>
                Star this Repo!</a>

              <!--              <iframe class="float-right"-->
              <!--                        src="https://ghbtns.com/github-btn.html?user=mayank091193&repo=quasar-draggable-tree&type=star&count=true&size=large"-->
              <!--                        frameborder="0" scrolling="0" width="136" height="30" title="GitHub"></iframe>-->
            </div>

            <div class="border-r-2 q-pl-md q-pr-md "><a
              class="text-weight-bold text-body1 text-indigo-600 hover:text-indigo-500" target="_blank"
              href="https://github.com/mayur091193/readme-pro/issues" style="text-decoration: none;">Report Issue</a>
            </div>
            <div class="border-r-2 q-pl-md q-pr-md "><a
              class="text-weight-bold text-body1 text-indigo-600 hover:text-indigo-500" target="_blank"
              href="https://github.com/sponsors/mayur091193" style="text-decoration: none;">Support</a></div>
            <div class="q-px-md border-r-2"><a target="_blank" href="https://github.com/mayur091193/readme-pro"
                                                       class="text-h6 text-indigo-600 hover:text-indigo-500"
                                                       style="text-decoration: none; "><i aria-hidden="true"
                                                                                          role="presentation"
                                                                                          class="cursor-pointer q-mb-xs fab fa-github q-icon notranslate"
                                                                                          style="font-size: 25px;">
              <!----></i></a></div>

            <div class="rounded-md shadow q-ml-md">
              <a @click="view_modal=true;generateProfile('')"
                 class="cursor-pointer flex w-full items-center justify-center rounded-md border border-transparent bg-indigo-600 px-4 py-2 text-base font-medium text-white hover:bg-indigo-700 md:text-lg">
                <q-icon class="q-mr-sm" name="visibility"/>
                View</a>
            </div>


          </div>
        </div>
      </div>

    </header>

    <div class="py-5" :style="{'height':available_height}">
      <div class=" lg:grid  lg:grid-cols-12 lg:gap-4 q-pr-xl" :style="{'height':available_height}">
        <div class=" col-span-4 q-pl-xl">
          <div class="sticky top-6  bg-white space-y-4 border-2"
               :style="{'height':available_height,'min-height':available_height}" style="overflow-y: auto">
            <!-- Your content -->

            <div class="">
              <!-- Sidebar component, swap this element with another sidebar if you like -->
              <nav class="flex flex-grow flex-col overflow-y-auto pt-5 pb-4">
                <div class="flex flex-shrink-0 items-center px-4">
                  <div class="text-weight-bold text-h6 text-purple-600">
                    GitHub Profile README Generator
                  </div>
                </div>
                <div class="mt-5 flex-grow border-t-2 q-pt-sm">
                  <div class="space-y-1">
                    <!-- Current: "bg-purple-50 border-purple-600 text-purple-600", Default: "border-transparent text-gray-600 text-weight-bold hover:text-gray-900 hover:bg-gray-50" -->
                    <a @click="selected_tab='Basic Information'"
                       :class="selected_tab==='Basic Information' ? 'bg-purple-50 border-purple-600 text-purple-600 group' : ''"
                       class="border-l-4 border-transparent text-gray-600 text-weight-bold hover:text-gray-900 hover:bg-gray-50 group border-l-4 py-2 px-3 flex items-center cursor-pointer ">
                      Basic Information
                    </a>
                    <a @click="selected_tab='Work Details'"
                       :class="selected_tab==='Work Details' ? 'bg-purple-50 border-purple-600 text-purple-600 group' : ''"
                       class="border-l-4 border-transparent text-gray-600 text-weight-bold hover:text-gray-900 hover:bg-gray-50 group border-l-4 py-2 px-3 flex items-center cursor-pointer ">
                      Work Details
                    </a>
                    <a @click="selected_tab='Social(Tech)'"
                       :class="selected_tab==='Social(Tech)' ? 'bg-purple-50 border-purple-600 text-purple-600 group' : ''"
                       class="border-l-4 border-transparent text-gray-600 text-weight-bold hover:text-gray-900 hover:bg-gray-50 group border-l-4 py-2 px-3 flex items-center cursor-pointer ">
                      Social(Tech)
                    </a>
                    <a @click="selected_tab='Programming Languages'"
                       :class="selected_tab==='Programming Languages' ? 'bg-purple-50 border-purple-600 text-purple-600 group' : ''"
                       class="border-l-4 border-transparent text-gray-600 text-weight-bold hover:text-gray-900 hover:bg-gray-50 group border-l-4 py-2 px-3 flex items-center cursor-pointer ">
                      Programming Languages
                      <span
                        class="bg-purple-200 text-indigo-600 ml-3 py-0.5 px-2.5 rounded-full text-xs font-medium md:inline-block"
                        v-if="all_data.selected_prog_techs.length > 0">
                        {{ all_data.selected_prog_techs.length }} &nbsp; selected
                      </span>
                    </a>
                    <a @click="selected_tab='Frontend Technologies'"
                       :class="selected_tab==='Frontend Technologies' ? 'bg-purple-50 border-purple-600 text-purple-600 group' : ''"
                       class="border-l-4 border-transparent text-gray-600 text-weight-bold hover:text-gray-900 hover:bg-gray-50 group border-l-4 py-2 px-3 flex items-center cursor-pointer ">
                      Frontend Technologies
                      <span
                        class="bg-purple-200 text-indigo-600 ml-3 py-0.5 px-2.5 rounded-full text-xs font-medium md:inline-block"
                        v-if="all_data.selected_frontend_techs.length > 0">
                        {{ all_data.selected_frontend_techs.length }} &nbsp; selected
                      </span>
                    </a>
                    <a @click="selected_tab='Backend Technologies'"
                       :class="selected_tab==='Backend Technologies' ? 'bg-purple-50 border-purple-600 text-purple-600 group' : ''"
                       class="border-l-4 border-transparent text-gray-600 text-weight-bold hover:text-gray-900 hover:bg-gray-50 group border-l-4 py-2 px-3 flex items-center cursor-pointer ">
                      Backend Technologies
                      <span
                        class="bg-purple-200 text-indigo-600 ml-3 py-0.5 px-2.5 rounded-full text-xs font-medium md:inline-block"
                        v-if="all_data.selected_backend_techs.length > 0">
                        {{ all_data.selected_backend_techs.length }} &nbsp; selected
                      </span>
                    </a>
                    <a @click="selected_tab='Mobile App Technologies'"
                       :class="selected_tab==='Mobile App Technologies' ? 'bg-purple-50 border-purple-600 text-purple-600 group' : ''"
                       class="border-l-4 border-transparent text-gray-600 text-weight-bold hover:text-gray-900 hover:bg-gray-50 group border-l-4 py-2 px-3 flex items-center cursor-pointer ">
                      Mobile App Technologies
                      <span
                        class="bg-purple-200 text-indigo-600 ml-3 py-0.5 px-2.5 rounded-full text-xs font-medium md:inline-block"
                        v-if="all_data.selected_mobileapp_techs.length > 0">
                        {{ all_data.selected_mobileapp_techs.length }} &nbsp; selected
                      </span>
                    </a>
                    <a @click="selected_tab='AI/ML'"
                       :class="selected_tab==='AI/ML' ? 'bg-purple-50 border-purple-600 text-purple-600 group' : ''"
                       class="border-l-4 border-transparent text-gray-600 text-weight-bold hover:text-gray-900 hover:bg-gray-50 group border-l-4 py-2 px-3 flex items-center cursor-pointer ">
                      AI/ML
                      <span
                        class="bg-purple-200 text-indigo-600 ml-3 py-0.5 px-2.5 rounded-full text-xs font-medium md:inline-block"
                        v-if="all_data.selected_aiml_techs.length > 0">
                        {{ all_data.selected_aiml_techs.length }} &nbsp; selected
                      </span>
                    </a>
                    <a @click="selected_tab='Database'"
                       :class="selected_tab==='Database' ? 'bg-purple-50 border-purple-600 text-purple-600 group' : ''"
                       class="border-l-4 border-transparent text-gray-600 text-weight-bold hover:text-gray-900 hover:bg-gray-50 group border-l-4 py-2 px-3 flex items-center cursor-pointer ">
                      Database
                      <span
                        class="bg-purple-200 text-indigo-600 ml-3 py-0.5 px-2.5 rounded-full text-xs font-medium md:inline-block"
                        v-if="all_data.selected_database_techs.length > 0">
                        {{ all_data.selected_database_techs.length }} &nbsp; selected
                      </span>
                    </a>
                    <a @click="selected_tab='Devops'"
                       :class="selected_tab==='Devops' ? 'bg-purple-50 border-purple-600 text-purple-600 group' : ''"
                       class="border-l-4 border-transparent text-gray-600 text-weight-bold hover:text-gray-900 hover:bg-gray-50 group border-l-4 py-2 px-3 flex items-center cursor-pointer ">
                      Devops
                      <span
                        class="bg-purple-200 text-indigo-600 ml-3 py-0.5 px-2.5 rounded-full text-xs font-medium md:inline-block"
                        v-if="all_data.selected_devops_techs.length > 0">
                        {{ all_data.selected_devops_techs.length }} &nbsp; selected
                      </span>
                    </a>
                    <a @click="selected_tab='Static Site Generator'"
                       :class="selected_tab==='Static Site Generator' ? 'bg-purple-50 border-purple-600 text-purple-600 group' : ''"
                       class="border-l-4 border-transparent text-gray-600 text-weight-bold hover:text-gray-900 hover:bg-gray-50 group border-l-4 py-2 px-3 flex items-center cursor-pointer ">
                      Static Site Generator
                      <span
                        class="bg-purple-200 text-indigo-600 ml-3 py-0.5 px-2.5 rounded-full text-xs font-medium md:inline-block"
                        v-if="all_data.selected_staticsitegenerator_techs.length > 0">
                        {{ all_data.selected_staticsitegenerator_techs.length }} &nbsp; selected
                      </span>
                    </a>
                    <a @click="selected_tab='Gaming'"
                       :class="selected_tab==='Gaming' ? 'bg-purple-50 border-purple-600 text-purple-600 group' : ''"
                       class="border-l-4 border-transparent text-gray-600 text-weight-bold hover:text-gray-900 hover:bg-gray-50 group border-l-4 py-2 px-3 flex items-center cursor-pointer ">
                      Gaming
                      <span
                        class="bg-purple-200 text-indigo-600 ml-3 py-0.5 px-2.5 rounded-full text-xs font-medium md:inline-block"
                        v-if="all_data.selected_gaming_techs.length > 0">
                        {{ all_data.selected_gaming_techs.length }} &nbsp; selected
                      </span>
                    </a>
                  </div>
                </div>

              </nav>
            </div>

          </div>
        </div>
        <main class="col-span-8 bg-white border-2">

          <div class="q-py-md q-px-lg">

            <div class="text-purple-500 text-h6 text-weight-bold"> {{ selected_tab }}</div>

            <div v-if="selected_tab==='Basic Information'">
              <div class="q-mt-lg">
                <div class="row">
                  <div class="col-4">
                    <div class="text-subtitle1">Title</div>
                    <q-input v-model="all_data.title" stack-label/>
                  </div>
                  <div class="col-8 q-pl-md">
                    <div class="text-subtitle1 invisible">Title</div>
                    <q-input v-model="all_data.name" stack-label/>
                  </div>
                </div>
                <div class="row q-mt-xl">
                  <div class="col-12">
                    <div class="text-subtitle1">Description</div>
                    <q-input v-model="all_data.description" stack-label/>
                  </div>
                </div>
              </div>
            </div>

            <div v-if="selected_tab==='Work Details'">
              <div class="q-mt-md">
                <div class="row">
                  <div class="col-5">
                    <q-input v-model="all_data.work_line_1_label" stack-label/>
                  </div>
                  <div class="col-7 q-pl-md">
                    <q-input v-model="all_data.work_line_1_value" stack-label/>
                  </div>
                </div>

                <div class="row">
                  <div class="col-5">
                    <q-input v-model="all_data.work_line_2_label" stack-label/>
                  </div>
                  <div class="col-7 q-pl-md">
                    <q-input v-model="all_data.work_line_2_value" stack-label/>
                  </div>
                </div>

                <div class="row">
                  <div class="col-5">
                    <q-input v-model="all_data.work_line_3_label" stack-label/>
                  </div>
                  <div class="col-7 q-pl-md">
                    <q-input v-model="all_data.work_line_3_value" stack-label/>
                  </div>
                </div>

                <div class="row">
                  <div class="col-5">
                    <q-input v-model="all_data.work_line_4_label" stack-label/>
                  </div>
                  <div class="col-7 q-pl-md">
                    <q-input v-model="all_data.work_line_4_value" stack-label/>
                  </div>
                </div>

                <div class="row">
                  <div class="col-5">
                    <q-input v-model="all_data.work_line_5_label" stack-label/>
                  </div>
                  <div class="col-7 q-pl-md">
                    <q-input v-model="all_data.work_line_5_value" stack-label/>
                  </div>
                </div>

                <div class="row">
                  <div class="col-5">
                    <q-input v-model="all_data.work_line_6_label" stack-label/>
                  </div>
                  <div class="col-7 q-pl-md">
                    <q-input v-model="all_data.work_line_6_value" stack-label/>
                  </div>
                </div>

                <div class="row">
                  <div class="col-5">
                    <q-input v-model="all_data.work_line_7_label" stack-label/>
                  </div>
                  <div class="col-7 q-pl-md">
                    <q-input v-model="all_data.work_line_7_value" stack-label/>
                  </div>
                </div>

                <div class="row">
                  <div class="col-5">
                    <q-input v-model="all_data.work_line_8_label" stack-label/>
                  </div>
                  <div class="col-7 q-pl-md">
                    <q-input v-model="all_data.work_line_8_value" stack-label/>
                  </div>
                </div>

              </div>
            </div>

            <div v-if="selected_tab==='Social(Tech)'">
              <div class="q-mt-lg">

                <div class="row">
                  <div class="col-4 q-pr-md">
                    <q-input v-model="all_data.github_username" placeholder="Github Username">
                      <template v-slot:prepend>
                        <q-avatar square>
                          <img src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/github.svg">
                        </q-avatar>
                      </template>
                    </q-input>
                  </div>
                  <div class="col-4 q-px-md">
                    <q-input v-model="all_data.devdotto_username" placeholder="Dev.to Username">
                      <template v-slot:prepend>
                        <q-avatar square>
                          <img src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/dev-dot-to.svg">
                        </q-avatar>
                      </template>
                    </q-input>
                  </div>
                  <div class="col-4 q-px-md">
                    <q-input v-model="all_data.twitter_username" placeholder="Twitter Username">
                      <template v-slot:prepend>
                        <q-avatar square>
                          <img src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/twitter.svg">
                        </q-avatar>
                      </template>
                    </q-input>
                  </div>
                </div>

                <div class="row q-mt-lg">
                  <div class="col-4 q-pr-md">
                    <q-input v-model="all_data.codepen_username" placeholder="Codepen Username">
                      <template v-slot:prepend>
                        <q-avatar square>
                          <img src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/codepen.svg">
                        </q-avatar>
                      </template>
                    </q-input>
                  </div>
                  <div class="col-4 q-px-md">
                    <q-input v-model="all_data.reddit_username" placeholder="Reddit Username">
                      <template v-slot:prepend>
                        <q-avatar square>
                          <img src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/reddit.svg">
                        </q-avatar>
                      </template>
                    </q-input>
                  </div>
                  <div class="col-4 q-px-md">
                    <q-input v-model="all_data.stackoverflow_username" placeholder="Stackoverflow User ID">
                      <template v-slot:prepend>
                        <q-avatar square>
                          <img src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/stackoverflow.svg">
                        </q-avatar>
                      </template>
                    </q-input>
                  </div>
                </div>

                <div class="row q-mt-lg">
                  <div class="col-4 q-pr-md">
                    <q-input v-model="all_data.linkdin_username" placeholder="LinkedIn Username">
                      <template v-slot:prepend>
                        <q-avatar square>
                          <img src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/linkedin.svg">
                        </q-avatar>
                      </template>
                    </q-input>
                  </div>
                  <div class="col-4 q-px-md">
                    <q-input v-model="all_data.medium_username" placeholder="Medium Username">
                      <template v-slot:prepend>
                        <q-avatar square>
                          <img src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/medium.svg">
                        </q-avatar>
                      </template>
                    </q-input>
                  </div>
                  <div class="col-4 q-px-md">
                    <q-input v-model="all_data.hackerearth_username" placeholder="HackerEarth Username">
                      <template v-slot:prepend>
                        <q-avatar square>
                          <img src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/hackerearth.svg">
                        </q-avatar>
                      </template>
                    </q-input>
                  </div>
                </div>

                <div class="row q-mt-lg">
                  <div class="col-4 q-pr-md">
                    <q-input v-model="all_data.youtube_username" placeholder="YouTube Channel Name">
                      <template v-slot:prepend>
                        <q-avatar square>
                          <img src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/youtube.svg">
                        </q-avatar>
                      </template>
                    </q-input>
                  </div>
                  <div class="col-4 q-px-md">
                    <q-input v-model="all_data.instagram_username" placeholder="Instagram Username">
                      <template v-slot:prepend>
                        <q-avatar square>
                          <img src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/instagram.svg">
                        </q-avatar>
                      </template>
                    </q-input>
                  </div>
                  <div class="col-4 q-px-md">
                    <q-input v-model="all_data.facebook_username" placeholder="Facebook Username">
                      <template v-slot:prepend>
                        <q-avatar square>
                          <img src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/facebook.svg">
                        </q-avatar>
                      </template>
                    </q-input>
                  </div>
                </div>

              </div>
            </div>

            <div v-if="selected_tab==='Programming Languages'">
              <div class="q-mt-sm">
                <div class="row">
                  <div class="col-3 q-mt-md" v-for="item in all_prog_tech">
                    <q-checkbox class="q-mb-xs" v-model="all_data.selected_prog_techs" :val="item.value" color="teal"/>
                    <img class="q-mb-xs q-pl-sm" style="height: 25px;display: inline-block"
                         :src="item.icons">
                    <span class="q-pl-md text-subtitle1">{{ item.text }}</span>
                  </div>
                </div>
              </div>
            </div>

            <div v-if="selected_tab==='Frontend Technologies'">
              <div class="q-mt-sm">
                <div class="row">
                  <div class="col-3 q-mt-md" v-for="item in all_frontend_tech">
                    <q-checkbox class="q-mb-xs" v-model="all_data.selected_frontend_techs" :val="item.value"
                                color="teal"/>
                    <img class="q-mb-xs q-pl-sm" style="height: 25px;display: inline-block"
                         :src="item.icons">
                    <span class="q-pl-md text-subtitle1">{{ item.text }}</span>
                  </div>
                </div>
              </div>
            </div>

            <div v-if="selected_tab==='Backend Technologies'">
              <div class="q-mt-sm">
                <div class="row">
                  <div class="col-3 q-mt-md" v-for="item in all_backend_tech">
                    <q-checkbox class="q-mb-xs" v-model="all_data.selected_backend_techs" :val="item.value"
                                color="teal"/>
                    <img class="q-mb-xs q-pl-sm" style="height: 25px;display: inline-block"
                         :src="item.icons">
                    <span class="q-pl-md text-subtitle1">{{ item.text }}</span>
                  </div>
                </div>
              </div>
            </div>

            <div v-if="selected_tab==='Mobile App Technologies'">
              <div class="q-mt-sm">
                <div class="row">
                  <div class="col-3 q-mt-md" v-for="item in all_mobile_tech">
                    <q-checkbox class="q-mb-xs" v-model="all_data.selected_mobileapp_techs" :val="item.value"
                                color="teal"/>
                    <img class="q-mb-xs q-pl-sm" style="height: 25px;display: inline-block"
                         :src="item.icons">
                    <span class="q-pl-md text-subtitle1">{{ item.text }}</span>
                  </div>
                </div>
              </div>
            </div>

            <div v-if="selected_tab==='AI/ML'">
              <div class="q-mt-sm">
                <div class="row">
                  <div class="col-3 q-mt-md" v-for="item in all_ai_ml_tech">
                    <q-checkbox class="q-mb-xs" v-model="all_data.selected_aiml_techs" :val="item.value" color="teal"/>
                    <img class="q-mb-xs q-pl-sm" style="height: 25px;display: inline-block"
                         :src="item.icons">
                    <span class="q-pl-md text-subtitle1">{{ item.text }}</span>
                  </div>
                </div>
              </div>
            </div>
            <div v-if="selected_tab==='Database'">
              <div class="q-mt-sm">
                <div class="row">
                  <div class="col-3 q-mt-md" v-for="item in all_database_tech">
                    <q-checkbox class="q-mb-xs" v-model="all_data.selected_database_techs" :val="item.value"
                                color="teal"/>
                    <img class="q-mb-xs q-pl-sm" style="height: 25px;display: inline-block"
                         :src="item.icons">
                    <span class="q-pl-md text-subtitle1">{{ item.text }}</span>
                  </div>
                </div>
              </div>
            </div>
            <div v-if="selected_tab==='Devops'">
              <div class="q-mt-sm">
                <div class="row">
                  <div class="col-3 q-mt-md" v-for="item in all_devops_tech">
                    <q-checkbox class="q-mb-xs" v-model="all_data.selected_devops_techs" :val="item.value"
                                color="teal"/>
                    <img class="q-mb-xs q-pl-sm" style="height: 25px;display: inline-block"
                         :src="item.icons">
                    <span class="q-pl-md text-subtitle1">{{ item.text }}</span>
                  </div>
                </div>
              </div>
            </div>
            <div v-if="selected_tab==='Static Site Generator'">
              <div class="q-mt-sm">
                <div class="row">
                  <div class="col-3 q-mt-md" v-for="item in all_static_site_generator_tech">
                    <q-checkbox class="q-mb-xs" v-model="all_data.selected_staticsitegenerator_techs" :val="item.value"
                                color="teal"/>
                    <img class="q-mb-xs q-pl-sm" style="height: 25px;display: inline-block"
                         :src="item.icons">
                    <span class="q-pl-md text-subtitle1">{{ item.text }}</span>
                  </div>
                </div>
              </div>
            </div>
            <div v-if="selected_tab==='Gaming'">
              <div class="q-mt-sm">
                <div class="row">
                  <div class="col-3 q-mt-md" v-for="item in all_gaming_tech">
                    <q-checkbox class="q-mb-xs" v-model="all_data.selected_gaming_techs" :val="item.value"
                                color="teal"/>
                    <img class="q-mb-xs q-pl-sm" style="height: 25px;display: inline-block"
                         :src="item.icons">
                    <span class="q-pl-md text-subtitle1">{{ item.text }}</span>
                  </div>
                </div>
              </div>
            </div>

          </div>
        </main>
      </div>
    </div>
  </div>


  <q-dialog
    v-model="view_modal"
    persistent
    :maximized="true"
    transition-show="slide-up"
    transition-hide="slide-down"
  >
    <q-card class=" text-white q-mb-xl">
      <q-bar class="bg-purple-600">
        <q-space/>
        <q-btn dense flat icon="close" v-close-popup>
          <q-tooltip class="bg-white text-primary">Close</q-tooltip>
        </q-btn>
      </q-bar>


      <q-card-section style="border-bottom: 1px solid lightgrey;">
        <div class="row">
          <div class="col-4 text-subtitle1 text-purple-600 text-capitalize text-weight-bold q-pt-xs">Your GitHUb profile
            will look like below:
          </div>
          <div class="col-8">
              <span class="isolate float-right rounded-md ">
<!--                <q-btn class="q-ml-md text-capitalize text-weight-bold" outline color="purple-500" label="Template 1"/>-->
<!--                <q-btn class="q-ml-md text-capitalize text-weight-bold" outline color="grey-8" label="Template 2"/>-->
<!--                <q-btn class="q-ml-md text-capitalize text-weight-bold" outline color="grey-8" label="Template 3"/>-->

                <a @click="copyMarkdownCode"
        class="cursor-pointer z-max q-ml-md items-center text-weight-bold justify-center rounded-md border border-transparent bg-green-7 px-4 py-2 text-base text-subtitle2 text-white hover:bg-indigo-700 ">
      <q-icon class="q-mr-sm" name="content_copy"/>
      Copy Markdown</a>
              </span>
          </div>
        </div>
      </q-card-section>
      <q-card-section>
        <div class="q-px-xl">
          <div class="row">
            <div class="col-4 q-pl-xl q-pr-xl">
              <div class="text-black">
                <img class=" h-64 w-64 q-ml-lg q-pl-sm flex-shrink-0 rounded-full"
                     src="https://avatars.githubusercontent.com/u/55240045?v=4" alt="">
                <div class="text-weight-bold text-h5 q-mt-lg">Mayur Patel</div>
                <div class="text-grey-7 text-h6">mayur091193</div>
                <div class="text-subtitle1 q-mt-md">Open for remote work | 7+ years of experience in IT field</div>
                <q-btn dense disable outline
                       class="q-mt-md bg-grey-2 full-width text-black text-capitalize text-weight-bold"
                       label="Edit Profile"/>
                <q-btn dense disable outline
                       class="q-mt-sm bg-grey-2 full-width text-black text-capitalize text-weight-bold"
                       label="Sponsor dashboard"/>

                <div class="flex-order-1 flex-md-order-none mt-2 mt-md-0">
                  <div class="mb-3 q-mt-md">
                    <a class="Link--secondary no-underline no-wrap">
                      <svg style="float: left;margin-top: 3px;margin-right: 5px;" text="muted" aria-hidden="true"
                           height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true"
                           class="octicon octicon-people">
                        <path fill-rule="evenodd"
                              d="M5.5 3.5a2 2 0 100 4 2 2 0 000-4zM2 5.5a3.5 3.5 0 115.898 2.549 5.507 5.507 0 013.034 4.084.75.75 0 11-1.482.235 4.001 4.001 0 00-7.9 0 .75.75 0 01-1.482-.236A5.507 5.507 0 013.102 8.05 3.49 3.49 0 012 5.5zM11 4a.75.75 0 100 1.5 1.5 1.5 0 01.666 2.844.75.75 0 00-.416.672v.352a.75.75 0 00.574.73c1.2.289 2.162 1.2 2.522 2.372a.75.75 0 101.434-.44 5.01 5.01 0 00-2.56-3.012A3 3 0 0011 4z"></path>
                      </svg>
                      <span class="text-bold color-fg-default">22</span>
                      followers
                    </a> · <a class="Link--secondary no-underline no-wrap">
                    <span class="text-bold color-fg-default">30</span>
                    following
                  </a></div>
                </div>

                <ul>

                  <li class="vcard-detail pt-1 css-truncate css-truncate-target hide-sm hide-md" itemprop="homeLocation"
                      show_title="false" aria-label="Home location: Pune, Maharashtra, India">
                    <svg class="octicon octicon-location" viewBox="0 0 16 16" version="1.1" width="16" height="16"
                         aria-hidden="true" style="float:left
                ;margin-right:5px;margin-top:3px">
                      <path fill-rule="evenodd"
                            d="M11.536 3.464a5 5 0 010 7.072L8 14.07l-3.536-3.535a5 5 0 117.072-7.072v.001zm1.06 8.132a6.5 6.5 0 10-9.192 0l3.535 3.536a1.5 1.5 0 002.122 0l3.535-3.536zM8 9a2 2 0 100-4 2 2 0 000 4z"></path>
                    </svg>
                    <span class="p-label">Pune, Maharashtra, India</span>
                  </li>

                  <li itemprop="email" aria-label="Email: mayur091193@gmail.com"
                      class="vcard-detail pt-1 css-truncate css-truncate-target ">
                    <svg class="octicon octicon-mail" viewBox="0 0 16 16" version="1.1" width="16" height="16"
                         aria-hidden="true" style="float:left
                ;margin-right:5px;margin-top:3px">
                      <path fill-rule="evenodd"
                            d="M1.75 2A1.75 1.75 0 000 3.75v.736a.75.75 0 000 .027v7.737C0 13.216.784 14 1.75 14h12.5A1.75 1.75 0 0016 12.25v-8.5A1.75 1.75 0 0014.25 2H1.75zM14.5 4.07v-.32a.25.25 0 00-.25-.25H1.75a.25.25 0 00-.25.25v.32L8 7.88l6.5-3.81zm-13 1.74v6.441c0 .138.112.25.25.25h12.5a.25.25 0 00.25-.25V5.809L8.38 9.397a.75.75 0 01-.76 0L1.5 5.809z"></path>
                    </svg>
                    <a class="Link--primary" href="mailto:mayur091193@gmail.com">mayur091193@gmail.com</a>
                  </li>
                  <li itemprop="url" data-test-selector="profile-website-url"
                      class="vcard-detail pt-1 css-truncate css-truncate-target ">
                    <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16"
                         data-view-component="true" class="octicon octicon-link" style="float:left
                ;margin-right:5px;margin-top:3px">
                      <path fill-rule="evenodd"
                            d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path>
                    </svg>
                    <a rel="nofollow me" class="Link--primary" href="https://q-google-map.netlify.app">https://q-google-map.netlify.app</a>
                  </li>
                </ul>
              </div>
            </div>
            <div class="col-8 q-pr-md">
              <div class="border-b border-gray-200">
                <nav class="-mb-px flex space-x-8" aria-label="Tabs">
                  <!-- Current: "border-indigo-500 text-indigo-600", Default: "border-transparent text-gray-500 hover:text-gray-700 hover:border-gray-300" -->
                  <a style="border-bottom-color: #fd8c73;pointer-events: none"
                     class="border-b-2  text-black hover:text-gray-700 hover:border-gray-300 group inline-flex items-center py-4 px-1 border-b-2 font-medium text-sm">
                    <!--
                      Heroicon name: mini/user

                      Current: "text-indigo-500", Default: "text-gray-400 group-hover:text-gray-500"
                    -->
                    <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16"
                         data-view-component="true" class="octicon octicon-book UnderlineNav-octicon hide-sm">
                      <path fill-rule="evenodd"
                            d="M0 1.75A.75.75 0 01.75 1h4.253c1.227 0 2.317.59 3 1.501A3.744 3.744 0 0111.006 1h4.245a.75.75 0 01.75.75v10.5a.75.75 0 01-.75.75h-4.507a2.25 2.25 0 00-1.591.659l-.622.621a.75.75 0 01-1.06 0l-.622-.621A2.25 2.25 0 005.258 13H.75a.75.75 0 01-.75-.75V1.75zm8.755 3a2.25 2.25 0 012.25-2.25H14.5v9h-3.757c-.71 0-1.4.201-1.992.572l.004-7.322zm-1.504 7.324l.004-5.073-.002-2.253A2.25 2.25 0 005.003 2.5H1.5v9h3.757a3.75 3.75 0 011.994.574z"></path>
                    </svg>
                    <span class="q-ml-sm q-mb-xs text-weight-bold">Overview</span>
                  </a>

                  <a href="#" style="pointer-events: none;"
                     class="border-transparent text-black  hover:border-gray-300 group inline-flex items-center py-4 px-1 border-b-2 font-medium text-sm">
                    <!-- Heroicon name: mini/building-office -->
                    <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16"
                         data-view-component="true" class="octicon octicon-repo UnderlineNav-octicon hide-sm">
                      <path fill-rule="evenodd"
                            d="M2 2.5A2.5 2.5 0 014.5 0h8.75a.75.75 0 01.75.75v12.5a.75.75 0 01-.75.75h-2.5a.75.75 0 110-1.5h1.75v-2h-8a1 1 0 00-.714 1.7.75.75 0 01-1.072 1.05A2.495 2.495 0 012 11.5v-9zm10.5-1V9h-8c-.356 0-.694.074-1 .208V2.5a1 1 0 011-1h8zM5 12.25v3.25a.25.25 0 00.4.2l1.45-1.087a.25.25 0 01.3 0L8.6 15.7a.25.25 0 00.4-.2v-3.25a.25.25 0 00-.25-.25h-3.5a.25.25 0 00-.25.25z"></path>
                    </svg>
                    <span class="q-ml-sm q-mb-xs">Repositories</span><span class="q-ml-sm q-mb-xs">Stars</span> <span
                    class="bg-gray-200 text-black ml-3 py-0.5 px-2.5 rounded-full text-xs font-medium md:inline-block">14</span>
                  </a>

                  <a href="#" style="pointer-events: none;"
                     class=" text-black group inline-flex items-center py-4 px-1  font-medium text-sm"
                     aria-current="page">
                    <!-- Heroicon name: mini/users -->
                    <svg aria-hidden="true" height="14" viewBox="0 0 16 16" version="1.1" width="16"
                         data-view-component="true" class="octicon octicon-table UnderlineNav-octicon hide-sm">
                      <path fill-rule="evenodd"
                            d="M0 1.75C0 .784.784 0 1.75 0h12.5C15.216 0 16 .784 16 1.75v12.5A1.75 1.75 0 0114.25 16H1.75A1.75 1.75 0 010 14.25V1.75zM1.5 6.5v7.75c0 .138.112.25.25.25H5v-8H1.5zM5 5H1.5V1.75a.25.25 0 01.25-.25H5V5zm1.5 1.5v8h7.75a.25.25 0 00.25-.25V6.5h-8zm8-1.5h-8V1.5h7.75a.25.25 0 01.25.25V5z"></path>
                    </svg>
                    <span class="q-ml-sm q-mb-xs">Projects</span>
                  </a>

                  <a href="#" style="pointer-events: none;"
                     class="border-transparent text-black hover:text-gray-700 hover:border-gray-300 group inline-flex items-center py-4 px-1 border-b-2 font-medium text-sm">
                    <!-- Heroicon name: mini/credit-card -->
                    <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16"
                         data-view-component="true" class="octicon octicon-package UnderlineNav-octicon hide-sm">
                      <path fill-rule="evenodd"
                            d="M8.878.392a1.75 1.75 0 00-1.756 0l-5.25 3.045A1.75 1.75 0 001 4.951v6.098c0 .624.332 1.2.872 1.514l5.25 3.045a1.75 1.75 0 001.756 0l5.25-3.045c.54-.313.872-.89.872-1.514V4.951c0-.624-.332-1.2-.872-1.514L8.878.392zM7.875 1.69a.25.25 0 01.25 0l4.63 2.685L8 7.133 3.245 4.375l4.63-2.685zM2.5 5.677v5.372c0 .09.047.171.125.216l4.625 2.683V8.432L2.5 5.677zm6.25 8.271l4.625-2.683a.25.25 0 00.125-.216V5.677L8.75 8.432v5.516z"></path>
                    </svg>
                    <span class="q-ml-sm q-mb-xs">Packages</span>
                  </a>

                  <a href="#" style="pointer-events: none;"
                     class="border-transparent text-black hover:text-gray-700 hover:border-gray-300 group inline-flex items-center py-4 px-1 border-b-2 font-medium text-sm">
                    <!-- Heroicon name: mini/credit-card -->
                    <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16"
                         data-view-component="true" class="octicon octicon-star UnderlineNav-octicon hide-sm">
                      <path fill-rule="evenodd"
                            d="M8 .25a.75.75 0 01.673.418l1.882 3.815 4.21.612a.75.75 0 01.416 1.279l-3.046 2.97.719 4.192a.75.75 0 01-1.088.791L8 12.347l-3.766 1.98a.75.75 0 01-1.088-.79l.72-4.194L.818 6.374a.75.75 0 01.416-1.28l4.21-.611L7.327.668A.75.75 0 018 .25zm0 2.445L6.615 5.5a.75.75 0 01-.564.41l-3.097.45 2.24 2.184a.75.75 0 01.216.664l-.528 3.084 2.769-1.456a.75.75 0 01.698 0l2.77 1.456-.53-3.084a.75.75 0 01.216-.664l2.24-2.183-3.096-.45a.75.75 0 01-.564-.41L8 2.694v.001z"></path>
                    </svg>
                    <span class="q-ml-sm q-mb-xs">Stars</span> <span
                    class="bg-gray-200 text-black ml-3 py-0.5 px-2.5 rounded-full text-xs font-medium md:inline-block">17</span>
                  </a>
                </nav>
              </div>
              <div class="q-mt-lg">
                <div class="q-pa-md" style="border: 1px solid #d0d7de;border-radius: 6px;">
                  <div class="text-black">mayur091193 / readme.md</div>
                  <div class="text-black q-pt-md">
                    <q-markdown
                      :key="count"
                      v-model:src="markdown"
                      :no-html="noHtml"
                      :no-link="noLink"
                      :no-linkify="noLinkify"
                      :no-typographer="noTypographer"
                      :no-breaks="noBreaks"
                      :no-highlight="noHighlight"
                      :no-image="noImage"
                      :no-container="noContainer"
                      :plugins="plugins"
                      class=" "
                    />
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </q-card-section>

    </q-card>
  </q-dialog>


<!--  <div v-if="view_modal" class="rounded-md q-ml-lg q-pa-md fixed-bottom-right  z-max">-->
<!--    <a @click="copyMarkdownCode"-->
<!--        class="cursor-pointer z-max flex w-full items-center text-weight-bold justify-center rounded-md border border-transparent bg-green-7 px-4 py-2 text-base text-subtitle2 text-white hover:bg-indigo-700 ">-->
<!--      <q-icon class="q-mr-sm" name="content_copy"/>-->
<!--      Copy Markdown</a>-->
<!--  </div>-->

</template>

<style lang="sass">

.q-markdown
  position: relative

  a
    display: inline-block !important

  ul
    display: block
    list-style-type: disc
    margin-top: 1em
    margin-bottom: 1em
    margin-left: 0
    margin-right: 0
    padding-left: 40px

  ol
    display: block
    list-style-type: decimal
    margin-top: 1em
    margin-bottom: 1em
    margin-left: 0
    margin-right: 0
    padding-left: 40px


  code, pre
    font-family: Consolas, Monaco, Andale Mono, Ubuntu Mono, monospace

  pre
    border-radius: $generic-border-radius
    padding: 5px
    margin: 0
    background-size: 1.5em 1.5em
    background-origin: content-box
    background-attachment: local
    max-height: inherit
    height: inherit
    display: block
    overflow: auto
    position: relative
    font-size: 12px
    background: $blue-grey-1
    color: $grey-10
    text-align: left
    white-space: pre
    word-spacing: normal
    word-break: normal
    word-wrap: normal
    line-height: 1.5em
    tab-size: 4
    hyphens: none

  pre code
    border-radius: 0
    width: max-content

  &--heading
    cursor: pointer

    &:after
      content: ' #'
      opacity: 0
      transition: opacity .2s

    &:hover:after
      opacity: 1

    &-h1
      font-size: 2rem
      line-height: 2rem
      padding: 1rem 0
      font-weight: 500
      margin: 0 0 1rem

    &-h2
      font-size: 1.5rem
      line-height: 1.5rem
      padding: 0.5rem 0
      font-weight: 500
      margin: 1rem 0 1rem

    &-h3
      font-size: 1.1rem
      line-height: 1.1rem
      padding: 0.45rem 0
      margin: 1rem 0 1rem

    &-h4
      font-size: 1rem
      line-height: 1rem
      padding: 0.25rem 0
      margin: 1rem 0

    &-h5
      font-size: 0.9rem
      margin: 1rem 0

    &-h6
      font-size: 0.8rem
      margin: 1rem 0

    .q-markdown--link
      border-bottom: inherit
      color: inherit

    &--anchor-link
      cursor: pointer

      &:after
        content: ' #'
        opacity: 0
        transition: opacity .2s

      &:hover:after
        opacity: 1

  &--title-heavy
    border-bottom: 3px solid #ccc

  &--title-light
    border-bottom: 1px solid #ccc

  &--image
    max-width: 100%
    height: auto

  &--link
    font-weight: 500
    text-decoration: none
    outline: 0
    border-bottom: 1px dotted currentColor
    text-align: center
    transition: opacity .2s
    // white-space: nowrap // prevents long headlines from wrapping properly

    &:hover
    // color: yellow

    &-local
      font-family: inherit

    &-external
      font-family: inherit

      &:after
        content: '\e895'
        // hash
        font-family: Material Icons
        font-weight: normal
        font-style: normal
        display: inline-block
        line-height: 1
        text-transform: none
        letter-spacing: normal
        word-wrap: normal
        white-space: nowrap
        direction: ltr
        text-rendering: optimizeLegibility
        -webkit-font-smoothing: antialiased
        -moz-osx-font-smoothing: grayscale
        font-feature-settings: "liga"
        margin: 0 0 0 3px
        padding: 0

  &--token
    white-space: nowrap
    background: $grey-1
    color: $grey-10
    border: $grey-8 solid 1px
    padding: 1px 2px
    font-family: inherit
    border-radius: $generic-border-radius

  &--note
    margin: 14px 0
    padding: 10px
    font-size: 1em
    letter-spacing: .5px
    background: $blue-grey-1
    color: $grey-10
    font-weight: 400

    > p:last-child, .q-markdown--note:last-child
      margin-bottom: 0

    .q-markdown--link
    // color: $grey-2

    &--
      border-left: 10px solid lighten($grey-8, 30%)
      border-radius: 8px 0 0 8px

      .q-markdown--link
        color: lighten($grey-8, 10%)

    &--info
      border-left: 10px solid lighten($blue-8, 30%)
      border-radius: 8px 0 0 8px
      color: $grey-9
      background: $blue-2

      .q-markdown--link
        color: lighten($blue-8, 10%)

      .q-markdown--note-title
        color: lighten($blue-8, 10%)

    &--tip
      border-left: 10px solid lighten($green-8, 30%)
      border-radius: 8px 0 0 8px
      color: $grey-9
      background: $green-2

      .q-markdown--link
        color: lighten($green-8, 10%)

      .q-markdown--note-title
        color: lighten($green-8, 10%)

    &--warning
      border-left: 10px solid lighten($orange-10, 30%)
      border-radius: 8px 0 0 8px
      color: $grey-9
      background: $orange-2

      .q-markdown--link
        color: lighten($orange-10, 10%)

      .q-markdown--note-title
        color: lighten($orange-10, 10%)

    &--danger
      border-left: 10px solid lighten($negative, 30%)
      border-radius: 8px 0 0 8px
      color: $grey-9
      background: $red-2

      .q-markdown--link
        color: lighten($red-8, 10%)

      .q-markdown--note-title
        color: lighten($red-8, 10%)

    &-title
      font-weight: 800
      margin-left: -4px
      margin-right: -4px
      padding: 0 4px
      margin-bottom: 4px

  &--table
    width: fit-content
    margin-bottom: 16px
    border-collapse: collapse
    max-width: 100%
    border-width: 1px
    border-style: solid
    border-color: $grey

  &--line-numbers-wrapper
    display: flex
    justify-content: flex-start
    font-size: 12px
    margin: 0 0 1.0em 0
    background: $blue-grey-1
    color: $grey-10
    font-family: Consolas, Monaco, 'Andale Mono', 'Ubuntu Mono', monospace
    border-radius: $generic-border-radius

  &--line-numbers
    padding: 5px
    text-align: right

  &--line-number
    color: $grey-6
    margin: 0
    position: relative
    text-align: left
    white-space: pre
    word-spacing: normal
    word-break: normal
    word-wrap: normal
    line-height: 1.5
    tab-size: 4
    hyphens: none

  &--code-wrapper
    width: 100%
    min-width: 0

  &--code,
  &--code__inner
    margin: 0
    position: relative
    text-align: left
    white-space: pre
    word-spacing: normal
    word-break: normal
    word-wrap: normal
    line-height: 1.5
    tab-size: 4
    hyphens: none
    border-radius: $generic-border-radius
    background: $blue-grey-1
    color: $grey-10


  &--code
    overflow: visible
    padding: 0

    &__inner
      max-height: inherit
      height: inherit
      display: block
      overflow: auto

  &--table
    border-color: $grey-4
    background: $grey-1

  &--table thead
    background: $grey-4

  &--table thead tr th
    padding: 8px
    border-width: 1px
    border-style: solid
    background: $grey-2

  &--table tbody
    background: $grey-1

  &--table tbody td,
  &--table tbody th
    padding: 8px
    border-width: 1px
    border-style: solid

  &--table tbody tr:nth-child(odd)
    background: $grey-4

// .q-markdown--page > div, .q-markdown--page > pre
//   margin-bottom: 22px

blockquote.q-markdown--link
  background: transparent
  // color: $teal-6

  &:hover
// color: yellow

blockquote.q-markdown--note
  border-width: 1px 8px 1px 8px
  border-radius: 8px
  border-style: solid
  border-color: $grey-6 $teal-6

.q-markdown__copy
  position: absolute
  top: 15px
  right: 15px

.body--dark
  .q-markdown
    color: $grey-2

    code
      background: $grey-9
      color: $grey-2

    .q-markdown--link
      // color: $teal-6

      &:hover
    // color: yellow

    blockquote.q-markdown--note
      border-color: $grey-6 $grey-6
      background: $dark
      color: $grey-2

    pre, pre code
      background: $dark

    .q-markdown--line-numbers-wrapper
      background: $dark
      color: $grey-2

    .q-markdown--token
      background: $grey-6
      color: $grey-10
      border: $grey-4 solid 1px

    .q-markdown--code
      background: $dark
      color: $grey-10

    .q-markdown--note
      background: $grey-10
      color: white
      border-top: 1px solid $grey-9
      border-bottom: 1px solid $grey-9

    .q-markdown--note--
      border-left: 10px solid $grey-6

    .q-markdown--note--info
      border-left: 10px solid $light-blue-10

    .q-markdown--note--tip
      border-left: 10px solid $light-green-10

    .q-markdown--note--warning
      border-left: 10px solid $orange-10

    .q-markdown--note--danger
      border-left: 10px solid $red-10

    .q-markdown--table thead tr th,
    .q-markdown--table tbody
      background-color: $dark

    .q-markdown--table tbody tr:nth-child(2n+1)
      background-color: $grey-9

</style>

<script>
import {defineComponent, ref, watch, onMounted, getCurrentInstance} from 'vue'
import {QMarkdown} from '@quasar/quasar-ui-qmarkdown'
import '@quasar/quasar-ui-qmarkdown/dist/index.css'

import abbreviation from 'markdown-it-abbr'
import deflist from 'markdown-it-deflist'
import emoji from 'markdown-it-emoji'
import footnote from 'markdown-it-footnote'
import insert from 'markdown-it-ins'
import mark from 'markdown-it-mark'
import subscript from 'markdown-it-sub'
import superscript from 'markdown-it-sup'
import taskLists from 'markdown-it-task-lists'
import mermaid from '@datatraccorporation/markdown-it-mermaid'
import {copyToClipboard} from 'quasar'

export default {
  name: 'GH',
  components: {
    QMarkdown
  },
  setup() {
    const
      splitterModel = ref(50),
      markdown = ref('Testing'),
      noHtml = ref(false),
      noLink = ref(false),
      noLinkify = ref(false),
      noTypographer = ref(false),
      noBreaks = ref(false),
      noHighlight = ref(false),
      noEmoji = ref(false),
      noSubscript = ref(false),
      noSuperscript = ref(false),
      noFootnote = ref(false),
      noDeflist = ref(false),
      noAbbreviation = ref(false),
      noInsert = ref(false),
      noMark = ref(false),
      noImage = ref(false),
      noTasklist = ref(false),
      noContainer = ref(false),
      noMermaid = ref(false),
      plugins = ref([]),
      count = ref(0)

    watch([
      noAbbreviation,
      noDeflist,
      noEmoji,
      noFootnote,
      noInsert,
      noMark,
      noSubscript,
      noSuperscript,
      noTasklist,
      noMermaid
    ], () => {
      rebuildPlugins()
    })

    function rebuildPlugins() {
      plugins.value.splice(0, plugins.value.length)

      if (noAbbreviation.value !== true) plugins.value.push(abbreviation)
      if (noDeflist.value !== true) plugins.value.push(deflist)
      if (noEmoji.value !== true) plugins.value.push(emoji)
      if (noFootnote.value !== true) plugins.value.push(footnote)
      if (noInsert.value !== true) plugins.value.push(insert)
      if (noMark.value !== true) plugins.value.push(mark)
      if (noSubscript.value !== true) plugins.value.push(subscript)
      if (noSuperscript.value !== true) plugins.value.push(superscript)
      if (noTasklist.value !== true) plugins.value.push(taskLists)
      if (noMermaid.value !== true) plugins.value.push(mermaid)

      // by having `:key="count"` on the q-markdown component,
      // we can force Vue to do a refresh when the plugins change
      count.value += 1
    }

    onMounted(() => {
      rebuildPlugins()
    })

    return {
      splitterModel,
      noHtml,
      noLink,
      noLinkify,
      noTypographer,
      noBreaks,
      noHighlight,
      noEmoji,
      noSubscript,
      noSuperscript,
      noFootnote,
      noDeflist,
      noAbbreviation,
      noInsert,
      noMark,
      noImage,
      noTasklist,
      noContainer,
      noMermaid,
      plugins,
      count,
      markdown: ref(`<p>
  <a href="https://twitter.com/Mayur06322144">
    <img src="https://img.shields.io/twitter/follow/Mayur06322144?label=Follow%20%40Mayur06322144&style=social" alt="Twitter">
  </a>&ensp;
  <a href="https://www.reddit.com/user/mayur091193">
    <img src="https://img.shields.io/reddit/user-karma/combined/mayur091193?style=social" alt="Reddit">
  </a>&ensp;
  <a href="https://stackoverflow.com/users/4762957/mayur-patel?tab=profile">
    <img src="https://img.shields.io/stackexchange/stackoverflow/r/4762957?color=orange" alt="Stackoverflow">
  </a>&ensp;
  <a href="https://dev.to/mayur091193">
    <img src="https://img.shields.io/badge/dev.to-Follow-lightgrey?style=social&logo=dev.to" alt="dev.to">
  </a>
</p>

### Hi there 👋, Mayur here...Thanks for visiting my Profile


- 🔭 I’m currently working on open-source projects (Quasar framework and Vue.js, Angular 12, Python 3.X)
- 🌱 Always learning new Technologies
- 🏗 I’m developing free quasar app extensions, chrome extensions, templates and components
- 💬 Ask me about Quasar framework and Vue.js! And many more technologies like Python-flask framework, JavaScript, jQuery, AngularJS, Angular ...
- 📫 How to reach me: mayur091193@gmail.com
- 💖 Sponsor me to support my open source work. https://github.com/sponsors/mayur091193
- 🌴 Loves nature travel
- 🖼️ Loves to help developers
- 🔗 Owner of q-google-map: https://q-google-map.netlify.app/


---

<div>
  <h4>🏆 Github Profile Trophy</h4>
  <img src="https://github-profile-trophy.vercel.app/?username=mayur091193&column=7"/>
</div>

---

<div>
  <h4>👨🏻‍💻 GitHub Usage stats</h4>
  <img height="170" align="left" src="https://github-readme-stats.vercel.app/api?username=mayur091193&count_private=true&include_all_commits=true" />
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=mayur091193&layout=compact" />
</div>

---
`),
      view_modal: ref(false),
      available_height: ref(0),
      selected_tab: ref("Basic Information"),
      all_prog_tech: ref([
        {
          text: 'Python',
          icons: 'https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg',
          value: 'python'
        }, {
          text: 'Java',
          icons: 'https://raw.githubusercontent.com/devicons/devicon/master/icons/java/java-original.svg',
          value: 'java'
        }, {
          text: 'C',
          icons: 'https://raw.githubusercontent.com/devicons/devicon/master/icons/c/c-original.svg',
          value: 'c'
        }, {
          text: 'C++',
          icons: 'https://raw.githubusercontent.com/devicons/devicon/master/icons/cplusplus/cplusplus-original.svg',
          value: 'cplusplus'
        }, {
          text: 'C#',
          icons: 'https://raw.githubusercontent.com/devicons/devicon/master/icons/csharp/csharp-original.svg',
          value: 'csharp'
        }, {
          text: 'Go',
          icons: 'https://raw.githubusercontent.com/devicons/devicon/master/icons/go/go-original.svg',
          value: 'go'
        }, {
          text: 'PHP',
          icons: 'https://raw.githubusercontent.com/devicons/devicon/master/icons/php/php-original.svg',
          value: 'php'
        }, {
          text: 'Perl',
          icons: 'https://api.iconify.design/logos-perl.svg',
          value: 'perl'
        }, {
          text: 'Ruby',
          icons: 'https://raw.githubusercontent.com/devicons/devicon/master/icons/ruby/ruby-original.svg',
          value: 'ruby'
        },
      ]),
      all_frontend_tech: ref([
        {
          text: 'Vue.js',
          icons: 'https://raw.githubusercontent.com/devicons/devicon/master/icons/vuejs/vuejs-original-wordmark.svg',
          value: 'vuejs'
        }, {
          text: 'React',
          icons: 'https://raw.githubusercontent.com/devicons/devicon/master/icons/react/react-original-wordmark.svg',
          value: 'react'
        }, {
          text: 'Angular JS',
          icons: 'https://raw.githubusercontent.com/devicons/devicon/master/icons/angularjs/angularjs-original-wordmark.svg',
          value: 'angularjs'
        }, {
          text: 'Angular',
          icons: 'https://angular.io/assets/images/logos/angular/angular.svg',
          value: 'angular'
        }, {
          text: 'JavaScript',
          icons: 'https://raw.githubusercontent.com/devicons/devicon/master/icons/javascript/javascript-original.svg',
          value: 'javascript'
        }, {
          text: 'Typescript',
          icons: 'https://raw.githubusercontent.com/devicons/devicon/master/icons/typescript/typescript-original.svg',
          value: 'typescript'
        }, {
          text: 'Bootstrap',
          icons: 'https://raw.githubusercontent.com/devicons/devicon/master/icons/bootstrap/bootstrap-plain-wordmark.svg',
          value: 'bootstrap'
        }, {
          text: 'Vuetify',
          icons: 'https://bestofjs.org/logos/vuetify.svg',
          value: 'vuetify'
        }, {
          text: 'HTML5',
          icons: 'https://raw.githubusercontent.com/devicons/devicon/master/icons/html5/html5-original-wordmark.svg',
          value: 'html5'
        }, {
          text: 'SAAS',
          icons: 'https://raw.githubusercontent.com/devicons/devicon/master/icons/sass/sass-original.svg',
          value: 'sass'
        }, {
          text: 'Redux',
          icons: 'https://raw.githubusercontent.com/devicons/devicon/master/icons/redux/redux-original.svg',
          value: 'redux'
        }, {
          text: 'Webpack',
          icons: 'https://raw.githubusercontent.com/devicons/devicon/d00d0969292a6569d45b06d3f350f463a0107b0d/icons/webpack/webpack-original-wordmark.svg',
          value: 'webpack'
        }, {
          text: 'Tailwind CSS',
          icons: 'https://www.vectorlogo.zone/logos/tailwindcss/tailwindcss-icon.svg',
          value: 'tailwind'
        }
      ]),
      all_backend_tech: ref([
        {
          text: 'NodeJs',
          icons: 'https://raw.githubusercontent.com/devicons/devicon/master/icons/nodejs/nodejs-original-wordmark.svg',
          value: 'nodejs'
        }, {
          text: 'Spring',
          icons: 'https://www.vectorlogo.zone/logos/springio/springio-icon.svg',
          value: 'spring'
        }, {
          text: 'Express',
          icons: 'https://raw.githubusercontent.com/devicons/devicon/master/icons/express/express-original-wordmark.svg',
          value: 'express'
        }, {
          text: 'RabbitMQ',
          icons: 'https://www.vectorlogo.zone/logos/rabbitmq/rabbitmq-icon.svg',
          value: 'rabbitMQ'
        }, {
          text: 'Hadoop',
          icons: 'https://www.vectorlogo.zone/logos/apache_hadoop/apache_hadoop-icon.svg',
          value: 'hadoop'
        }, {
          text: 'Nginx',
          icons: 'https://raw.githubusercontent.com/devicons/devicon/master/icons/nginx/nginx-original.svg',
          value: 'nginx'
        }, {
          text: 'NestJs',
          icons: 'https://raw.githubusercontent.com/devicons/devicon/master/icons/nestjs/nestjs-plain.svg',
          value: 'nestjs'
        }
      ]),
      all_mobile_tech: ref([
        {
          text: 'Android',
          icons: 'https://raw.githubusercontent.com/devicons/devicon/master/icons/android/android-original-wordmark.svg',
          value: 'android'
        }, {
          text: 'Flutter',
          icons: 'https://www.vectorlogo.zone/logos/flutterio/flutterio-icon.svg',
          value: 'flutter'
        }, {
          text: 'Dart',
          icons: 'https://www.vectorlogo.zone/logos/dartlang/dartlang-icon.svg',
          value: 'dart'
        }, {
          text: 'Kotlin',
          icons: 'https://www.vectorlogo.zone/logos/kotlinlang/kotlinlang-icon.svg',
          value: 'kotlin'
        }, {
          text: 'Native Script',
          icons: 'https://raw.githubusercontent.com/detain/svg-logos/780f25886640cef088af994181646db2f6b1a3f8/svg/nativescript.svg',
          value: 'nativescript'
        }, {
          text: 'Xamarin',
          icons: 'https://raw.githubusercontent.com/detain/svg-logos/780f25886640cef088af994181646db2f6b1a3f8/svg/xamarin.svg',
          value: 'xamarin'
        }, {
          text: 'React Native',
          icons: 'https://reactnative.dev/img/header_logo.svg',
          value: 'reactnative'
        }, {
          text: 'Ionic',
          icons: 'https://upload.wikimedia.org/wikipedia/commons/d/d1/Ionic_Logo.svg',
          value: 'ionic'
        }, {
          text: 'Apache Cordova',
          icons: 'https://www.vectorlogo.zone/logos/apache_cordova/apache_cordova-icon.svg',
          value: 'apachecordova'
        }
      ]),
      all_ai_ml_tech: ref([
        {
          text: 'TensorFlow',
          icons: 'https://www.vectorlogo.zone/logos/tensorflow/tensorflow-icon.svg',
          value: 'tensorflow'
        }, {
          text: 'Pytorch',
          icons: 'https://www.vectorlogo.zone/logos/pytorch/pytorch-icon.svg',
          value: 'pytorch'
        }, {
          text: 'Pandas',
          icons: 'https://raw.githubusercontent.com/devicons/devicon/2ae2a900d2f041da66e950e4d48052658d850630/icons/pandas/pandas-original.svg',
          value: 'pandas'
        }, {
          text: 'Seaborn',
          icons: 'https://seaborn.pydata.org/_images/logo-mark-lightbg.svg',
          value: 'seaborn'
        }, {
          text: 'OpenCV',
          icons: 'https://www.vectorlogo.zone/logos/opencv/opencv-icon.svg',
          value: 'opencv'
        }, {
          text: 'Scikit Learn',
          icons: 'https://upload.wikimedia.org/wikipedia/commons/0/05/Scikit_learn_logo_small.svg',
          value: 'scikit_learn'
        },
      ]),
      all_database_tech: ref([
        {
          text: 'MongoDB',
          icons: 'https://raw.githubusercontent.com/devicons/devicon/master/icons/mongodb/mongodb-original-wordmark.svg',
          value: 'mongodb'
        }, {
          text: 'MySql',
          icons: 'https://raw.githubusercontent.com/devicons/devicon/master/icons/mysql/mysql-original-wordmark.svg',
          value: 'mysql'
        }, {
          text: 'PoastgreSQL',
          icons: 'https://raw.githubusercontent.com/devicons/devicon/master/icons/postgresql/postgresql-original-wordmark.svg',
          value: 'postgresql'
        }, {
          text: 'Redis',
          icons: 'https://raw.githubusercontent.com/devicons/devicon/master/icons/redis/redis-original-wordmark.svg',
          value: 'redis'
        }, {
          text: 'Oracle',
          icons: 'https://raw.githubusercontent.com/devicons/devicon/master/icons/oracle/oracle-original.svg',
          value: 'oracle'
        }, {
          text: 'CouchDB',
          icons: 'https://raw.githubusercontent.com/devicons/devicon/0d6c64dbbf311879f7d563bfc3ccf559f9ed111c/icons/couchdb/couchdb-original.svg',
          value: 'couchdb'
        }, {
          text: 'MariaDB',
          icons: 'https://www.vectorlogo.zone/logos/mariadb/mariadb-icon.svg',
          value: 'mariadb'
        }, {
          text: 'ElasticSearch',
          icons: 'https://www.vectorlogo.zone/logos/elastic/elastic-icon.svg',
          value: 'elasticsearch'
        }, {
          text: 'Sqlite',
          icons: 'https://www.vectorlogo.zone/logos/sqlite/sqlite-icon.svg',
          value: 'sqlite'
        }, {
          text: 'MS SQL Server',
          icons: 'https://www.svgrepo.com/show/303229/microsoft-sql-server-logo.svg',
          value: 'mssql'
        },
      ]),
      all_devops_tech: ref([
        {
          text: 'AWS',
          icons: 'https://raw.githubusercontent.com/devicons/devicon/master/icons/amazonwebservices/amazonwebservices-original-wordmark.svg',
          value: 'aws'
        }, {
          text: 'Docker',
          icons: 'https://raw.githubusercontent.com/devicons/devicon/master/icons/docker/docker-original-wordmark.svg',
          value: 'docker'
        }, {
          text: 'Jenkins',
          icons: 'https://www.vectorlogo.zone/logos/jenkins/jenkins-icon.svg',
          value: 'jenkins'
        }, {
          text: 'Kubernetes',
          icons: 'https://www.vectorlogo.zone/logos/kubernetes/kubernetes-icon.svg',
          value: 'kubernetes'
        }, {
          text: 'Bach',
          icons: 'https://www.vectorlogo.zone/logos/gnu_bash/gnu_bash-icon.svg',
          value: 'bash'
        }, {
          text: 'Azure',
          icons: 'https://www.vectorlogo.zone/logos/microsoft_azure/microsoft_azure-icon.svg',
          value: 'azure'
        }
      ]),
      all_static_site_generator_tech: ref([
        {
          text: 'Gatsby',
          icons: 'https://www.vectorlogo.zone/logos/gatsbyjs/gatsbyjs-icon.svg',
          value: 'gatsby'
        }, {
          text: 'Gridsome',
          icons: 'https://www.vectorlogo.zone/logos/gridsome/gridsome-icon.svg',
          value: 'gridsome'
        }, {
          text: 'Hugo',
          icons: 'https://api.iconify.design/logos-hugo.svg',
          value: 'hugo'
        }, {
          text: 'Nextjs',
          icons: 'https://cdn.worldvectorlogo.com/logos/nextjs-2.svg',
          value: 'nextjs'
        }, {
          text: 'Nuxtjs',
          icons: 'https://www.vectorlogo.zone/logos/nuxtjs/nuxtjs-icon.svg',
          value: 'nuxtjs'
        }, {
          text: 'Vuepress',
          icons: 'https://raw.githubusercontent.com/AliasIO/wappalyzer/master/src/drivers/webextension/images/icons/VuePress.svg',
          value: 'vuepress'
        }
      ]),
      all_gaming_tech: ref([
        {
          text: 'Unity',
          icons: 'https://www.vectorlogo.zone/logos/unity3d/unity3d-icon.svg',
          value: 'unity'
        }, {
          text: 'Unreal',
          icons: 'https://raw.githubusercontent.com/kenangundogan/fontisto/036b7eca71aab1bef8e6a0518f7329f13ed62f6b/icons/svg/brand/unreal-engine.svg',
          value: 'unreal'
        }
      ]),
      all_data: ref({
        title: 'Hi there 👋, I am ',
        name: 'Mayur Patel from India.',
        github_username: '',
        devdotto_username: '',
        twitter_username: '',
        codepen_username: '',
        reddit_username: '',
        stackoverflow_username: '',
        linkdin_username: '',
        medium_username: '',
        hackerearth_username: '',
        youtube_username: '',
        instagram_username: '',
        facebook_username: '',
        description: 'Full-stack developer working on open source projects!',
        work_line_1_label: "🔭 I’m currently working on ",
        work_line_1_value: "open-source projects.",
        work_line_2_label: "🌱 Always learning ",
        work_line_2_value: "new Technologies.",
        work_line_3_label: "🏗 I’m developing ",
        work_line_3_value: "ios/mobile apps as well as free website templates.",
        work_line_4_label: "💬 Ask me about ",
        work_line_4_value: "Quasar framework and Vue.js!",
        work_line_5_label: "📫 How to reach me ",
        work_line_5_value: "mayur091193@gmail.com",
        work_line_6_label: "🔗 Owner of q-google-map: ",
        work_line_6_value: "https://q-google-map.netlify.app/",
        work_line_7_label: "💖 Sponsor me to support my open source work: ",
        work_line_7_value: "https://github.com/sponsors/mayur091193",
        work_line_8_label: "🙏 Please Support: ",
        work_line_8_value: "https://www.buymeacoffee.com/mayur091193",
        selected_prog_techs: [],
        selected_frontend_techs: [],
        selected_backend_techs: [],
        selected_mobileapp_techs: [],
        selected_aiml_techs: [],
        selected_database_techs: [],
        selected_devops_techs: [],
        selected_staticsitegenerator_techs: [],
        selected_gaming_techs: [],
      })
    }
  },
  mounted() {
    this.available_height = (window.innerHeight - 105) + 'px';
  },
  methods: {
    generateProfile(selected_template) {
      let self = this;
      let final_markdown = ``;

      final_markdown = final_markdown + "<p>";
      final_markdown = final_markdown + "\n";
      if (self.all_data.twitter_username) {
        final_markdown = final_markdown + ('<a href="https://twitter.com/twitter_username">' +
          '<img src="https://img.shields.io/twitter/follow/twitter_username?label=Follow%20%40twitter_username&style=social" alt="Twitter">' +
          '</a>&ensp;').replaceAll('twitter_username', self.all_data.twitter_username)
      }
      if (self.all_data.reddit_username) {
        final_markdown = final_markdown + ('<a href="tps://www.reddit.com/user/reddit_username">' +
          '<img src="https://img.shields.io/reddit/user-karma/combined/reddit_username?style=social" alt="Reddit">' +
          '</a>&ensp;').replaceAll('reddit_username', self.all_data.reddit_username)
      }
      if (self.all_data.stackoverflow_username) {
        final_markdown = final_markdown + ('<a href="https://stackoverflow.com/users/stackoverflow_username">' +
          '<img src="https://img.shields.io/stackexchange/stackoverflow/r/stackoverflow_username?color=orange" alt="Twitter">' +
          '</a>&ensp;').replaceAll('stackoverflow_username', self.all_data.stackoverflow_username)
      }
      if (self.all_data.devdotto_username) {
        final_markdown = final_markdown + ('<a href="https://dev.to/devdotto_username">' +
          '<img src="https://img.shields.io/badge/dev.to-Follow-lightgrey?style=social&logo=dev.to" alt="dev.to">' +
          '</a>&ensp;').replaceAll('devdotto_username', self.all_data.devdotto_username)
      }
      final_markdown = final_markdown + "</p> \n";

      if (self.all_data.name) {
        final_markdown = final_markdown + "\n ### " + self.all_data.title.trim() + ' ' + self.all_data.name.trim() + '\n';
      }
      if (self.all_data.description) {
        final_markdown = final_markdown + "\n ##### " + self.all_data.description.trim() + '\n';
      }

      if (self.all_data.work_line_1_value) {
        final_markdown = final_markdown + '\n - ' + self.all_data.work_line_1_label.trim() + ' ' + self.all_data.work_line_1_value;
      }
      if (self.all_data.work_line_2_value) {
        final_markdown = final_markdown + '\n - ' + self.all_data.work_line_2_label.trim() + ' ' + self.all_data.work_line_2_value;
      }
      if (self.all_data.work_line_3_value) {
        final_markdown = final_markdown + '\n - ' + self.all_data.work_line_3_label.trim() + ' ' + self.all_data.work_line_3_value;
      }
      if (self.all_data.work_line_4_value) {
        final_markdown = final_markdown + '\n - ' + self.all_data.work_line_4_label.trim() + ' ' + self.all_data.work_line_4_value;
      }
      if (self.all_data.work_line_5_value) {
        final_markdown = final_markdown + '\n - ' + self.all_data.work_line_5_label.trim() + ' ' + self.all_data.work_line_5_value;
      }
      if (self.all_data.work_line_6_value) {
        final_markdown = final_markdown + '\n - ' + self.all_data.work_line_6_label.trim() + ' ' + self.all_data.work_line_6_value;
      }
      if (self.all_data.work_line_7_value) {
        final_markdown = final_markdown + '\n - ' + self.all_data.work_line_7_label.trim() + ' ' + self.all_data.work_line_7_value;
      }
      if (self.all_data.work_line_8_value) {
        final_markdown = final_markdown + '\n - ' + self.all_data.work_line_8_label.trim() + ' ' + self.all_data.work_line_8_value;
      }

      final_markdown = final_markdown + "\n \n ---\n\n";
      final_markdown = final_markdown + "\n \n";
      // final_markdown = final_markdown + "<p>";
      // final_markdown = final_markdown + "\n";
      // if (self.all_data.twitter_username) {
      //   final_markdown = final_markdown + ('<a href="https://twitter.com/twitter_username">' +
      //     '<img src="https://img.shields.io/twitter/follow/twitter_username?label=Follow%20%40twitter_username&style=social" alt="Twitter">' +
      //     '</a>&ensp;').replaceAll('twitter_username', self.all_data.twitter_username)
      // }
      // if (self.all_data.reddit_username) {
      //   final_markdown = final_markdown + ('<a href="tps://www.reddit.com/user/reddit_username">' +
      //     '<img src="https://img.shields.io/reddit/user-karma/combined/reddit_username?style=social" alt="Reddit">' +
      //     '</a>&ensp;').replaceAll('reddit_username', self.all_data.reddit_username)
      // }
      // if (self.all_data.stackoverflow_username) {
      //   final_markdown = final_markdown + ('<a href="https://stackoverflow.com/users/stackoverflow_username">' +
      //     '<img src="https://img.shields.io/stackexchange/stackoverflow/r/stackoverflow_username?color=orange" alt="Twitter">' +
      //     '</a>&ensp;').replaceAll('stackoverflow_username', self.all_data.stackoverflow_username)
      // }
      // if (self.all_data.devdotto_username) {
      //   final_markdown = final_markdown + ('<a href="https://dev.to/devdotto_username">' +
      //     '<img src="https://img.shields.io/badge/dev.to-Follow-lightgrey?style=social&logo=dev.to" alt="dev.to">' +
      //     '</a>&ensp;').replaceAll('devdotto_username', self.all_data.devdotto_username)
      // }
      // final_markdown = final_markdown + "</p>\n";


      // work tech
      if(self.all_data.devdotto_username || self.all_data.codepen_username || self.all_data.stackoverflow_username || self.all_data.linkdin_username || self.all_data.medium_username || self.all_data.hackerearth_username
      || self.all_data.twitter_username || self.all_data.reddit_username || self.all_data.youtube_username || self.all_data.instagram_username || self.all_data.facebook_username){
        // final_markdown = final_markdown + "\n \n ---\n\n";
        final_markdown = final_markdown + '\n ### Social(Tech) Profiles \n '
      }
      final_markdown = final_markdown + "<p align='left'>"
      if(self.all_data.devdotto_username){
        final_markdown = final_markdown + '<a href="https://dev.to/' + self.all_data.devdotto_username.trim() + '" target="_blank"><img height="30" width="30" src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/dev-dot-to.svg" /></a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'
      }
      if(self.all_data.codepen_username){
        final_markdown = final_markdown + '<a href="https://codepen.io/' + self.all_data.codepen_username.trim() + '" target="_blank"><img height="30" width="30" src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/codepen.svg" /></a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'
      }
      if(self.all_data.stackoverflow_username){
        final_markdown = final_markdown + '<a href="https://stackoverflow.com/users/' + self.all_data.stackoverflow_username.trim() + '" target="_blank"><img height="30" width="30" src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/stackoverflow.svg" /></a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'
      }
      if(self.all_data.linkdin_username){
        final_markdown = final_markdown + '<a href="https://linkedin.com/in/' + self.all_data.linkdin_username.trim()+ '" target="_blank"><img height="30" width="30" src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/linkedin.svg" /></a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'
      }
      if(self.all_data.medium_username){
        final_markdown = final_markdown + '<a href="https://medium.com/' + self.all_data.medium_username.trim() + '" target="_blank"><img height="30" width="30" src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/medium.svg" /></a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'
      }
      if(self.all_data.hackerearth_username){
        final_markdown = final_markdown + '<a href=https://www.hackerearth.com/"' + self.all_data.hackerearth_username.trim() + '" target="_blank"><img height="30" width="30" src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/hackerearth.svg" /></a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'
      }
      if(self.all_data.twitter_username){
        final_markdown = final_markdown + '<a href="https://twitter.com/' + self.all_data.twitter_username.trim() + '" target="_blank"><img height="30" width="30" src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/twitter.svg" /></a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'
      }
      if(self.all_data.reddit_username){
        final_markdown = final_markdown + '<a href="https://www.reddit.com/user/' + self.all_data.reddit_username.trim() + '" target="_blank"><img height="30" width="30" src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/reddit.svg" /></a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'
      }
      if(self.all_data.youtube_username){
        final_markdown = final_markdown + '<a href="https://www.youtube.com/c/' + self.all_data.youtube_username.trim() + '" target="_blank"><img height="30" width="30" src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/youtube.svg" /></a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'
      }
      if(self.all_data.instagram_username){
        final_markdown = final_markdown + '<a href="https://instagram.com/' + self.all_data.instagram_username.trim() + '" target="_blank"><img height="30" width="30" src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/instagram.svg" /></a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'
      }
      if(self.all_data.facebook_username){
        final_markdown = final_markdown + '<a href="https://fb.com/' + self.all_data.facebook_username.trim() + '" target="_blank"><img height="30" width="30" src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/facebook.svg" /></a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'
      }
      final_markdown = final_markdown + "</p> \n"

      final_markdown = final_markdown + "\n \n ---\n\n";

      //Prog tech
      if(self.all_data.selected_prog_techs.length > 0) {
        final_markdown = final_markdown + '\n ### Programming Languages \n '
        final_markdown = final_markdown + "<p align='left'>"
        self.all_data.selected_prog_techs.map(function (item){
          let obj_item = self.all_prog_tech.filter(function (item_all) { return item == item_all.value});

          final_markdown = final_markdown + '<a><img height="30" width="30" src="' + obj_item[0].icons + '" /></a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'
        });
        final_markdown = final_markdown + "</p>"
        final_markdown = final_markdown + "\n \n ---\n\n";
      }

      //Frontend tech
      if(self.all_data.selected_frontend_techs.length > 0) {
        final_markdown = final_markdown + '\n ### Frontend Development \n '
        final_markdown = final_markdown + "<p align='left'>"
        self.all_data.selected_frontend_techs.map(function (item){
          let obj_item = self.all_frontend_tech.filter(function (item_all) { return item == item_all.value});

          final_markdown = final_markdown + '<a><img height="30" width="30" src="' + obj_item[0].icons + '" /></a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'
        });
        final_markdown = final_markdown + "</p>"
        final_markdown = final_markdown + "\n \n ---\n\n";
      }

      //Backend tech
      if(self.all_data.selected_backend_techs.length > 0) {
        final_markdown = final_markdown + '\n ### Backend Development \n '
        final_markdown = final_markdown + "<p align='left'>"
        self.all_data.selected_backend_techs.map(function (item){
          let obj_item = self.all_backend_tech.filter(function (item_all) { return item == item_all.value});

          final_markdown = final_markdown + '<a><img height="30" width="30" src="' + obj_item[0].icons + '" /></a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'
        });
        final_markdown = final_markdown + "</p>"
        final_markdown = final_markdown + "\n \n ---\n\n";
      }


      //Mobile app tech
      if(self.all_data.selected_mobileapp_techs.length > 0) {
        final_markdown = final_markdown + '\n ### Mobile App Development \n '
        final_markdown = final_markdown + "<p align='left'>"
        self.all_data.selected_mobileapp_techs.map(function (item){
          let obj_item = self.all_mobile_tech.filter(function (item_all) { return item == item_all.value});

          final_markdown = final_markdown + '<a><img height="30" width="30" src="' + obj_item[0].icons + '" /></a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'
        });
        final_markdown = final_markdown + "</p>"
        final_markdown = final_markdown + "\n \n ---\n\n";
      }


      //ai/ml tech
      if(self.all_data.selected_aiml_techs.length > 0) {
        final_markdown = final_markdown + '\n ### AI/ML \n '
        final_markdown = final_markdown + "<p align='left'>"
        self.all_data.selected_aiml_techs.map(function (item){
          let obj_item = self.all_ai_ml_tech.filter(function (item_all) { return item == item_all.value});

          final_markdown = final_markdown + '<a><img height="30" width="30" src="' + obj_item[0].icons + '" /></a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'
        });
        final_markdown = final_markdown + "</p>"
        final_markdown = final_markdown + "\n \n ---\n\n";
      }


      //db tech
      if(self.all_data.selected_database_techs.length > 0) {
        final_markdown = final_markdown + '\n ### Database \n '
        final_markdown = final_markdown + "<p align='left'>"
        self.all_data.selected_database_techs.map(function (item){
          let obj_item = self.all_database_tech.filter(function (item_all) { return item == item_all.value});

          final_markdown = final_markdown + '<a><img height="30" width="30" src="' + obj_item[0].icons + '" /></a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'
        });
        final_markdown = final_markdown + "</p>"
        final_markdown = final_markdown + "\n \n ---\n\n";
      }


      //devops tech
      if(self.all_data.selected_devops_techs.length > 0) {
        final_markdown = final_markdown + '\n ### DevOps \n '
        final_markdown = final_markdown + "<p align='left'>"
        self.all_data.selected_devops_techs.map(function (item){
          let obj_item = self.all_devops_tech.filter(function (item_all) { return item == item_all.value});

          final_markdown = final_markdown + '<a><img height="30" width="30" src="' + obj_item[0].icons + '" /></a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'
        });
        final_markdown = final_markdown + "</p>"
        final_markdown = final_markdown + "\n \n ---\n\n";
      }


      //static site generato tech
      if(self.all_data.selected_staticsitegenerator_techs.length > 0) {
        final_markdown = final_markdown + '\n ### Static Site Generator \n '
        final_markdown = final_markdown + "<p align='left'>"
        self.all_data.selected_staticsitegenerator_techs.map(function (item){
          let obj_item = self.all_static_site_generator_tech.filter(function (item_all) { return item == item_all.value});

          final_markdown = final_markdown + '<a><img height="30" width="30" src="' + obj_item[0].icons + '" /></a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'
        });
        final_markdown = final_markdown + "</p>"
        final_markdown = final_markdown + "\n \n ---\n\n";
      }


      //gaming tech
      if(self.all_data.selected_gaming_techs.length > 0) {
        final_markdown = final_markdown + '\n ### Gaming \n '
        final_markdown = final_markdown + "<p align='left'>"
        self.all_data.selected_gaming_techs.map(function (item){
          let obj_item = self.all_gaming_tech.filter(function (item_all) { return item == item_all.value});

          final_markdown = final_markdown + '<a><img height="30" width="30" src="' + obj_item[0].icons + '" /></a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'
        });
        final_markdown = final_markdown + "</p>"
        final_markdown = final_markdown + "\n \n ---\n\n";
      }

      self.markdown = final_markdown;
    },
    copyMarkdownCode(){
      let self = this;
      copyToClipboard(self.markdown)
      .then(() => {
        self.sendMessage('Markdown Code Copied!')
      })
      .catch(() => {
        // fail
      })

    },
    sendMessage(msg){
      this.$q.notify({
          type: 'positive',
          message: msg,
          position: 'bottom-right'
        })
    }
  }
}
</script>
