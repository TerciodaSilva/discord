<template>
  <div class="menu-server">
    <Direct id="0" @click="changeServer()"/>
    <hr/>
    <Server id="1"/>
    <Server id="2"/>
    <Server id="3"/>
    <Server id="4"/>
  </div>
</template>

<script>

import Server from "@/components/Server.vue"
import Direct from "@/components/Direct.vue"

export default {
  name: 'App',
  components: {
    Server,
    Direct
  },
  methods: {
    changeServer() {
      console.log("Hello")
    },
  }

}
</script>

<style scoped>
  .menu-server {
    display: flex;
    align-items: center;
    flex-direction: column;
    background-color: #1E1F22;
    height: 100vh;
    width: 72px;
    gap: 10px;
    padding-top: 10px;
  }

  hr {
    border: 1px solid hsl(223 calc( 1 * 6.7%) 20.6% / 1);
    width: 30px;
    border-radius: 100px;
  }
</style>
