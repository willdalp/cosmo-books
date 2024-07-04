<script setup>
import GuestLayout from '@/Layouts/GuestLayout.vue';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import TextInput from '@/Components/TextInput.vue';
import { Head, useForm } from '@inertiajs/vue3';

defineProps({
    status: {
        type: String,
    },
});

const form = useForm({
    email: '',
});

const submit = () => {
    form.post(route('password.email'));
};
</script>

<template>
    <GuestLayout>
        <Head title="Recuperar senha" />

        <div class="main-container">
            <p class="text-recover-password">
                Para recuperar sua senha, insira o e-mail utilizado no cadastro da sua conta. Enviaremos um link para redefinição da senha.
            </p>
            <div v-if="status" class="mb-4 font-medium text-sm text-green-600">
                {{ status }}
            </div>
            <form @submit.prevent="submit">
                <div>
                    <InputLabel for="email" value="Email" />
                    <TextInput
                        id="email"
                        type="email"
                        class="login-button"
                        v-model="form.email"
                        required
                        autofocus
                        autocomplete="username"
                    />
                    <InputError class="mt-2" :message="form.errors.email" />
                </div>
    
                <div class="container-primary-button">
                    <PrimaryButton :disabled="form.processing">
                        Email Password Reset Link
                    </PrimaryButton>
                </div>
            </form>
        </div>
    </GuestLayout>
</template>

<style scoped>
    .main-container {
        padding: 30px 40px 0;
    }
    .login-button {
        margin-top: 1px;
        width: 100%;
        border-radius: 4px;
        background-color: var(--mix-400);
        color: var(--custom-gray);
        border: none;
        font-size: 1.4rem;
        padding: 1.1rem;
    }
    .login-button::placeholder {
        color: var(--custom-gray);
    }
    .container-primary-button {
        padding-top: 3rem;
    }
    .text-recover-password {
        padding-bottom: 2rem;
        color: #FFFFFF;
        font-size: 1.4rem;
    }
</style>