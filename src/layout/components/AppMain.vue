<template>
  <section class="app-main">
    <transition name="fade-transform" mode="out-in">
      <router-view v-if="!alive" :key="key" />
      <keep-alive v-if="alive">
        <router-view :key="key" />
      </keep-alive>
    </transition>
  </section>
</template>

<script>
export default {
  name: 'AppMain',
  computed: {
    key() {
      return this.$route.path
    },
    alive() {
      return this.$route.meta.alive || false
    }
  },
  mounted() {
    console.log(this.$route)
  }
}
</script>

<style scoped>
.app-main {
  /*50 = navbar  */
  min-height: calc(100vh - 50px);
  width: 100%;
  position: relative;
  overflow: hidden;
}
.fixed-header+.app-main {
  padding-top: 50px;
}
</style>

<style lang="scss">
// fix css style bug in open el-dialog
.el-popup-parent--hidden {
  .fixed-header {
    padding-right: 15px;
  }
}
</style>
