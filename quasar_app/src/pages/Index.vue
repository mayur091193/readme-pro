<template>
  <div class="mx-auto max-w-7xl q-my-sm  md:flex md:items-center md:justify-between md:space-x-5"
       style="height: 64px !important;">
    <div class="flex items-start space-x-5">
      <div class="flex-shrink-0">
        <div class="relative q-ml-xs cursor-pointer" @click="$router.push({ path: '/' })">
          <img class="h-16 q-ml-md q-mt-sm" src="../assets/logo.png" alt=""/>
        </div>
      </div>

      <div class="pt-1.5">
      </div>
    </div>
    <div
      class="justify-stretch mt-6 flex flex-col-reverse space-y-4 space-y-reverse sm:flex-row-reverse sm:justify-end sm:space-y-0 sm:space-x-3 sm:space-x-reverse md:mt-0 md:flex-row md:space-x-3">

      <div class="border-r-2 q-pr-lg inline-flex items-center justify-center"><a
        class="text-weight-bold text-h6 text-indigo-600 hover:text-indigo-500" target="_blank"
        href="https://github.com/mayur091193/readme-pro" style="text-decoration: none;">
        <q-icon name="star" color="yellow-10" size="23px" class="q-mr-xs q-mb-xs"/>
        Star this Repo!</a></div>
      <div class="border-r-2 q-pr-lg q-pl-md inline-flex items-center justify-center"><a
        class="text-weight-bold text-h6 text-indigo-600 hover:text-indigo-500" target="_blank"
        href="https://github.com/mayur091193/readme-pro/issues" style="text-decoration: none;">Report Issue</a></div>
      <div class="border-r-2 q-pr-lg q-pl-md inline-flex items-center justify-center"><a
        class="text-weight-bold text-h6 text-indigo-600 hover:text-indigo-500" target="_blank"
        href="https://github.com/sponsors/mayur091193" style="text-decoration: none;">Support</a></div>
      <div class="q-pl-md inline-flex items-center justify-center"><a target="_blank"
                                                                      href="https://github.com/mayur091193/readme-pro"
                                                                      class="text-h6 text-indigo-600 hover:text-indigo-500"
                                                                      style="text-decoration: none; "><i
        aria-hidden="true" role="presentation" class="cursor-pointer fab fa-github q-icon notranslate"
        style="font-size: 25px;"> <!----></i></a></div>
    </div>
  </div>

  <!-- This example requires Tailwind CSS v2.0+ -->
  <div class="relative overflow-hidden bg-white" :style="{'height':available_height}">
    <div class="mx-auto max-w-7xl" :style="{'height':available_height}">
      <div class="relative z-10 bg-white pb-8 sm:pb-16 md:pb-20 lg:w-full lg:max-w-2xl lg:pb-28 xl:pb-32"
           :style="{'height':available_height}">
