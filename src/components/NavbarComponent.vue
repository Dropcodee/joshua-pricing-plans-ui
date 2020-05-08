<template>
    <div>
        <nav class="bg-white p-4 mt-0 fixed w-full z-10 top-0 hover:shadow-lg shadow-md">
            <div class="container mx-auto flex flex-wrap items-center">
                <div class="flex w-full sm:w-1/2 justify-center sm:justify-start text-white font-extrabold">
                    <router-link class="text-blue-700 no-underline hover:text-blue-900 hover:no-underline" to="/">
                        AppRuve
                    </router-link>
                </div>
                <div class="flex w-full justify-between sm:w-1/2 sm:justify-end">
                    <ul class="list-reset flex justify-between flex-1 md:flex-none items-center">
                        <li class="mr-2" v-for="(navlink, i) in navLinks" :key="i">
                            <router-link :to="navlink.path" class="text-blue-700 font-semibold rounded hover:bg-gray-200 px-2 py-2 block sm:mt-0 sm:ml-3 sm:px-4">{{ navlink.text }}</router-link>
                        </li>
                    </ul>
                </div>
            </div>
        </nav>
    </div>
</template>
<script>
export default {

    name: 'NavbarComponent',

    data() {
        return {
            navLinks: [
                { path: '/', text: 'Pricings' },
                { path: '/', text: 'Products' },
                { path: '/', text: 'Forum' },
            ],
        };
    },
};
</script>
<style lang="css" scoped>
</style>
