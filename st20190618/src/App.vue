<template>
  <div id="app">
    <h2>20190618 Using Event Bus</h2>
    <control-area></control-area>
    <view-area ></view-area>
  </div>
</template>

<script>
import ViewArea from './components/ViewArea.vue'
import ControlArea from './components/ControlArea.vue'

export default {
  name: 'app',
  components: {
    ViewArea,
    ControlArea
  }
}
</script>

<style>
  @font-face {
    font-family: 'makdae';
    src: url('font/HoonMakdaeyunpilR.ttf') format('truetype');
  }
  @font-face {
    font-family: 'yanolza';
    src: url('font/야놀자 야체 Regular.ttf') format('truetype');
  }
  * { margin: 0; padding: 0; }
  body {
    padding: 20px;
    background: #f6f6f6;
  }
  h2 {
    margin: 20px 0;
    color: #aaa;
  }
</style>
