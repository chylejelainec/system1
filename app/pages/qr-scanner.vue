<template>
  <div class="mx-auto d-flex justify-center align-center" style="height: 90vh;">

    <v-card>
      <v-card-text>
        <!-- show qr -->
        <video ref="videoRef" class="qr-video"></video>
        <!-- start scn -->
        <v-btn color="primary" @click="startScanner"  block> Start Scanner</v-btn>
        <!-- stop -->
        <v-btn color="error" class="mt-3" block> Stop Scanner</v-btn>

      </v-card-text>
    </v-card>
    
  </div>
</template>

<script lang="ts" setup>
import QrScanner from 'qr-scanner'

const videoRef = ref<HTMLVideoElement | null>(null)
  let scanner: QrScanner | null = null

const startScanner = async () => {
  if (!videoRef.value) return

  scanner = new QrScanner(
    videoRef.value,
    (scanResult) => {
      scanner?.stop()
    },
    {
      preferredCamera: 'environment',
      highlightCodeOutline: true,
      highlightScanRegion: true,
    }
  )

  await scanner.start()
}
  

</script>

<style scoped>
.qr-video{
  width: 100%;
  max-width: 400px;
  border-radius: 12px;
  background: #000;
}


</style>
