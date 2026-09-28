<template>
  <div 
    class="mx-auto d-flex align-center justify-center" 
    style="height: 90vh;">

      <v-card 
        width="500" 
        class="py-8" 
        rounded="xl" 
        elevation="8">
          <v-card-text  
            class="text-center">
              <v-icon 
                size="100" 
                color="primary">
                mdi-account
                  </v-icon>
                    <h3>Welcome back, please login</h3>
                      <v-form class="px-8">

                        <v-text-field 
                        prepend-inner-icon="mdi-account" 
                        variant="solo-filled" 
                        flat label="Username" 
                        rounded>
                        </v-text-field>

                        <v-text-field 
                        prepend-inner-icon="mdi-lock" 
                        variant="solo-filled" 
                        flat label="Password" 
                        type="123" 
                        rounded>
                        </v-text-field>

                        <v-btn 
                        color="primary" 
                        class="mt-3" 
                        rounded block
                        > Login
                        </v-btn>
                          
                          <v-divider class="my-8">OR</v-divider>

                        <v-btn 
                        prepend-icon="mdi-google" 
                        variant="flat" 
                        color="red" 
                        rounded block 
                        @click="loginWithGoogle">sign in with google 
                        </v-btn>
        </v-form>
      </v-card-text>
    </v-card>
  </div>
</template>
<script setup lang="ts">
// @ts-nocheck
definePageMeta({
  layout: false,
  // middleware:'auth'
})

const config = useRuntimeConfig()
declare global {
 interface Window {
 google: any
 }
}
const loginWithGoogle = () => {
 const client = window.google.accounts.oauth2.initTokenClient({
 client_id: config.public.googleClientId,
 scope: 'openid email profile',
 callback: async (response: any) => {
 const userInfo = await $fetch(
 'https://www.googleapis.com/oauth2/v3/userinfo',
 {
 headers: {
 Authorization: `Bearer ${response.access_token}`
 }
 }
 )
 localStorage.setItem(
 'google_user',
 JSON.stringify(userInfo)
 )
 localStorage.setItem(
 'google_token',
 response.access_token
 )
 navigateTo('/')
 }
 })
 client.requestAccessToken()
}
</script>