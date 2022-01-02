<template>
    <app-layout title="UserPage">
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Categories
            </h2>
        </template>
        <div>
          <div class="max-w-7x1 mx-auto py-10 sm:px-6 lg:px-8">
            <jet-form-section @submitted="editCategory">
              <template #title>
                Category更新
              </template>
              <template #description>
                Categoryの更新を行います
              </template>
              <template #form>
                <div class="col-span-6 sm:col-span-4">
                  <jet-label for="title" value="タイトル" />
                  <jet-input
                    id="title"
                    type="text"
                    class="mt-1 block w-full"
                    v-model="form.title"
                  />

                </div>
              </template>
              <template #actions>
                <jet-button class="bg-blue-700">
                  更新
                </jet-button>
              </template>
            </jet-form-section>
          </div>
        </div>
    </app-layout>
</template>

<script>
    import { defineComponent } from 'vue'
    import AppLayout from '@/Layouts/AppLayout.vue'
    import JetFormSection from '@/Jetstream/FormSection'
    import JetInput from '@/Jetstream/Input'
    import JetLabel from '@/Jetstream/Label'
    import JetButton from '@/Jetstream/Button'


    export default defineComponent({
        props:['locations','category'],
        components: {
            AppLayout,
            JetFormSection,
            JetInput,
            JetLabel,
            JetButton,
        },
        data() {
          return {
            form: this.$inertia.form(
              {
                _method: "PUT",
                title: this.category.title,
              },
              {
                bag: "CategoryEdit",
                resetOnSuccess: false,
              }
            )
          }
        },
        methods: {
          editCategory() {
            this.form.post(route("category.update",this.category.id));
          }
        }
    })
</script>
