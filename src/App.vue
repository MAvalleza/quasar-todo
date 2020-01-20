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
      div.bg-black
        div.row.items-center
          div.col-3.q-px-md
            q-avatar(color="primary" text-color="white") A
          div.col-8.q-px-sm
            h5.text-white Almond Valleza
          

      q-list(bordered)
        q-item(
          clickable
          v-ripple
          v-for="(item, key) in drawerItems"
          :key="key"
        )
          q-item-section(avatar)
            q-icon(:name="item.icon")
          q-item-section {{ item.title }}

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
      leftDrawerOpen: false,
      drawerItems: [
        { title: 'List' , icon: 'inbox' },
        { title: 'Help', icon: 'help' }
      ]
    }
  }
}
</script>

<style>
</style>
