<template>
    <form @submit.prevent="onSubmit">
        <textarea v-model="body" required placeholder="Type tweet here" />
        <button class="btn btnTweet" type="submit">Post Tweet</button>
    </form>
</template>
  
<script>
import { ref } from 'vue';
export default {
    setup(_, { emit }) {
        const body = ref('');

        function onSubmit() {
            emit('onSubmit', {
                id: Math.round(Math.random() * 30),
                avatar: `https://api.dicebear.com/7.x/croodles/svg?seed=${Date.now()}`,
                body: body.value,
                likes: 0,
                date: new Date(Date.now()).toLocaleString()
            })
            body.value = '';
        }

        return{body, onSubmit};
    }
}
</script>