<!--        <svg class="absolute inset-y-0 right-0 h-full w-48 translate-x-1/2 transform text-white lg:block"-->
<!--             fill="currentColor" viewBox="0 0 100 100" preserveAspectRatio="none" aria-hidden="true">-->
<!--          <polygon points="50,0 100,0 50,100 0,100"/>-->
<!--        </svg>-->


        <div class="relative px-4 pt-6 sm:px-6 lg:px-8">
          <nav class="relative flex items-center justify-between sm:h-10 lg:justify-start" aria-label="Global">
            <div class="flex flex-shrink-0 flex-grow items-center lg:flex-grow-0">
              <div class="flex w-full items-center justify-between md:w-auto">
                <a href="#">
                  <span class="sr-only">Your Company</span>
                  <!--                  <img alt="Your Company" class="h-8 w-auto sm:h-10" src="https://tailwindui.com/img/logos/mark.svg?color=indigo&shade=600">-->
                </a>
                <div class="-mr-2 flex items-center md:hidden">
                  <button type="button"
                          class="inline-flex items-center justify-center rounded-md bg-white p-2 text-gray-400 hover:bg-gray-100 hover:text-gray-500 focus:outline-none focus:ring-2 focus:ring-inset focus:ring-indigo-500"
                          aria-expanded="false">
                    <span class="sr-only">Open main menu</span>
                    <!-- Heroicon name: outline/bars-3 -->
                    <svg class="h-6 w-6" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24"
                         stroke-width="1.5" stroke="currentColor" aria-hidden="true">
                      <path stroke-linecap="round" stroke-linejoin="round"
                            d="M3.75 6.75h16.5M3.75 12h16.5m-16.5 5.25h16.5"/>
                    </svg>
                  </button>
                </div>
              </div>
            </div>
            <div class="hidden md:ml-10 md:block md:space-x-8 md:pr-4">
              <a href="#" class="font-medium text-gray-500 hover:text-gray-900">Product</a>

              <a href="#" class="font-medium text-gray-500 hover:text-gray-900">Features</a>

              <a href="#" class="font-medium text-gray-500 hover:text-gray-900">Marketplace</a>

              <a href="#" class="font-medium text-gray-500 hover:text-gray-900">Company</a>

              <a href="#" class="font-medium text-indigo-600 hover:text-indigo-500">Log in</a>
            </div>
          </nav>
        </div>

        <main class="mx-auto max-w-7xl px-4  sm:px-6 lg:px-8">
          <div class="sm:text-center lg:text-left">
            <h1 class="text-3xl font-bold tracking-tight text-gray-900 sm:text-5xl">
              <span class="block q-mt-md xl:inline">Best and Easy way to</span>
              <span class="block text-indigo-600 xl:inline">Create Readme</span>
            </h1>
            <p class="mt-12 mb-14  text-base text-gray-500 sm:mx-auto sm:max-w-xl sm:text-lg md:text-xl lg:mx-0"><span>Readme Pro</span>
              provides the easiest way to create readme file which you can use at many places like github personal
              profile, documentation and much more. <br/><br/> Choose from lots of <span class="text-indigo-600">ready templates</span>
              to get started!</p>
            <div class="sm:flex sm:justify-center lg:justify-start">
              <div class="rounded-md shadow">
                <a @click="$router.push({ path: '/main' })"
                   class="cursor-pointer flex w-full items-center justify-center rounded-md border border-transparent bg-indigo-600 px-4 py-3 text-base font-medium text-white hover:bg-indigo-700  md:text-lg">Readme
                  Generator</a>
              </div>
              <div class="rounded-md q-ml-md shadow">
                <a @click="$router.push({ path: '/github-profile-generator' })"
                   class="cursor-pointer flex w-full items-center justify-center rounded-md border border-transparent px-4 py-3 text-base font-medium  md:text-lg bg-indigo-100 text-indigo-700 hover:bg-indigo-200">
                  <i aria-hidden="true"
                     role="presentation"
                     class="cursor-pointer  q-mr-sm fab fa-github q-icon notranslate" style="font-size: 25px;"> </i>
                  GitHub Profile Generator </a>
              </div>
              <!--            <div class="mt-3 sm:mt-0 sm:ml-3">-->
              <!--              <a href="#" class="flex w-full items-center justify-center rounded-md border border-transparent bg-indigo-100 px-8 py-3 text-base font-medium text-indigo-700 hover:bg-indigo-200 md:py-4 md:px-10 md:text-lg">Live demo</a>-->
              <!--            </div>-->
            </div>
            <div class="q-my-xl  q-pt-sm q-mt-xs">
              <div class="text-center text-h5">
                <div class="q-mr-md q-py-sm text-weight-bold text-grey-7">
                  Hand-crafted with
                  <i aria-hidden="true" role="presentation" class="fa fa-heart q-icon notranslate"
                     style="font-size: 26px; color: rgb(226, 85, 85);"> </i>
                  by
                  <a target="_blank" href="https://github.com/mayur091193" class="text-indigo-600 hover_underline_white"
                     style="text-decoration: none; ">Mayur Patel</a></div>
              </div>
            </div>
          </div>
        </main>
      </div>
    </div>
    <div class="lg:absolute q-px-xl lg:inset-y-0 lg:right-0 lg:w-1/2" :style="{'height':available_height}">
      <img :style="{'height':parseInt(available_height)-26 + 'px'}" class="q-mb-md w-full lg:w-full"
           src="../assets/demo_image.jpeg"
           alt="">
    </div>
  </div>

  <!--  <div  class="q-my-xl  q-pt-sm q-mt-xs"><div  class="text-center text-h5"><div class="q-mr-md q-py-sm text-weight-bold text-grey-7">-->
  <!--        Hand-crafted with-->
  <!--        <i aria-hidden="true" role="presentation" class="fa fa-heart q-icon notranslate" style="font-size: 26px; color: rgb(226, 85, 85);"> </i>-->
  <!--        by-->
  <!--        <a target="_blank" href="https://github.com/mayur091193" class="text-indigo-600 hover_underline_white" style="text-decoration: none; ">Mayur Patel</a></div></div></div>-->

</template>

<style lang="sass">

.q-markdown
  position: relative

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

export default {
  name: 'Index',
  data() {
    return {
      available_height: 0
    }
  },
  mounted() {
    this.available_height = (window.innerHeight - 80) + 'px';
  },
  methods: {
    openUrl(url) {
      window.open(url, "_blank");
    }
  }
}
</script>
