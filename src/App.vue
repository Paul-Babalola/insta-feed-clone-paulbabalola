<template>
  <Header />
  <Stories />
  <Body />
  <RightSide />

</template>

<script>
import Header from './components/InstagramHeader.vue';
import Stories from './components/InstagramStories.vue';
import Body from './components/InstagramBody.vue';
import RightSide from './components/InstagramSide.vue';

export default {
  name: 'App',
  components: {
    Header,
    Stories,
    Body,
    RightSide
  }
}
</script>

<style>
  body {
    font-family: 'Roboto', sans-serif;
    background-color: #f9f9f9;
  }
</style>