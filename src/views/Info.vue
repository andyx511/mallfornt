<template>
    <div>
      hello Info
      <button type="button" @click="add">添加</button>
      <div>{{la}}</div>
    </div>
</template>

<script>
import store from '@/store'
export default {
  name: 'Info',
  store,
  data () {
    return {
      la: store.get('count')
    }
  },
  methods: {
    add () {
      console.log('add Event')
      store.commit('increase')
    }
  }

}
</script>

<style scoped>

</style>
