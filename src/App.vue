<template>
  <div class="wrapper">
    <div class="wrapper-content">
      <div class="view">
        <div class="container">
          <Form @onSubmit="handleSubmit"/>
          <List :items="items" />
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import {ref} from 'vue';
import Form from './components/Form.vue';
import List from './components/List.vue';
export default {
  components: {
    Form,
    List
  },
  setup() {
    const items = ref([
      {
        id: 1,
        body: 'hello, vue 3',
        likes: 12,
        avatar: `https://api.dicebear.com/7.x/croodles/svg?seed=${Math.random()}`,
        date: new Date(Date.now()).toLocaleString()
      },
      {
        id: 2,
        body: 'hello, world',
        likes: 10,
        avatar: `https://api.dicebear.com/7.x/croodles/svg?seed=${Math.random()}`,
        date: new Date(Date.now()).toLocaleString()
      }
    ]);

    function handleSubmit(item) {
      items.value.push(item)
    }

    return{items, handleSubmit}

  }
}
</script>
<style></style>