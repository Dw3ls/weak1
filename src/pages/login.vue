<script setup lang="ts">
    import { useAuthStore } from '@/stores/auth';
    import { ref } from 'vue';
    import { useRouter } from 'vue-router';

    const auth = useAuthStore()
    const username = ref('')
    const password = ref('')
    const router = useRouter()

    const onLogin = () => {
        const validUsername = 'admin'
        const validPassword = '12345'

        if (username.value === validUsername && password.value === validPassword) {
            auth.login(username.value)
            router.push('/')
        } else {
            window.alert('Username atau password salah')
        }
    }
</script>

<template>
    <div>
        <h1>Login Page</h1>
        <div class="flex flex-col gap-2">
            <input type="text" v-model="username" class="border p-2" placeholder="Username" />
            <input type="password" v-model="password" class="border p-2" placeholder="Password" />
            <button @click="onLogin" class="bg-blue-500 text-white py-1 px-3">Login</button>
        </div>
    </div>
</template>