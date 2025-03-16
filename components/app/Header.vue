<script setup>
const auth = useAuth();
</script>

<template>
  <div class="p-6 flex gap-4 shadow-lg">
    <div class="container m-auto flex justify-between items-center gap-6">
      <div class="flex gap-8 items-center">
        <NuxtLink
          to="/"
          class="uppercase font-black text-2xl text-green-700 flex gap-1 items-center"
        >
          <UIcon name="i-mdi-cook" />
          <span>good</span>
          <span class="text-orange-500">recipes</span>
        </NuxtLink>
        <AppAuthChecker>
          <template #unAuth>
            <NuxtLink to="/about">About</NuxtLink>
          </template>
        </AppAuthChecker>
      </div>

      <AppAuthChecker>
        <template #unAuth>
          <NuxtLink to="/login">
            <UButton class="bg-green-600 duration-300 hover:bg-green-700"
              >Login</UButton
            >
          </NuxtLink>
        </template>

        <template #auth>
          <UButton
            variant="soft"
            icon="i-heroicons-arrow-left-on-rectangle-16-solid"
            @click="auth.logout()"
            >Log Out</UButton
          >
        </template>
      </AppAuthChecker>
    </div>
  </div>
</template>
