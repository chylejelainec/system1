<template>
  <div 
    class="mx-auto d-flex align-center justify-center" 
    style="height: 90vh;"
  >
  <v-app>
    <v-navigation-drawer
        expand-on-hover
        permanent
        rail
      >
        <v-list>
          <v-list-item
            prepend-avatar="https://randomuser.me/api/portraits/women/85.jpg"
            subtitle="cenzon@gmailcom"
            title="Chyle Cenzon"
          ></v-list-item>
        </v-list>

        <v-divider></v-divider>

        <v-list density="compact" nav>
          <v-list-item prepend-icon="mdi-view-dashboard" title="Dashboard" value="/ "></v-list-item>
          <v-list-item prepend-icon="mdi-qrcode-scan" title="Qr-Scanner" to="/qr-scanner"></v-list-item>
          <v-list-item prepend-icon="mdi-weather-cloudy" title="Weather" to="/weather"></v-list-item>
        </v-list>
      </v-navigation-drawer>

      <v-app-bar color="primary">
        <v-app-bar-nav-icon variant="text" @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
        <v-app-bar-title>System Integration</v-app-bar-title>
      </v-app-bar>

      <v-main>
        <v-container fluid>
    <slot />
    </v-container>
    </v-main>
    </v-app>
    </div>
</template>

<script lang="ts" setup>
  const drawer = ref(true)
 
</script>

<style>

</style>