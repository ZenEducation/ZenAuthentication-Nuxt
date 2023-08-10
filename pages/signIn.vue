<template>
    <div class="container">
        <h1>Login here</h1>
        <form class="form" @submit.prevent="handleSubmit">
            <div class="form-group">
                <label for="email">Email:</label>
                <input v-model="formData.email" type="text" id="email" name="email" required />
                <label for="password">Password:</label>
                <input v-model="formData.password" type="password" id="password" name="password" required />
            </div>
            <button type="submit">Submit</button>
        </form>
    </div>
</template>
<style scoped>
.container {
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    align-items: center;
    /* margin-top: 20px; */
}

h1 {
    font-size: 24px;
    margin-bottom: 20px;
}

.main {
    display: flex;
    flex-direction: column;
    height: 100vh;
    justify-content: center;
    align-items: center;
}

.form {
    display: flex;
    flex-direction: column;
    width: 380px;
}

.form-group {
    display: flex;
    flex-direction: column;
    margin-bottom: 15px;
}

label {
    font-size: 16px;
    margin-bottom: 5px;
}

input,
textarea {
    padding: 8px;
    font-size: 16px;
    border: 1px solid #ccc;
    border-radius: 4px;
}

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
import { ref } from 'vue';
import { Auth } from 'aws-amplify';
import awsExports from '../src/aws-exports'; // Update the path to aws-exports.js
// import { useRoute } from '@nuxtjs/composition-api';

Auth.configure(awsExports);

const formData = ref({
    email: '',
    password: '',
});
// const route = useRoute();

const handleSubmit = async () => {
    try {
        const user = await Auth.signIn(formData.value.email, formData.value.password);
        if (user) {
            localStorage.setItem('authToken', user.signInUserSession.accessToken.jwtToken);
            localStorage.setItem('name', user.attributes.name);
            window.alert('Successfully logged In');
            console.log('logged in successfully', user);
            // route.push('/profile');
            window.location.replace("http://localhost:3000/profile");
        }
    } catch (error) {
        const obj = {
            status: true,
            message: error,
        };
        console.log('error', error);
        // setErrorMsg(obj);
    }
};
</script>
