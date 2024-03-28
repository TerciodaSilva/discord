<template>
  <div class="menu-server">
    <Direct :id="this.directItems.id" v-bind:enable="this.directItems.status" @click="setDirect()"/>
    <hr/>
    <li v-for="item in this.items" :key="item.id">
      <Server :id="item.id" v-bind:enable="item.status" @click="setSelect(item.id)"/>
    </li>
  </div>
</template>

<script>

import Server from "@/components/Server.vue"
import Direct from "@/components/Direct.vue"

export default {
  name: 'PageInit',
  data () {
    return {
      directItems: {
        id: 0,
        status: true
      },
      items: [
        { 
          id: 1,
          status: false 
        },
        { 
          id: 2,
          status: false 
        }
      ]
    }
  },

  components: {
    Server,
    Direct    
  },

  methods: {
    disable(variable) {
      variable.status = false;
    },
    enable(variable) {
      variable.status = true
    },
    setDirect() {
      this.items.forEach((item) => { this.disable(item) })
      this.enable(this.directItems)  
    },
    setSelect(id) {
      this.disable(this.directItems)
      this.items.forEach((item) => { (item.id === id) ? this.enable(item) : this.disable(item)})
    }
  }
}

</script>

<style scoped>

  li {
    list-style: none;
  }

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
