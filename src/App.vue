<template>
  <div id="app">
     
<input type="text" v-model="channelname" /><button @click="addstream">Add</button>
  
  <vdrag v-for="stream in streams" :key="stream.id" @activated="onActivated($event,stream)"  @deactivated="onDeactivated($event, stream)"   :w="200" :h="400" v-on:resizing="resize($event, stream)" v-on:dragging="resize($event,stream)"   :snapToGrid="true" :gridX="20">
          <Stream :channel="stream.channel"  :w="stream.w" :h="stream.h" :active="stream.active" />
  </vdrag>
  </div>
</template>

<script>
import Stream from './components/Stream.vue'
 import vdrag from 'vue-drag-resize'
export default {
  name: 'App',
  components: {
    vdrag,
    Stream
  },
  data() { 
    return {
      streams: [],
      streamobj: {channel:'summit1g', w:200, h:400, active:true},
      channelname: 'summit1g',

    }
  },
  methods: {
    onActivated: function(evt, stream) {
      stream.active=true;
    },
    onDeactivated: function(evt, stream) {
      stream.active=false;
    },
    addstream: function() {
      this.streams.push({channel: this.channelname, w: 200, h:400, active: true});
    },
     resize(newRect, stream) {  
       stream.w = newRect.width;
       stream.h = newRect.height;
        this.width = newRect.width;
        this.height = newRect.height;
        this.top = newRect.top;
        this.left = newRect.left; 
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
