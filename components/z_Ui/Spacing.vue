<template lang="pug" functional>
div
  center
    h1 Spacing Scale
  dl.gridChart
    template(
      v-for="It in [0.125,0.25,0.375,0.5,0.75,1.25,2,3.25,5.25,8.5,13.75]"
    )
      dt.gridChart_bar(
        :style="`height: ${It}em`"
      )
      dd.gridChart_val {{It}}
</template>

<style lang="stylus" scoped>
h1
  margin 1em 0 -2em

.gridChart
  display: grid;
  align-items: end;
  justify-content: center;

  grid-template-columns: repeat(11, minmax(1em, 3em));
  grid-template-rows: 100px, 1fr;
  grid-gap: .2em 1em;
  padding 2em
//dt
.gridChart_bar
  background #2a6df4
//dd
.gridChart_val
  grid-row-start: 2;
  text-align center
</style>


