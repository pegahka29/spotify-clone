<template>
    <div id="app" class="bg-dark h-screen">
        <div class="flex" style="height: 88vh">
            <!--side-nav-->
            <div class="w-56 bg-black h-full flex-none">
                <div class="p-6">
                    <img alt="logo" src="@/assets/Spotify-Logo.wine.svg" class="z-40 h-20">
                </div>
                <div v-for="page in pages" :key="page.id" class="mx-2">
                    <button @click="setID = page.id"
                            :class="`w-full text-xs font-semibold rounded px-3 py-2 flex justify-start items-center ${setID === page.id ? 'bg-lightest text-white': 'text-lightest'}`">
                        <font-awesome-icon size="lg" :icon="['fas', page.icon ]"/>
                        <p class="ml-2">{{ page.name }}</p>
                    </button>
                </div>
                <div class="flex justify-start items-start flex-col mx-5 mt-3">
                    <h1 class="text-xs text-lightest tracking-widest uppercase mb-3">Playlists</h1>
                    <div class="flex opacity-75 hover:opacity-100 cursor-pointer">
                        <button class="flex items-center justify-start bg-white rounded p-1">
                            <font-awesome-icon :icon="['fas', 'plus']"/>
                        </button>
                        <p class="text-sm font-semibold text-white ml-2">Create Playlist</p>
                    </div>
                    <div class="flex opacity-75 hover:opacity-100 mt-3 cursor-pointer">
                        <button class="flex items-center justify-start bg-white rounded p-1">
                            <font-awesome-icon :icon="['fas', 'heart']"/>
                        </button>
                        <p class="text-sm font-semibold text-white ml-2">Liked Songs</p>
                    </div>
                </div>
            </div>
            <!--main-content-->
            <div class="w-full h-full relative">
            </div>
            <!--header-->
            <div class="w-full sticky top-0 p-2"></div>
        </div>
        <!--play-bar-->
        <div class="w-full bg-light" style="height: 12vh"></div>
    </div>
</template>

<script>

export default {
    name: 'App',
    components: {},
    data() {
        return {
            pages: [
                {
                    id: 'home',
                    name: 'Home',
                    icon: 'home'
                },
                {
                    id: 'search',
                    name: 'Search',
                    icon: 'search'
                },
                {
                    id: 'library',
                    name: 'Your Library',
                    icon: 'book'
                }
            ],
            setID: 'home'
        }
    },
}
</script>

<style>
</style>
