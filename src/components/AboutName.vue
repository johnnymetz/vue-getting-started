<template>
  <div class="about">
    <h1>Hello {{ name }}! This is an about page</h1>
    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna ali blah blah blah...</p>
  </div>
</template>


<script>
export default {
  data() {
    console.log(this.$route);
    return {
      name: this.$route.params.name
    }
  }
}
</script>