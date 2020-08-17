<template>
  <ul class="list">
    <li class="item"
      v-for="item in letters"
      :key="item"
      :ref="item"
      @touchStart="handleTouchStart"
      @touchMove="handleTouchMove"
      @touchEnd="handleTouchEnd"
      @click="handleLetterClick"
      >
      {{item}}
    </li>
  </ul>
</template>
<script>
export default {
  name: 'CityAlphabet',
  props: {
    cities: Object
  },
  computed: {
    letters () {
      const letters = []
      for (let i in this.cities) {
        letters.push(i)
      }
      return letters
    }
  },
  data () {
    return {
      touchStatus: false
    }
  },
  methods: {
    handleLetterClick (e) {
      this.$emit('change', e.target.innerText)
    },
    handleTouchStart () {
      this.touchStatus = true
    },
    handleTouchMove () {
      if (this.touchStatus) {
        const startY = this.$refs['A'][0].offsetTop
        console.log(startY)
      }
    },
    handleTouchEnd () {
      this.touchStatus = false
    }
  }
}
</script>
<style lang="stylus" scoped>
@import '~styles/varibles.styl'
  .list
    display: flex
    flex-direction: column
    justify-content: center
    position: absolute
    top: 1.58rem
    right: 0
    bottom: 0
    width: .4rem
    .item
      line-height: .4rem
      color: $bgColor
      text-align: center
</style>
