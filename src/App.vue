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
                            :class="`w-full focus:outline-none text-xs font-semibold rounded px-3 py-2 flex justify-start items-center ${setID === page.id ? 'bg-lightest text-white': 'text-lightest'}`">
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
                    <div class="flex opacity-75 hover:opacity-100 mt-3 cursor-pointer border-b border-light w-full">
                        <button class="flex items-center justify-start bg-white rounded p-1 mb-1">
                            <font-awesome-icon :icon="['fas', 'heart']"/>
                        </button>
                        <p class="text-sm font-semibold text-white ml-2">Liked Songs</p>
                    </div>
                </div>
                <div class="mx-5">
                    <div class="w-full h-24 overflow-y-scroll">
                        <p v-for="album in albums" :key="album.id" class="text-lightest hover:text-white text-sm py-1">
                            {{ album.name }}
                        </p>
                    </div>
                    <button class="flex items-center justify-start text-lightest hover:text-white py-2">
                        <font-awesome-icon class="mr-2" size="sm" :icon="['fas', 'circle-down']"/>
                        <p class="text-sm font-semibold">Install App</p>
                    </button>
                </div>
                <div class="relative pt-4">
                    <div class="w-full h-full flex justify-end absolute p-2 opacity-0 hover:opacity-100 items-start">
                        <div class="bg-black rounded-full h-8 w-8 flex justify-center items-center">
                            <font-awesome-icon class="text-white" :icon="['fas', 'chevron-down']"/>
                        </div>
                    </div>
                    <img src="@/assets/download.jpg">
                </div>
            </div>
            <!--main-content-->
            <div class="w-full h-full relative overflow-y-scroll">
                <!--header-->
                <div class="w-full sticky top-0 py-4 px-6 flex items-center justify-between">
                    <div class="flex items-center">
                        <button class="rounded-full bg-black w-8 h-8 text-white mr-3">
                            <font-awesome-icon class="text-3xl" :icon="['fas', 'chevron-left']"/>
                        </button>
                        <button class="rounded-full bg-black w-8 h-8 text-white">
                            <font-awesome-icon class="text-3xl" :icon="['fas', 'chevron-right']"/>
                        </button>
                    </div>
                    <div class="relative">
                        <button @click="showDropdown = !showDropdown"
                                class="bg-light rounded-full py-1 px-2 flex items-center">
                            <img src="@/assets/my-face.jpg" class="rounded-full h-6 w-6 mr-2"/>
                            <p class="text-white font-semibold text-xs">Pegah K</p>
                            <font-awesome-icon class="ml-2 text-white" size="sm"
                                               :icon="['fas', !showDropdown ? 'caret-down' : 'caret-up']"/>
                        </button>
                        <div v-if="showDropdown" class="absolute bg-light mt-1 w-full rounded">
                            <button @click="showDropdown = false"
                                    class="w-full py-2 text-lightest hover:text-white border-b border-white opacity-75 hover:opacity-100 text-sm focus:outline-none">
                                Account
                            </button>
                            <button @click="showDropdown = false"
                                    class="w-full py-2 text-lightest hover:text-white border-b border-light text-sm opacity-75 hover:opacity-100 focus:outline-none">
                                Logout
                            </button>
                        </div>
                    </div>
                </div>
                <!--cards-->
                <div class="px-6 py-3">
                    <div class="flex items-center justify-between">
                        <h1 class="text-2xl text-white font-semibold tracking-wider hover:underline cursor-pointer pl-2">
                            Recently played</h1>
                        <h2 class="text-xs text-lightest tracking-wider hover:underline uppercase cursor-pointer pl-8 pt-4 mb-3">
                            See All</h2>
                    </div>
                    <div class="w-full flex flex-wrap">
                        <div v-for="recent in recents" :key="recent.title" class="p-2 w-48">
                            <div class="bg-light w-full h-auto p-5 rounded-lg shadow-md cursor-pointer">
                                <img src="@/assets/Spotify-Logo.wine.svg" class="h-auto w-full shadow mb-2">
                                <h1 class="text-sm text-white font-semibold tracking-wide">{{ recent.title }}</h1>
                                <h2 class="text-xs text-lightest tracking-wide pb-5">{{ recent.artist }}</h2>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="px-6 py-3">
                    <div class="pl-2">
                        <h1 class="text-2xl text-white font-semibold tracking-wider hover:underline cursor-pointer">Made
                            for Pegah</h1>
                        <h2 class="text-sm text-lightest">Get Better recommendation</h2>
                    </div>
                    <div class="w-full flex flex-wrap">
                        <div v-for="custom in custom" :key="custom.title" class="p-2 w-48">
                            <div class="bg-light w-full h-auto p-5 rounded-lg shadow-md cursor-pointer">
                                <img src="@/assets/Spotify-Logo.wine.svg" class="h-auto w-full shadow mb-2">
                                <h1 class="text-sm text-white font-semibold tracking-wide">{{ custom.title }}</h1>
                                <h2 class="text-xs text-lightest tracking-wide pb-5">{{ custom.artist }}</h2>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
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
            setID: 'home',
            albums: [
                {
                    id: 'drive',
                    name: 'drive'
                },
                {
                    id: 'zhu',
                    name: 'zhu'
                },
                {
                    id: 'All New Indie',
                    name: 'All New Indie'
                },
                {
                    id: 'Mellow',
                    name: 'Mellow'
                },
                {
                    id: 'Classic Old Trip Songs',
                    name: 'Classic Old Trip Songs'
                },
                {
                    id: 'Lana Del Rey Radio',
                    name: 'Lana Del Rey Radio'
                }
            ],
            showDropdown: false,
            recents: [
                {title: 'Daily Nix 2', artist: 'By Spotify'},
                {title: 'Daily Mix 3', artist: "By Spotify"},
                {title: "BilLie Eflish Radio", artist: 'BiLlie Eflish'},
                {title: 'Cold Case Files', artist: 'Podcastone'},
                {title: 'Life Is Good Radio', artist: 'By Spotify'},
                {title: "run", artist: 'Stephanie Dietz'}
            ],
            custom: [
                {
                    title: 'Dafly Mlx4',
                    artists: "By Spotify"
                },
                {
                    title: 'Dafly Mlx3',
                    artists: "By Spotify"
                },
            ]
        }
    }
}

</script>

<style>
</style>
