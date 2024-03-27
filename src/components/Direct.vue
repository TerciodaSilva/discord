<template>
  <div class="server" :class="{ select: select }" @click="setSelect(), $emit('click', $event)">
    <img src="../assets/dicord-icon.svg">
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
  },
  data() {
    return {
      select: false
    }
  },
  methods: {
    setSelect() {
      this.select = true
    }
  }
}
</script>

<style scoped>

  .server img {
    position: relative;
    width: 27px;
  }

  .server {
    background-color: hsl(223 calc( 1 * 6.7%) 20.6% / 1);
    height: 48px;
    width: 48px;
    border-radius: 100%;
  }

  .select, .server:hover{
    background-color: #5865F2;
    border-radius: 15px;
    transition: .4s;
  }
</style>
