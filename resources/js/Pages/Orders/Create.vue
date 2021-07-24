<template>
    <app-layout>
        <template #header>
            <h1 class="text-center text-2xl font-bold leading-7 text-gray-300 sm:text-3xl sm:truncate py-4 bg-gradient-to-l from-indigo-500 to-indigo-800 ">Crear Orden</h1>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white overflow-hidden shadow-xl sm:rounded-lg">





                    <!-- Ojo personalizar -->
                    <!-- component -->
                    <div class="container">
                        <div class="mt-5">
                            <div class="w-1/2 mx-auto bg-white rounded-md">
                            <!-- first -->
                            <div class="flex flex-col justify-center items-center">


                                <div
                                class="
                                    flex flex-col
                                    justify-between
                                    items-center
                                    px-3
                                    py-5
                                    w-full
                                "
                                >
                                <div class="mb-5 flex flex-col min-w-full">
                                    <label for="code" class="font-medium text-black"
                                    >Tipo</label
                                    >
                                    <input
                                        v-model="form.tipo"
                                        type="text"
                                        id="code"
                                        class="w-full py-2 border mt-3 border-gray-300 rounded-md"
                                    />
                                </div>
                                <div class="mb-5 flex flex-col min-w-full">
                                    <label for="code" class="font-medium text-black"
                                    >Cantidad</label
                                    >
                                    <input
                                        v-model="form.cantidad"
                                        type="number"
                                        id="code"
                                        class="w-full py-2 border mt-3 border-gray-300 rounded-md"
                                    />
                                </div>

                                <div class="mb-5 flex flex-col min-w-full">
                                    <label for="code" class="font-medium text-black"
                                    >Estado</label
                                    >
                                    <select 
                                        v-model="form.estado"
                                        class="w-full py-2 border mt-3 border-gray-300 rounded-md"
                                    >
                                        <option v-for="state in states" :key="state" :value="state">{{state}}</option>
                                    </select>
                                </div>
                                <button
                                    class="w-full bg-indigo-600 text-white px-2 py-2 rounded-md"
                                    @click="guardar"
                                >
                                    Guardar
                                </button>
                                </div>

                            </div>
                            <!-- end -->
                            </div>
                        </div>
                        </div>
                    <!-- Ojo personalizar -->

                </div>    
            </div>
       </div>    


    </app-layout>
</template>

<script>
    import AppLayout from '@/Layouts/AppLayout'
    import { useForm } from "@inertiajs/inertia-vue3";
    import { ref } from "vue";

    export default {
        name: "orders_create",
        components: {
            AppLayout,
        },
        props: {
        },
        setup(props){
            const form = useForm({
                tipo: '',
                cantidad: 0,
                estado: 'Activo'
            });

            const states = ref(['Activo','Inactivo','Proceso','Despachado']);

            function guardar(){
                form.post(route('orders.store'), {
                    preserveScroll: true,
                    preserveState: true,
                    onSuccess: () => {
                        // alert('guardado con exito');
                    },
                    onError: (e) => {
                        alert('Error' + escape);
                    },
                })
            }

            return {
                states,
                form,
                guardar
            }
        }
    }
</script>
