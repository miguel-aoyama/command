<template>
    <app-layout title="UserPage">
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Categories
            </h2>
        </template>

        <div>
          <div class="max-w-7x1 mx-auto py-10 sm:px-6 lg:px-8">
            <div>
              <Link :href="route('category.create')">
                <jet-button class="bg-blue-700 text-base">
                  Category create
                </jet-button>
              </Link>
            </div>
            <table>
              <thead>
                <tr>
                  <th>title</th>
                  <th class="w-2/12">削除</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="category in categories" :key="category.id">
                  <td class="border px-4 py-2">{{category.title}}</td>
                  <td class="border px-4 py-2 text-center">
                    <jet-button class="bg-red text-base"
                    @click.native="deleteCategory(category.id)">削除</jet-button>
                  </td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
    </app-layout>
</template>

<script>
    import { defineComponent } from 'vue'
    import AppLayout from '@/Layouts/AppLayout.vue';
    import JetButton from "@/Jetstream/Button";
    import Link from "@/Jetstream/NavLink"

    export default defineComponent({
        props:['locations','categories'],
        components: {
            AppLayout,
            JetButton,
            Link,
        },
        data() {
          return {
            form: this.$inertia.form(
              {
              _method: "DELETE",
              }
            ),
          };
        },
        methods: {
          deleteCategory(id) {
            this.form.post(route("category.destroy", id), {
              preserveScroll: true,
            });
          }
        }
    })
</script>
