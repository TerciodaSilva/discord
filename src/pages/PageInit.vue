<template>
  <div class="menu-server">
    <Server 
      :id="this.directItems.id" 
      :enable="this.directItems.status"
      :color="this.directItems.color"
      image="img/assets/dicord-icon.svg"
      @click="setDirect()"/>
    <hr/>
    <li v-for="item in this.items" :key="item.id">
      <Server :id="item.id" :enable="item.status" @click="setSelect(item.id)" :color="item.color" />
    </li>
    <hr/>
    <Server :id="10" :enable="s" @click="setSelect(item.id)" title="B"/>
    <EventosServidor/>
  </div>
</template>

<script>

import Server from "@/components/Server.vue"
import EventosServidor from "@/components/EventosServidor"

export default {
  name: 'PageInit',
  data () {
    return {
      directItems: {
        id: 0,
        status: true,
        color: '#5865F2'
      },
      items: [
        { 
          id: 1,
          status: false,
          color: '' 
        },
        { 
          id: 2,
          status: false,
          color: '' 
        }
      ]
    }
  },

  components: {
    Server,
    EventosServidor    
  },

  methods: {
    disable(variable) {
      variable.status = false;
      variable.color = '';
    },
    enable(variable) {
      variable.status = true
      variable.color = '#5865F2';
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
