<script setup>
import { z } from "zod";

definePageMeta({
  layout: false,
});
// state
const formState = reactive({
  username: undefined,
  password: undefined,
});
// schema
const schema = z.object({
  username: z.string().trim().min(1, "Username is required"),
  password: z.string().trim().min(1, "Password is required"),
});

// submit function
const isLoading = ref(false);
const errorMsg = ref(null);
const auth = useAuth();
const router = useRouter();

async function login({ data }) {
  console.log("Submitting:", data);
  try {
    isLoading.value = true;
    await auth.login(data);
    router.push("/");
  } catch (error) {
    if (error.message.includes("Invalid credentials")) {
      errorMsg.value = "Invalid username or password. Please try again.";
    } else {
      errorMsg.value = "An unexpected error occurred. Please try again.";
    }
    console.log('Login error:', error);
  } finally {
    isLoading.value = false;
  }
}
</script>

<template>
  <div class="h-screen flex items-center justify-center p-6">
    <div
      class="bg-white shadow-lg rounded w-[800px] overflow-hidden flex items-center h-[450px]"
    >
      <div class="w-1/2 h-full bg-slate-100"/>

      <div class="p-6 grow">
        <h1 class="text-4xl mb-1 text-green-800 font-black uppercase">Login</h1>
        <p class="text-slate-500 mb-4">Welcome back to good recipes</p>

        <div class="h-[30px] mb-4">
          <p v-if="errorMsg" class="text-center p-2 text-sm bg-red-50 rounded">
            {{ errorMsg }}
          </p>
        </div>

        <UForm :state="formState" :schema="schema" @submit="login">
          <div class="h-[100px]">
            <UFormGroup label="Username" name="username">
              <UInput v-model="formState.username"/>
            </UFormGroup>
          </div>
          <div class="h-[100px]">
            <UFormGroup label="Password" name="password">
              <UInput v-model="formState.password" type="password"/>
            </UFormGroup>
          </div>

          <UButton
            :loading="isLoading"
            type="submit"
            color="orange"
            class="duration-300 hover:bg-orange-600 mb-6 bg-amber-500"
            block
          >
            Login
          </UButton>
        </UForm>
      </div>
    </div>
  </div>
</template>
