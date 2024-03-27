<template>
  <div class="container">
    <div class="line" :class="{'line-off': !select, 'line-on': select, hover: hover}"></div>
    <div class="box-server">
      <div class="server" @mouseover="this.setHover" @mouseout="this.outHover" :class="{ select: select}" @click="this.setSelect">
        <h1>A</h1>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
  },
  data() {
    return {
      select: false,
      hover: false
    }
  },
  methods: {
    setSelect() {
      this.select = true
      this.outHover()
    },
    setHover() {
      if(!this.select) this.hover = true
    },
    outHover() {
      this.hover = false;
    },
    test() {
      console.log("Leave")
    }
  }
}
</script>

<style>
  @font-face {
      font-family: gg;
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
    color: white;
    justify-content: center;
    align-items: center;
    font-family: "gg";
    font-size: 10px;
    transition: .4s;
  }

  .select, .server:hover{
    background-color: #5865F2;
    border-radius: 15px;
    transition: .4s;
  }

  .select:active {
    margin-top: 10px;
  }

  .box-server {
    display: flex;
    margin: 0;
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


</style>
