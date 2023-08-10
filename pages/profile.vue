<template>
    <div style="display: flex; justify-content: center; align-items: center; height: 100vh;">
        <div style="width: 100vw;>
            <h1 style="text-align: center; font-size: 2.5rem;">Profile</h1>
            <p style="text-align: center; font-size: 1.5rem; padding: 10px;">Hi {{ name }}! Welcome to your profile</p>
            <!-- <div style="display: flex; justify-content: center; align-items: center;"> -->
            <nuxt-link to="/" style="display: flex; justify-content: center;">
                <button style="width: 360px;">Sign Out</button>
            </nuxt-link>
            <!-- </div> -->
        </div>
    </div>
</template>
<template>
  <div style="display: flex; justify-content: center; align-items: center; height: 100vh;">
    <div>
      <h1 style="text-align: center; font-size: 2.5rem;">Profile</h1>
      <p style="text-align: center; font-size: 1.5rem; padding: 10px;">Hi {{ name }}! Welcome to your profile</p>
      <div style="display: flex; justify-content: center; align-items: center;"></div>
      <nuxt-link to="/">
        <button style="width: 380px;">Sign Out</button>
      </nuxt-link>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { useRoute } from '@nuxtjs/composition-api';

const name = ref('');
const route = useRoute();

onMounted(() => {
  name.value = localStorage.getItem('name');
});
</script>
<style scoped>

button {
    padding: 10px 15px;
    background-color: #007bff;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    font-size: 16px;
}

button:hover {
    background-color: #0056b3;
}
</style>
<script setup>
import { ref, onMounted } from 'vue';
// import { useRoute } from '@nuxtjs/composition-api';

const name = ref('');
// const route = useRoute();

onMounted(() => {
    name.value = localStorage.getItem('name');
});
</script>
