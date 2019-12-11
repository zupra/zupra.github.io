<template lang="pug">

#layout

  transition(name="slideSidebar")
    #sidebar(v-show="showSidebar")
      .scrollableArea

        nav
          nuxt-link(to="/")
            svg(width="26", height="24")
              path(d="M10,20V14H14V20H19V12H22L12,3L2,12H5V20H10Z")
            | Home

        //-
        nav
          h4 Принципы

          //- :to="{ path:'/UI', hash:`#${hash}`}"
          //- :href="`/UI#${hash}`"
          a(
            v-for="hash,i in hashNav",
            :href="`/UI#${hash}`"
            :key="i"
            :class="{hashActive:i == hashActive}"
            @click="hashActive = i"
          ) {{hash}}


        nav
          h4 Принципы

          //- :to="{ path:'/UI', hash:`#${hash}`}"
          //- :href="`/UI#${hash}`"
          a(
            v-for="hash,i in hashNav",
            :href="`/UI#${hash}`"
            :key="i"
            :class="{hashActive:i == hashActive}"
            @click="hashActive = i"
          ) {{hash}}

        nav
          h4 тестовые страницы
          nuxt-link(v-for="link in pages", :to="link.url", :key="link.url" ) {{link.name}}
        //- nav
        //-   h3 test megaMenu
        //-   each _,i in Array(30)
        //-     a(href="#") link #{i+1}
        br

  //- MAIN
  #main
    .scrollableArea
      <nuxt/>

</template>

<script>
import Radio from '~/components/Radio.vue'
import Dropdown from '~/components/Dropdown/Dropdown.vue'

const hashNav = [
  'Цвет',
  'Spacing',
  'Shadow',
  'Buttons',
  'Typography',
  'Иконки',
  'Table',
  // 'MaskedInput',
  'Input_Prepend',
  'Input_ReadonlyTgl',
  'Input_Star',
  'Input_Number',
  'Input_Switch',
  'Dropdown',
  'UiSelect',
  'BigSelect_many',
  'Pagination',
  'Card',
  'Calendar',
  'Modal',
  'Expander',

  'Checkbox-Radio',
  'Input-EL',
]

export default {
  // middleware: 'user',
  components: {
    Radio,
    Dropdown
  },
  data () {
    return {
      hashNav,
      hashActive: null,
      showSidebar: true,
      pages: [
        { url: '/test_WS', name: 'WS' },
        { url: '/test_imgCropper', name: 'image Cropper' },
        { url: '/test_notice', name: 'Notice list' },
        { url: '/test_valid', name: 'Валидация форм' },
        { url: '/test_grid', name: 'Grid' }
      ]
    }
  }
}
</script>

<style lang="stylus">
#sidebar .hashActive
  color #FFF
  background cornflowerblue
</style>
