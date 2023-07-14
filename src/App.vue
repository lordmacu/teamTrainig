<template>
    <div>
        <div style="background-color: yellow;">Mensg: {{msg}} <button @click="callFromParent">Call Child method</button></div>
        <HelloWorld ref="child" @fromChild="fromChild" :type="10" msg="Welcome to Your Vue.js App"/>
    </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data: function () {
    return {
        msg:''
    }
  },
  methods: {
    fromChild(value) {
        this.msg = value.msg
        console.log('fromChild ',value)
    },
    callFromParent() {
        this.$refs.child.callFromParent('valor desde el padre');
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
