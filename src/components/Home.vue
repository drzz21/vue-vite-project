<template>
    <div class="p-4">
        <h1 class="mb-6 text-3xl font-extrabold">Home</h1>
        <p class="mb-6">Name in store is {{ name }}</p>
        <input v-model="newName" type="text" class="border border-gray-600 p-2 rounded">
        <button @click="saveName" class="text-white bg-indigo-600 p-2 rounded">submit</button>
    </div>
</template>

<script setup>
import { useStore } from 'vuex';
import { computed,ref } from 'vue';
import { useRouter } from 'vue-router';

const router = useRouter();
const store = useStore();

const name = computed(() => {
    return store.state.user.name;
})
const newName=ref('');
function saveName(){
    store.dispatch('saveName',newName.value);
    newName.value='';
    router.push('/about');
}
</script>
