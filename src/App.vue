<template>
  <div id="app">
    <h1>Custom Directives</h1>
    <p>You can create your own directives if you need to access the DOM for interactions. If you are not doing an interaction, you are likely better off with a component.
    <br>
    <br>
    Here I'm using a custom video directive, which is one way bound to data in the model, and replacing the directive with an element utilizing the data that it is bound to.
    <br>
    <br>
    Probably better off as a component here because a video is not an interaction. Further the component benefits from the its lifecycle, where as I suspect the directive doesn't have the same... 
    <!-- super late, will get back to this -->
    </p>
    <div v-video="video"></div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data: function () {
    return {
      video: {
        videoID: 'P6g2QbXTpL4',
        width: 500,
        height: 315
      }
    }
  },
  directives: {
    video: function(el, binding) {
      el.innerHTML = '<embed width="' + binding.value.width + '" height="' + binding.value.height + '" src="https://www.youtube.com/embed/' + binding.value.videoID + '">';
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
