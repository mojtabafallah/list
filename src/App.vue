<script>



export default {
  data() {
    return {
      key_change: -1,
      edit_mode: false,
      content: '',
      items: []
    }
  },
  methods: {
    add_to_list(text) {
      if (!this.items.includes(text)) {
        this.items.push(text);
        this.content = '';
      }
    },
    remove(value) {
      this.items.splice(this.items.indexOf(value), 1);
    },
    set_value_input(value) {
      this.content = this.items[value];
      this.edit_mode = true;
      this.key_change = value;
    },
    apply_change(new_value) {
      this.items[this.key_change] = new_value;
      this.edit_mode = false;
      this.content = '';
    }
  }
}
</script>

<template>
  <input v-model="content">
  <button v-if="!edit_mode" @click="add_to_list(content)">add</button>
  <button v-else @click="apply_change(content)">Apply</button>
  <li v-for="(item, key) in items">
    {{ item }} <button @click="remove(item)">remove</button>
    <button @click="set_value_input(key)">Edit</button>
  </li>
</template>
