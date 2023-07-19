<template>
    <div id="app" class="bg-dark h-screen">
        <div class="flex" style="height: 88vh">
            <!--side-nav-->
            <div class="w-56 bg-black h-full flex-none">
                <div class="p-6">
                    <img alt="logo" src="@/assets/Spotify-Logo.wine.svg" class="z-40 h-10">
                </div>
                <div class="mx-2">
                    <button class="w-full rounded px-3 py-2 flex justify-start items-center"></button>
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
                    id: '',
                    name: ''
                }
            ]
        }
    },
}
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
</style>
