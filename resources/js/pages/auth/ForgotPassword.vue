<template>
<div class="min-h-screen flex flex-col sm:justify-center items-center pt-6 sm:pt-0">
    <router-link :to="{name: 'Login'}" class="flex items-center space-x-1 pt-8 sm:justify-start sm:pt-0 text-xl text-gray-800 font-bold">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 12h14M5 12a2 2 0 01-2-2V6a2 2 0 012-2h14a2 2 0 012 2v4a2 2 0 01-2 2M5 12a2 2 0 00-2 2v4a2 2 0 002 2h14a2 2 0 002-2v-4a2 2 0 00-2-2m-2-4h.01M17 16h.01" />
        </svg>
        <span>Laravel Sanctum Vue SPA</span>
    </router-link>

    <div class="w-full sm:max-w-md mt-6 px-6 py-4 bg-gray-100 shadow-md overflow-hidden sm:rounded-lg">
        <form @submit.prevent="resetPassword">
            <div>
                <label class="block font-medium text-sm text-gray-500" for="email">
                    Email
                </label>
                <input v-model="email" class="p-2 rounded-md shadow-sm bg-white border-gray-900 text-gray-400 block mt-1 w-full" id="email" type="email" name="email" required="required" autofocus="autofocus">
            </div>
            <div class="flex items-center justify-end mt-4">
                <button type="submit" class="inline-flex items-center px-4 py-2 bg-gray-900 border border-transparent rounded-md font-semibold text-xs text-white uppercase tracking-widest hover:bg-gray-700 active:bg-gray-900 focus:outline-none focus:border-gray-900 focus:ring ring-gray-300 disabled:opacity-25 transition ease-in-out duration-150 ml-3">
                    Send Password-Reset E-Mail
                </button>
            </div>
        </form>
    </div>
</div>
</template>

<script>
export default {
    data: () => {
        return {
            email: null,
        }
    },
    methods: {
        resetPassword() {
            axios.post('/forgot-password', {email: this.email})
                .then((response) => {
                    console.log(response)
                    //router.push({name: 'Home'})
                })
                .catch((error) => {
                    console.error(error)
                })
        }
    }
}
</script>
