<template>
  <div class="about">
    <h1>This is an about page</h1>
    <div>{{id}}</div>
  </div>
</template>
<script>
export default {
  name: 'about',
  data () {
    return {
      id: this.$route.query.id
    }
  },
  watch: {
    id: function () {
    }
  },
  methods: {
  },
  created () {
  }
}
</script>

<style>

</style>
