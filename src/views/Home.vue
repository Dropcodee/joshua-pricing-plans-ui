<template>
    <div class="home">
        <navbar-component />
        <div class="bg-blue-900 w-full mt-16 landing">
            <div class="absolute inset-x-0 top-auto text-center mt-32">
                <h3 class="text-white text-5xl">New Plans For All</h3>
                <p class="text-gray-500 max-w-lg text-center mx-auto"> Affordable plans for all our premium products, we offer affpordable plans for individuals and teams.</p>
            </div>
        </div>
        <div class=" container">
            <div class="flex justify-between items-center overflow-x-auto pb-8  -mt-24 ">
                <div class="bg-white rounded-lg shadow-md  max-w-md px-8 ml-4 block" v-for="(plan, index) in plans" :key="index">
                    <div class="w-56 bg-blue-600 rounded-lg text-center mx-auto mt-8 py-4">
                        <svg class="mx-auto" width="24" height="24" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <path fill-rule="evenodd" clip-rule="evenodd" d="M13.92 9.5h-2v-3h-3v-2h3v-3h2v3h3v2h-3v3zm-7.99 11c0-1.1.89-2 1.99-2s2 .9 2 2-.9 2-2 2-1.99-.9-1.99-2zm11.99-2c-1.1 0-1.99.9-1.99 2s.89 2 1.99 2 2-.9 2-2-.9-2-2-2zm-1.45-5H9.02l-1.1 2h12v2h-12c-1.52 0-2.48-1.63-1.75-2.97l1.35-2.44-3.6-7.59h-2v-2h3.27l4.26 9h7.02l3.87-7 1.74.96-3.86 7.01c-.34.62-1 1.03-1.75 1.03z" fill="#fff" fill-opacity=".84" /></svg>
                        <span class="text-gray-300 font-bold text-2xl">{{ plan.name }}</span>
                    </div>
                    <div class="flex items-center justify-center mt-4 ">
                        <span class="text-blue-700 text-4xl font-bold">&#36;{{ plan.discount }}</span>
                        <s class="text-gray-500 text-lg pl-2 ">${{ plan.oldprice }}</s>
                    </div>
                    <div class="mt-6 mx-auto text-center">
                        <p class="flex justify-center mt-4 items-center px-1 text-center" v-for="(property, index) in plan.properties" :key="index">
                            <svg width="24" height="24" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path d="M8.8 15.9l-4.2-4.2-1.4 1.4 5.6 5.6 12-12-1.4-1.4L8.8 15.9z" fill="#000" fill-opacity=".54" /></svg>
                            <span class="text-gray-600 pl-2">{{ property }}</span>
                        </p>
                    </div>
                    <div class="border py-0 border-gray-400 max-w-xs mx-auto mt-6"></div>
                    <p class="text-gray-700 text-md mt-6 px-4 text-center">{{ plan.desc }}</p>
                    <div class="mx-auto flex items-center justify-center">
                        <button class="px-24 bg-blue-700 text-gray-300 rounded-full py-2 mt-6 mb-8" @click="showModal(plan)"> Subscribe </button>
                    </div>
                </div>
                <modal v-show="isModalVisible" @close="closeModal" :plan="selectedPlan" />
            </div>
        </div>
    </div>
</template>
<script>
import ModalComponent from '@/components/ModalComponent';
import NavbarComponent from '@/components/NavbarComponent'
export default {
    name: 'Home',
    components: {
        'navbar-component': NavbarComponent,
        'modal': ModalComponent
    },
    data() {
        return {
            isModalVisible: false,
            selectedPlan: {},
            plans: [{
                name: 'Monthly',
                discount: '12.99',
                oldprice: '45.99',
                properties: ['Create up to 20 users', 'Create up to 20 API keys'],
                desc: "Level up your career with a monthly plan that can be cancelled at any time"
            },
            {
                name: 'Yearly',
                discount: '75.99',
                oldprice: '129.99',
                properties: ['Create up to 70 users', 'Create up to 50 API keys', '10 chatrooms', 'Staff Mgt System'],
                desc: "commit to your business growth up your career with a yearly plan that can be cancelled at any time"
            },
            {
                name: 'Lifetime',
                discount: '280.99',
                oldprice: '390.99',
                properties: ['Create unlimited users', 'Create up to 120 API keys','Unlimited chatrooms', 'Staff Mgt System', 'Business charts & Accounts.'],
                desc: "Level up your career with a monthly plan that can be cancelled at any time"
            }
            ]
        }
    },
    methods: {
        showModal(plan) {
            this.selectedPlan = plan
            this.isModalVisible = true;
        },
        closeModal() {
            this.isModalVisible = false;
        }
    },
}
</script>
<style>
.landing {
    height: 400px
}
</style>