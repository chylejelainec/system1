<template>
  <div class="mx-auto d-flex justify-center align-center" style="height: 90vh;">

    <v-card>
      <v-card-text>
        <!-- show qr -->
        <video class="qr-video"></video>
        <!-- start scn -->
        <v-btn color="primary" block> Start Scanner</v-btn>
        <!-- stop -->
        <v-btn color="error" class="mt-3" block> Stop Scanner</v-btn>

      </v-card-text>
    </v-card>
    
  </div>
</template>

<script lang="ts" setup>

</script>

<style scoped>
.qr-video{
  width: 100%;
  max-width: 400px;
  border-radius: 12px;
  background: #000;
}

</style>
