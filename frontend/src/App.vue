<template>
  
  <SiteLayout v-if="route.meta.isUserRoute == true">
    <router-view />
  </SiteLayout>

  <AdminLayout v-else-if="route.meta.isAdminRoute == true">
    <router-view />
  </AdminLayout>

  <div v-else>
    <router-view />
  </div>

</template>

<script setup>
import AdminLayout from '@/layouts/Admin.vue'
import SiteLayout from '@/layouts/Site.vue'
import { useRoute } from "vue-router"

const route = useRoute()

</script>