
<template>

    <AuthenticatedLayout>
        <template #header>
            Dashboard
        </template>

        <div class="bg-white overflow-hidden shadow-sm sm:rounded-lg">
            <div class="p-6 border-b border-gray-200">
                
                    <form @submit.prevent="submit">
                            <div class="col-span-6 sm:col-span-4">
                             <InputLabel for="nombre" value="Nombre de la tarea" />
                             <TextInput
                                 id="nombre"
                                 type="text"
                                 class="mt-1 block w-full"
                                 v-model="form.nombre"
                                 autocomplete="nombre"
                             />
                            <!-- <InputError :message="errors.nombre" class="mt-2" /> -->
                            </div>
                            <div class="col-span-6 sm:col-span-4">
                             <InputLabel for="descripcion" value="Descripcion de la tarea" />
                             <TextInput
                                 id="descripcion"
                                 type="text"
                                 class="mt-1 block w-full"
                                 v-model="form.descripcion"
                                 autocomplete="descripcion"
                             />
                            <!-- <InputError :message="errors.descripcion" class="mt-2" /> -->
                            </div>
                            <div class="col-span-6 sm:col-span-4">
                             <InputLabel for="archivo" value="Subir archivo" />
                             <TextInput
                                 id="archivo"
                                 type="text"
                                 class="mt-1 block w-full"
                                 v-model="form.archivo"
                                 autocomplete="archivo"
                             />
                            <!-- <InputError :message="errors.archivo" class="mt-2" /> -->
                            </div>
                            <div class="col-span-6 sm:col-span-4">
                             <InputLabel for="nota_maxima" value="Nota Maxima" />
                             <TextInput
                                 id="nota_maxima"
                                 type="text"
                                 class="mt-1 block w-full"
                                 v-model="form.nota_maxima"
                                 autocomplete="nota_maxima"
                             />
                            <!-- <InputError :message="errors.nota_maxima" class="mt-2" /> -->
                            </div>
                            <div class="col-span-6 sm:col-span-4">
                             <InputLabel for="numero_intentos" value="Numero de Intentos" />
                             <TextInput
                                 id="numero_intentos"
                                 type="text"
                                 class="mt-1 block w-full"
                                 v-model="form.num_intentos"
                                 autocomplete="numero_intentos"
                             />
                            <!-- <InputError :message="errors.num_intentos" class="mt-2" /> -->

                          </div>

                          <div class="col-span-6 sm:col-span-4">
                             <InputLabel for="fecha_vencimiento" value="fecha de vencimiento" />
                             <TextInput
                                 id="fecha_vencimiento"
                                 type="date"
                                 class="mt-1 block w-full"
                                 v-model="form.fecha_vencimiento"
                                 autocomplete="fecha_vencimiento"
                             />
                            <!-- <InputError :message="errors.fecha_vencimiento" class="mt-2" /> -->

                          </div>

                          <div class="flex justify-end">
                            <PrimaryButton type="submit">Crear</PrimaryButton>
                          </div>
                          </form>

            </div>
        </div>
    </AuthenticatedLayout>
</template>
<script>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue'
import { useForm, router} from '@inertiajs/vue3';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import InputLabel from '@/Components/InputLabel.vue';
import TextInput from '@/Components/TextInput.vue';
import InputError from '@/Components/InputError.vue';
  export default {
    components:{
        AuthenticatedLayout,
        PrimaryButton,
        InputLabel,
        TextInput,
        InputError
    },
    props:{
        errors:Object,
    },

    setup() {
        const form = useForm({
            nombre: null,
            descripcion: null,
            archivo: null,
            nota_maxima: null,
            num_intentos: null,
            tipfecha_vencimiento: null

        })

        function submit() {
            router.post(route("tarea.store"), form)
        }
        return { form, submit };
    }
  };

</script>
