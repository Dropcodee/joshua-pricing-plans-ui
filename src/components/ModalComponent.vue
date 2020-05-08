<template>
    <transition name="modal-fade">
        <div class="modal-backdrop">
            <div class="modal bg-white mt-12" role="dialog" aria-labelledby="modalTitle" aria-describedby="modalDescription">
                <header class="flex items-center justify-between w-full" id="modalTitle">
                    <span class="text-gray-700 mt-4 font-semibold pl-12"> Subscribe For {{ plan.name }}</span>
                    <button class="justify-end py-2 px-4 bg-blue-600  mr-4 mt-4 rounded-md float-right font-bold text-white float-right" @click="close">X</button>
                </header>
                <section class="modal-body" id="modalDescription">
                    <form class="bg-white lg:px-8 lg:pt-6 pb-8 mt-4">
                        <div class=" relative">
                            <input class="shadow appearance-none border rounded-lg w-full py-4 px-16 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" type="text" placeholder="Full Name" v-model="form.fullname">
                        </div>
                        <div class="relative mt-6">
                            <input class="shadow appearance-none border rounded-lg w-full py-4 px-16 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" type="email" placeholder="Your Mail" v-model="form.email">
                            <!-- <p class="text-red-500 text-xs italic">Please choose a password.</p> -->
                        </div>
                        <div class="flex items-center justify-between mt-6">
                            <button class="w-full bg-blue-700 rounded-full hover:bg-blue-900 text-white font-bold py-4 px-4 rounded focus:outline-none focus:shadow-outline" type="button" @click="subscribe(plan)">
                                Subscribe Now
                            </button>
                        </div>
                    </form>
                </section>
                <footer class="modal-footer">
                    <slot name="footer">
                        <button type="button" class="px-8 py-2 bg-blue-700" @click="close" aria-label="Close modal">
                            Cancel Subscription
                        </button>
                    </slot>
                </footer>
            </div>
        </div>
    </transition>
</template>
<script>
export default {
    name: 'modal',
    props: {
        plan: {
            required: true,
            type: Object
        }
    },
    data() {
        return {
            form: {
                fullname: '',
                email: ''
            }
        }
    },
    methods: {
        close() {
            this.$emit('close');
        },
        subscribe(plan) {
            const { fullname } = this.form
            const message = `${fullname} thanks for subscribing for our ${plan.name} plan, we will get back to you shortly.`
            this.$swal({
                toast: true,
                icon: "success",
                width: 350,
                padding: '1.5em',
                background: "#fff",
                position: "top-end",
                text: message,
                showConfirmButton: false,
                timer: 6000,
                timerProgressBar: true,
                onOpen: toast => {
                    toast.addEventListener("mouseenter", this.$swal.stopTimer);
                    toast.addEventListener("mouseleave", this.$swal.resumeTimer);
                }
            });
            this.form.fullname = '',
            this.form.email = ''
        }
    },
};
</script>
<style>
.modal-backdrop {
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    background-color: rgba(0, 0, 0, 0.3);
    display: flex;
    justify-content: center;
    align-items: center;
}


.modal-body {
    position: relative;
    padding: 20px 10px;
}

.btn-close {
    border: none;
    font-size: 20px;
    padding: 20px;
    cursor: pointer;
    font-weight: bold;
    color: #4AAE9B;
    background: transparent;
}

.btn-green {
    color: white;
    background: #4AAE9B;
    border: 1px solid #4AAE9B;
    border-radius: 2px;
}
</style>
