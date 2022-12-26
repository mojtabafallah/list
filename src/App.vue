<script>
import { remove } from '@vue/shared';


export default {
  data() {
    return {
      content: '',
      items: []
    }
  },
  methods: {
    add_to_list(text) {
      if(!this.items.includes(text)){
        this.items.push(text);
        this.content = '';
      }
    },
    remove(value) {
      this.items.splice(this.items.indexOf(value), 1);  
    }
  }
}
</script>

<template>
  <input v-model="content">
  <button @click="add_to_list(content)">add</button>
  <li v-for="item in items">
    {{ item }} <button @click="remove(item)">remove</button>
  </li>
</template>