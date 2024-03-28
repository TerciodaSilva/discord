<template>
  <div class="container">
    <div class="line" :class="{'line-off': !enable, 'line-on': enable, hover: hover && !enable }"></div>
    <div class="box-server">
      <div class="server" 
        @mouseover="this.setHover" 
        @mouseout="this.outHover" 
        :class="{ select: enable}" 
        @click="$emit('click', $event)">
        <h1>A</h1>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'EventosServidor',
  props: {
    enable: {
      type: Boolean,
      default: false
    }
  },

  data() {
    return {
      hover: false
    }
  },

  methods: {
    setHover() {
      if(!this.enable) this.hover = true
    },
    outHover() {
      this.hover = false;
    }
  }
}

</script>

<style scoped>

  @font-face {
      font-family: Gg sans;
      src:url("/fonts/gg sans Regular.ttf");
  }

  .server {
    display: flex;
    background-color: hsl(223 calc( 1 * 6.7%) 20.6% / 1);
    height: 48px;
    width: 48px;
    border-radius: 100%;
    position: relative;
    cursor: pointer;
    color: #23A559;
    justify-content: center;
    align-items: center;
    font-family: "Gg sans";
    font-size: 10px;
    transition: .4s;
  }

  .select, .server:hover{
    background-color: #23A559;
    color: aliceblue;
    border-radius: 15px;
    transition: .4s;
  }

  .server:active {
    animation: select .4s;
  }

  .box-server {
    display: flex;
    margin: 0;
    height: 50px;
  }

  .line {
    background-color: aliceblue;
    width: 4px;
    height: 0px;
    border-radius: 0 10px 10px 0;
    position: fixed;
    left: 0;
    transition: .4s;
  }

  .line-off {
    height: 0px;
  }

  .line-on {
    height: 42px;
  }

  .hover {
    background-color: aliceblue;
    width: 5px;
    height: 20px;
    border-radius: 0 10px 10px 0;
    position: fixed;
    transition: .4s;
    left: 0;
  }

  .container {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  
  @keyframes select 
  {
    0% {
      margin-top: 2px;
    }
    100% {
      margin-top: 0px;
    }
  }

</style>
