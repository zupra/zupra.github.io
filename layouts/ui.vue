<template lang="pug">

#layout


  #topNav
    #burger.ml_2
      svg(
          @click="showSidebar = !showSidebar",
          width='80',
          height='44',
        )
        rect(x="14", y="6", width="30", height="32", fill="rgba(255, 255, 255, .2)")
        g(stroke='white', stroke-width='4')
          path(d='M8,14 L36,14')
          path(d='M8,22 L30,22')
          path(d='M8,30 L24,30')
        polyline(v-if="showSidebar", points="50,10 36,22 50,34", fill="lightsteelblue")


    div
      Dropdown(openTo="toLeft")
        button(slot="btn") Radio
        Radio


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
