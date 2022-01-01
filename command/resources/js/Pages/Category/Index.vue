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
                </tr>
              </thead>
              <tbody>
                <tr v-for="category in categories" :key="category.id">
                  <td class="border px-4 py-2">{{category.title}}</td>
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
    })
</script>
