<template>
    <div class="container">
        <form id="loginForm">
            <div class="form-floating mb-3">
                <label class="form-label" for="username">Username</label>
                <input class="form-control" placeholder="Username" type="username" id="username" name="username" v-model="username" required>
            </div>
            <div class="form-floating mb-3">
                <label class="form-label" for="password">Password</label>
                <input class="form-control" placeholder="Password" type="password" id="password" name="password" v-model="password" required>
            </div>
            <div class="center-horizontal">
                <button class="btn btn-primary" type="button" @click="submitForm">Login</button>
            </div>
        </form>
    </div>
</template>

<script setup lang="ts">
    const username = ref('');
const password = ref('');
async function submitForm() {
    try {
        const loginResult = await login(username.value, password.value)
        console.log(loginResult)
    } catch (error) {
        console.error("error:", error);
        // (document.getElementById("error-message") as HTMLParagraphElement).innerText = "An error occurred.";
    }
}
</script>

<style>
.center-horizontal {
    position: relative;
    left: 40%;
}
</style>
