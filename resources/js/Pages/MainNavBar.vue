<template>
    <div :class="{'mx-auto max-h-[75px] min-h-[75px] bg-white flex flex-col w-screen border-b-2': !menu, 'mx-auto max-h-[75px] min-h-[75px] bg-menu text-white flex flex-col w-screen border-b-2': menu}">
            <div class="flex w-full pr-[10px]">
                <div class="items-center text-left p-5">
                    <svg role="img" aria-labelledby="logo" :class="{'fill-black': !menu, 'fill-white': menu}" xmlns="http://www.w3.org/2000/svg" width="45" height="21" viewBox="0 0 45 21"><title id="logo">Ableton Homepage</title><path d="M0 0h3v21H0zM6 0h3v21H6zM12 0h3v21h-3zM18 0h3v21h-3zM24 18h21v3H24zM24 12h21v3H24zM24 6h21v3H24zM24 0h21v3H24z"></path></svg>
                </div>

                <!-- Responsive menu selector -->
                    <ul class="flex lg:hidden flex-row w-full gap-10 items-center font-bold">
                        <li class="w-fu">
                            <button class="inline-flex items-center" @click="showMenu">
                                <span>Menu</span>
                                <span :class="{hidden: menu}"><i class="fi-xwsdxl-caret-solid"></i></span>
                                <span :class="{hidden: !menu}"><i class="fi-xwsuxl-sort-up-solid"></i></span>
                            </button>
                        </li>
                    </ul>

                <!-- Standard menu -->
                <ul class="hidden lg:flex w-screen gap-10 items-center font-bold">
                    <li>
                        <span>Live</span>
                    </li>
                    <li>
                        <span>Push</span>
                    </li>
                    <li>
                        <span>Link</span>
                    </li>
                    <li>
                        <span>Shop</span>
                    </li>
                    <li>
                        <span>Packs</span>
                    </li>
                    <li>
                        <span>Help</span>
                    </li>
                    <li class="w-full">
                        <button class="inline-flex items-center w-full font-bold" @click="moreOrLess">
                            <span>More</span>
                            <span :class="{hidden: more}"><i class="fi-xwsuxl-plus-solid"></i></span>
                            <span :class="{hidden: !more}" v-on=""><i class="fi-xwsuxl-minus-solid"></i></span>
                        </button>
                    </li>

                    <div class="flex flex-row justify-end px-5 w-full bg-white max-h-[75px]">
                        <div class="flex flex-shrink flex-row justify-start gap-10">
                            <div>
                                <span>
                                    <Link href="#" class="font-bold">Try Live for Free</Link>
                                </span>
                            </div>

                            <div>
                                <span v-if="user" class="">
                                    <form method="POST" @submit.prevent="logout">
                                        <jet-responsive-nav-link as="button">
                                            Log Out
                                        </jet-responsive-nav-link>
                                    </form>
                                </span>
                                <span v-else>
                                    <Link href="/dashboard" class="text-[0.8em] font-bold">Log in or register</Link>
                                </span>
                            </div>
                        </div>
                    </div>
                </ul>
            </div>

            <div v-if="menu">
                <div class="flex flex-col pb-5 bg-menu absolute lg:hidden font-bold">
                    <div class="w-screen">
                        <ul class="pl-5">
                            <li class="pt-[2em]">
                                Live
                            </li>
                            <li class="pt-[2em]">
                                Push
                            </li>
                            <li class="pt-[2em]">
                                Link
                            </li>
                            <li class="pt-[2em]">
                                Shop
                            </li>
                            <li class="pt-[2em]">
                                Packs
                            </li>
                            <li class="pt-[2em]">
                                Help
                            </li>
                            <li class="pt-[2em]">
                                Try Live for free
                            </li>
                            <li class="pt-[1.5rem]">
                            <span v-if="user" class="">
                                <form method="POST" @submit.prevent="logout">
                                    <jet-responsive-nav-link as="button">
                                        Log Out
                                    </jet-responsive-nav-link>
                                </form>
                            </span>
                                <span v-else>
                                <Link href="/dashboard" class="text-[0.8em] font-bold">Log in or register</Link>
                            </span>
                            </li>
                            <li class="pt-[1.5em]">
                            <span>
                                More on Ableton.com:
                            </span>
                                <ul class="text-[0.8em] pt-[1em]">
                                    <li>
                                        Blog
                                    </li>
                                    <li class="pt-[1em]">
                                        Ableton for the Classroom
                                    </li>
                                </ul>
                            </li>
                            <li class="pt-[2em]">
                                <div class="flex-grow">
                                    More from Ableton:
                                </div>
                            </li>
                        </ul>

                    </div>
                    <div class="w-screen pt-5">

                        <div class="flex overflow-x-scroll max-h-[125px] justify-left ml-5 mr-5" >
                            <div id="scrollingTextWrapper"></div>
                            <div class="flex flex-row gap-10">
                                <div class="w-[500px]">
                                    <div>
                                        Loop
                                    </div>
                                    <div class="text-[0.8em]">
                                        Watch Talks, Performances and Features from Ableton's Summit for Music Makers
                                    </div>
                                </div>
                                <div class="max-w-[500px]">
                                    <div>
                                        Learning Music
                                    </div>
                                    <div class="text-[0.8em]">
                                        Learn the fundamentals of music making right in your browser.
                                    </div>
                                </div>
                                <div class="max-w-[500px]">
                                    <div>
                                        Learning Synths
                                    </div>
                                    <div class="text-[0.8em]">
                                        Get started with synthesis using a web-based synth and accompanying lessons.
                                    </div>
                                </div>
                                <div class="max-w-[500px]">
                                    <div>
                                        Making Music
                                    </div>
                                    <div class="text-[0.8em]">
                                        Some tips from 74 Creative Strategies for Electronic Producers.
                                    </div>
                                </div>
                            </div>

                        </div>

                    </div>
                </div>
            </div>

            <div v-if="!menu">
                <SecondNavBar />
            </div>

    </div>

</template>

<script>
import { computed } from 'vue';
import { usePage, Link } from '@inertiajs/inertia-vue3';
import SecondNavBar from "@/Pages/SecondNavBar";
export default {
    name: "MainNavBar",

    setup() {
        const user = computed(() => usePage().props.value.auth.user);
        return { user };
    },
    data() {
        return {
            more: false,
            menu: false,
        }
    },
    components: {
        Link,
        SecondNavBar
    },
    logout() {
        this.$inertia.post(route('logout'));
    },
    methods: {
        moreOrLess() {
            this.more = !this.more;
        },
        showMenu() {
            this.menu = !this.menu;
        }
    }
}
</script>

<style scoped>

    #scrollingTextWrapper {
        background-image: linear-gradient(90deg, rgba(0,0,255,0),blue);
        display:block;
        right: 1.2rem;
        bottom:1.25rem;
        width: 2.5rem;
        position: absolute;
        height:5rem;

    }
</style>
