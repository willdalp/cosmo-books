<script setup>
import Checkbox from '@/Components/Checkbox.vue';
import GuestLayout from '@/Layouts/GuestLayout.vue';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import { Head, Link, useForm } from '@inertiajs/vue3';

defineProps({
    canResetPassword: {
        type: Boolean,
    },
    status: {
        type: String,
    },
});

const form = useForm({
    email: '',
    password: '',
    remember: false,
});

const submit = () => {
    form.post(route('login'), {
        onFinish: () => form.reset('password'),
    });
};
</script>

<template>
    <GuestLayout>
        <Head title="Log in" />

        <!-- <div v-if="status" class="mb-4 font-medium text-sm text-green-600">
            {{ status }}
        </div> -->

        <form @submit.prevent="submit">
            <div class="main-container">
                <div>
                    <InputLabel for="email" value="Email" />
                    <input
                        id="email"
                        type="email"
                        class="login-button"
                        v-model="form.email"
                        required
                        autofocus
                        autocomplete="username"
                        placeholder="Ex: teste@gmail.com"
                    />
                    <InputError class="mt-2" :message="form.errors.email" />
                </div>
    
                <div class="mt-4">
                    <InputLabel for="password" value="Senha" />
                    <input
                        id="password"
                        type="password"
                        class="login-button"
                        v-model="form.password"
                        required
                        autocomplete="current-password"
                        placeholder="Ex: Senh@F*R&3%2"
                    />
                    <InputError class="mt-2" :message="form.errors.password" />
                </div>
    
                <div class="container-lembrar-recuperar-senha">
                    <label>
                        <Checkbox name="remember" v-model:checked="form.remember" class="checkbox"/>
                        <span>Lembrar login</span>
                    </label>
                    <Link v-if="canResetPassword"
                        :href="route('password.request')"
                        class="recuperar-senha">
                        Recuperar senha
                    </Link>
                </div>
    
                <div class="container-primary-button">
                    <PrimaryButton class="primary-button" :disabled="form. processing">
                        Efetuar Login
                    </PrimaryButton>
                </div>
            </div>
        </form>
    </GuestLayout>
</template>

<style scoped>
    @import url('https://fonts.googleapis.com/css2?family=DM+Sans:ital,opsz,wght@0,9..40,100..1000;1,9..40,100..1000&family=Plus+Jakarta+Sans:ital,wght@0,200..800;1,200..800&display=swap');

    .main-container {
        padding: 30px 40px 0;
    }
    .main-container div:first-child {
        padding-bottom: 1.6rem;
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
    .container-lembrar-recuperar-senha {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-top: 1rem;
    }
    .container-lembrar-recuperar-senha > label > span {
        font-size: 1.2rem;
        padding-left: 0.7rem;
        color: var(--custom-gray);
    }
    .checkbox {
        background-color: #D9D9D9;
    }
    .recuperar-senha {
        font-size: 1.2rem;
        text-decoration: underline var(--primary-300);
        color: var(--custom-gray);
    }
    .container-primary-button {
        padding-top: 50px;
    }
</style>
