<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
//@ts-ignore
import InputCheckbox from './components/InputCheckbox.vue'
//@ts-ignore
import InputForm from './components/InputForm.vue'
//@ts-ignore
import SubmitButton from './components/SubmitButton.vue'
import { ref } from 'vue'
import * as yup from 'yup'

const section = ref<String>("signin")

const goTo = (name: String) => {
    section.value = name;
}

const username = ref('')
const email = ref('')
const password = ref('')

const errors = ref({})

const schemaLogin = yup.object().shape({
    password: yup.string().required().min(8, 'Password minimal 8 huruf'),
    username: yup.string().required().min(4, 'Username minimal 4 huruf')
})

const schemaSignup = yup.object().shape({
    password: yup.string().required().min(8, 'Password minimal 8 huruf'),
    email: yup.string().required().email(),
    username: yup.string().required().min(4, 'Username minimal 4 huruf')
})

const submitLogin = () => {
    console.log("test", username.value)
    schemaLogin.validate({
        username: username.value,
        password: password.value
    })
        .then((value) => {
            alert("success")
            errors.value = ('')
        })
        .catch((error) => {
            errors.value = error.errors
            console.log(errors)
        })
}

const submitSignup = () => {
    console.log("test", username.value)
    schemaSignup.validate({
        username: username.value,
        email: email.value,
        password: password.value
    })
    .then((value) => {
        alert("success")
        errors.value = ('')
    })
    .catch((error) => {
        errors.value = error.errors
        console.log(errors)
    })
}

</script>

<template>
    <!-- component -->
    <section class="absolute w-full h-full top-0">
        <div class="absolute top-0 w-full h-full bg-cyan-900"></div>
        <div class="container mx-auto px-4 h-full">
            <div class="flex content-center items-center justify-center h-full">
                <div class="w-full lg:w-4/12 px-4 pt-8">
                    <div
                        class="relative flex flex-col min-w-0 break-words w-full mb-6 shadow-lg rounded-lg bg-slate-900 border-0"
                    >
                        <div class="rounded-t mb-0 px-8 lg:px-14 py-10">
                            <div class="btn-wrapper text-left">
                                <SubmitButton
                                    type="button"
                                    variant="tertiary"
                                    class="uppercase mr-4 mb-1 uppercase active:underline underline-offset-8 decoration-2 decoration-blue-700 font-medium text-lg"
                                    @click="goTo('signin')"
                                    text="Sign In"
                                />
                                <SubmitButton
                                    type="button"
                                    variant="tertiary"
                                    class="uppercase mr-4 mb-1 uppercase active:underline underline-offset-8 decoration-2 decoration-blue-700 font-medium text-lg"
                                    @click="goTo('signup')"
                                    text="Sign Up"
                                />
                            </div>
                            <div v-for="error in errors" :key="error">
                                <p class="text-red-700 text-s font-light ">{{ error }}</p>
                            </div>
                        </div>

                        <!-- v-if models Section -->
                        <div v-if="section === 'signin'" class="flex-auto px-4 lg:px-10 py-10 pt-0">
                            <form>
                                <div class="relative w-full mb-3">
                                    <InputForm
                                        v-model="username"
                                        label="Username"
                                        placeholder="Username"
                                        type="username"
                                    />
                                </div>
                                <div class="relative w-full mb-3">
                                    <InputForm
                                        v-model="password"
                                        label="Password"
                                        placeholder="Password"
                                        type="password"
                                    />
                                </div>
                                <div>
                                    <InputCheckbox 
                                        class="mt-4 ml-4" 
                                        text="Remember Me" 
                                    />
                                </div>
                                <div class="text-center mt-6">
                                    <SubmitButton
                                        type="button"
                                        variant="primary"
                                        class="shadow hover:shadow-lg uppercase mr-1 mb-1 w-full font-bold rounded-full text-sm"
                                        @click="submitLogin"
                                        text="Sign In"
                                    />
                                </div>
                            </form>
                        </div>

                        <div v-if="section === 'signup'" class="flex-auto px-4 lg:px-10 py-10 pt-0">
                            <form>
                                <div class="relative w-full mb-3">
                                    <InputForm
                                        v-model="username"
                                        label="Username"
                                        placeholder="Username"
                                        type="username"
                                    />
                                </div>
                                <div class="relative w-full mb-3">
                                    <InputForm
                                        v-model="email"
                                        label="Email"
                                        placeholder="Email"
                                        type="email"
                                    />
                                </div>
                                <div class="relative w-full mb-3">
                                    <InputForm
                                        v-model="password"
                                        label="Password"
                                        placeholder="Password"
                                        type="password"
                                    />
                                </div>
                                <div>
                                    <InputCheckbox 
                                        class="mt-4 ml-4" 
                                        text="Remember Me" 
                                    />
                                </div>
                                <div class="text-center mt-6">
                                    <SubmitButton
                                        type="button"
                                        variant="primary"
                                        class="shadow hover:shadow-lg uppercase mr-1 mb-1 w-full font-bold rounded-full text-sm"
                                        @click="submitSignup"
                                        text="Sign Up"
                                    />
                                </div>
                            </form>
                        </div>
                    </div>
                    <div class="flex flex-wrap mt-6">
                        <div class="w-1/2">
                            <a href="#pablo" class="text-gray-300">
                                <small>Forgot password?</small>
                            </a>
                        </div>
                        <div class="w-1/2 text-right">
                            <a href="#pablo" class="text-gray-300">
                                <small>Create new account</small>
                            </a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<style>
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
/* * {
  background-color: #2c3e50;
} */
</style>
