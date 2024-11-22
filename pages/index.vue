<script setup lang="ts">
import { useAuthStore, useIsLoadingStore } from '~/store/auth.store';
import { account } from '@/lib/appwrite'

const isLoadingStore = useIsLoadingStore()
const authStore = useAuthStore()
const router = useRouter()

const logout = async () => {
	// Turn On Loader
	isLoadingStore.set(true)
	// Deletting Session
	await account.deleteSession('current')
	// Clear Store
	authStore.clear()
	// Redirrect to Auth Page
	await router.push('/login')
	// Turn Of Loader
	isLoadingStore.set(false)
}
</script>
<template>
	<div class="w-full h-full">
		<button class=" w-[50px] h-[50px] bg-black" @click="logout">
		</button>
	</div>
</template>

<style scoped></style>