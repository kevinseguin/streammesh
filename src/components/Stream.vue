<template>
<div>
  <span v-if="active">{{channel}}</span>
 <iframe id="embed" :src="`https://player.twitch.tv/?muted=false&channel=${channel}`" class="stream" :width="w" :height="h" allowfullscreen="true"></iframe> 
</div>
</template>

<script>
export default {
    name: 'Stream',
  props: {
    channel: String,
    w:Number,
    h:Number,
    active:String
  }
}
</script>

<style>

</style>