<template lang="pug">
  q-layout(view="lHh Lpr lFf")
    q-header(elevated)
      q-toolbar.bg-primary
        q-btn(
          flat
          dense
          round
          @click="leftDrawerOpen = !leftDrawerOpen"
          aria-label="Menu"
          icon="menu"
        )
      div.q-px-lg.q-pt-xl.q-mb-md
        div.text-h3 Todo
        div.text-subtitle1 Monday 20 January

    q-drawer(
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      content-class="bg-grey-2"
    )
    q-page-container
      todo-list
</template>

<script>
import TodoList from './components/TodoList.vue'

export default {
  name: 'LayoutDefault',

  components: {
    TodoList
  },

  data () {
    return {
      leftDrawerOpen: false
    }
  }
}
</script>

<style>
</style>
