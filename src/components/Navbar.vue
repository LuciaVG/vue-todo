<template lang="html">

  <nav>
  <div class="nav-wrapper blue-grey lighten-1 nav">
    <a class="brand-logo center">{{title}}</a>
  </div>
</nav>

</template>

<script>
export default {
  props:{
    title: {
      type: String,
      required: true
    }
  }
}
</script>

<style lang="css">
@import url('https://fonts.googleapis.com/css?family=Oswald');
.nav{
  font-family: 'Oswald', sans-serif;
}
</style>
