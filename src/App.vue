<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import SignButton from './components/SignButton.vue'
import InputForm from './components/InputForm.vue'
import { ref } from 'vue'
import * as yup from 'yup'


const section = ref("signin")



const goTo = (name) => {
    section.value = name;
}

const username = ref('')
const password = ref('')

const errors = ref({})

const schemaLogin = yup.object().shape({
    password: yup.string().required().min(8),
    username: yup.string().required().min(4)
})

const submit = () => {
    console.log("test", username.value)
    schemaLogin.validate({
        username: username.value,
        password: password.value
    })
    .then((value) => {
        alert("success")
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
                <div class="w-full lg:w-4/12 px-4 pt-32">
                    <div
                        class="relative flex flex-col min-w-0 break-words w-full mb-6 shadow-lg rounded-lg bg-gray-300 border-0"
                    >
                        <div class="rounded-t mb-0 px-4 lg:px-10 py-10">
                            <div class="btn-wrapper text-left">
                                <SignButton
                                    @click="goTo('signin')"
                                    text="Sign In"
                                />
                                <SignButton
                                    @click="goTo('signup')"
                                    text="Sign Up"
                                />
                            </div>
                        </div>

                        <!-- v-if models Section -->
                        <div v-if="section === 'signin'" class="flex-auto px-4 lg:px-10 py-10 pt-0">
                            <div v-for="error in errors" :key="error">{{ error }}</div>
                            <form>
                                <div class="relative w-full mb-3">
                                    <InputForm
                                        v-model="username"
                                        label="Username"
                                        placeholder="username"
                                        type="email"
                                    />
                                </div>
                                <div class="relative w-full mb-3">
                                    <InputForm
                                        v-model="password"
                                        label="Password"
                                        placeholder="password"
                                        type="password"
                                    />
                                </div>
                                <div>
                                    <label class="inline-flex items-center cursor-pointer">
                                        <input
                                            id="customCheckLogin"
                                            type="checkbox"
                                            class="form-checkbox text-gray-800 ml-1 w-5 h-5"
                                            style="transition: all 0.15s ease 0s;"
                                        />
                                        <span
                                            class="ml-2 text-sm font-semibold text-gray-700"
                                        >Remember me</span>
                                    </label>
                                </div>
                                <div class="text-center mt-6">
                                    <button
                                        @click="submit"
                                        class="bg-gray-900 text-white active:bg-gray-700 text-sm font-bold uppercase px-6 py-3 rounded-full shadow hover:shadow-lg outline-none focus:outline-none mr-1 mb-1 w-full"
                                        type="button"
                                        style="transition: all 0.15s ease 0s;"
                                    >Sign In</button>
                                </div>
                            </form>
                        </div>

                        <div v-if="section === 'signup'" class="flex-auto px-4 lg:px-10 py-10 pt-0">
                            <form>
                                <div class="relative w-full mb-3">
                                    <label
                                        class="block uppercase text-gray-700 text-xs font-light mb-2"
                                        for="grid-password"
                                    >Email</label>
                                    <input
                                        type="email"
                                        class="px-3 py-3 placeholder-gray-400 text-gray-700 bg-white rounded-full text-sm shadow focus:outline-none focus:shadow-outline w-full"
                                        placeholder="Email"
                                        style="transition: all 0.15s ease 0s;"
                                    />
                                </div>
                                <div class="relative w-full mb-3">
                                    <label
                                        class="block uppercase text-gray-700 text-xs font-light mb-2"
                                        for="grid-password"
                                    >Email</label>
                                    <input
                                        type="email"
                                        class="px-3 py-3 placeholder-gray-400 text-gray-700 bg-white rounded-full text-sm shadow focus:outline-none focus:shadow-outline w-full"
                                        placeholder="Email"
                                        style="transition: all 0.15s ease 0s;"
                                    />
                                </div>
                                <div class="relative w-full mb-3">
                                    <label
                                        class="block uppercase text-gray-700 text-xs font-light mb-2"
                                        for="grid-password"
                                    >Password</label>
                                    <input
                                        type="password"
                                        class="px-3 py-3 placeholder-gray-400 text-gray-700 bg-white rounded-full text-sm shadow focus:outline-none focus:shadow-outline w-full"
                                        placeholder="Password"
                                        style="transition: all 0.15s ease 0s;"
                                    />
                                </div>
                                <div>
                                    <label class="inline-flex items-center cursor-pointer">
                                        <input
                                            id="customCheckLogin"
                                            type="checkbox"
                                            class="form-checkbox text-gray-800 ml-1 w-5 h-5"
                                            style="transition: all 0.15s ease 0s;"
                                        />
                                        <span
                                            class="ml-2 text-sm font-semibold text-gray-700"
                                        >Remember me</span>
                                    </label>
                                </div>
                                <div class="text-center mt-6">
                                    <button
                                        class="bg-gray-900 text-white active:bg-gray-700 text-sm font-bold uppercase px-6 py-3 rounded-full shadow hover:shadow-lg outline-none focus:outline-none mr-1 mb-1 w-full"
                                        type="button"
                                        style="transition: all 0.15s ease 0s;"
                                    >Sign In</button>
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
