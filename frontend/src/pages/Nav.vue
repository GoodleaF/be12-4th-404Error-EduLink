<script setup>
import { useRouter } from 'vue-router';
import axios from 'axios';
import { useMemberStore } from '@/stores/useMemberStore';

const router = useRouter();
const memberStore = useMemberStore();

const logout = async () => {
  try {
    await axios.post('/logout', {}, { withCredentials: true });
    memberStore.token = null;
    memberStore.role = null;
    memberStore.email = null;
    memberStore.name = null;
    router.push("/");
  } catch (error) {
    console.error("Logout error:", error);
  }
};
</script>

<template>
    <nav
        class="top-0 inset-x-0 fixed bg-gray-50 h-14 z-30 transition-position w-screen lg:w-auto dark:bg-slate-800 xl:pl-60">
        <div class="flex lg:items-stretch xl:max-w-6xl xl:mx-auto">
            <div class="flex flex-1 items-stretch h-14">
                <div   id="menu-toggle"
                    class="flex lg:hidden py-2 px-3 navbar-item-label items-center cursor-pointer dark:text-white dark:hover:text-slate-400">
                    <span class="inline-flex justify-center items-center w-6 h-6">
                        <svg viewBox="0 0 24 24" width="24"
                            height="24" class="inline-block">
                            <path fill="currentColor"
                                d="M19,13H3V11H19L15,7L16.4,5.6L22.8,12L16.4,18.4L15,17L19,13M3,6H13V8H3V6M13,16V18H3V16H13Z">
                            </path>
                        </svg>
                    </span>
                </div>
                <div
                    class="hidden lg:flex xl:hidden py-2 px-3 navbar-item-label items-center cursor-pointer dark:text-white dark:hover:text-slate-400">
                    <span class="inline-flex justify-center items-center w-6 h-6">
                        <svg viewBox="0 0 24 24" width="24"
                            height="24" class="inline-block">
                            <path fill="currentColor" d="M3,6H21V8H3V6M3,11H21V13H3V11M3,16H21V18H3V16Z"></path>
                        </svg>
                    </span>
                </div>
            </div>
            <div class="flex-none items-stretch flex h-14 lg:hidden">
                <div
                    class="flex py-2 px-3 navbar-item-label items-center cursor-pointer dark:text-white dark:hover:text-slate-400">
                    <span class="inline-flex justify-center items-center w-6 h-6">
                        <svg viewBox="0 0 24 24" width="24"
                            height="24" class="inline-block">
                            <path fill="currentColor"
                                d="M12,16A2,2 0 0,1 14,18A2,2 0 0,1 12,20A2,2 0 0,1 10,18A2,2 0 0,1 12,16M12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12A2,2 0 0,1 12,10M12,4A2,2 0 0,1 14,6A2,2 0 0,1 12,8A2,2 0 0,1 10,6A2,2 0 0,1 12,4Z">
                            </path>
                        </svg>
                    </span>
                </div>
            </div>
            <div
                class="max-h-screen-menu overflow-y-auto lg:overflow-visible absolute w-screen top-14 left-0 bg-gray-50 shadow-lg lg:w-auto lg:flex lg:static lg:shadow-none dark:bg-slate-800 hidden">
                <div
                    class="block lg:flex items-center relative cursor-pointer navbar-item-label dark:text-white dark:hover:text-slate-400 lg:py-2 lg:px-3">
                    <a href="/userinfo"
                        class="flex items-center bg-gray-100 dark:bg-slate-800 lg:bg-transparent lg:dark:bg-transparent p-3 lg:p-0">
                        <div class="w-6 h-6 mr-3 inline-flex"><img
                                src="https://api.dicebear.com/7.x/avataaars/svg?seed=doe-doe-doe-example-com"
                                alt="John Doe"
                                class="rounded-full block h-auto w-full max-w-full bg-gray-100 dark:bg-slate-800"></div>
                        <!--v-if--><span class="px-2 transition-colors">{{ memberStore.name }}</span>
                    </a>
                    <div
                        class="text-sm border-b border-gray-100 lg:border lg:bg-white lg:absolute lg:top-full lg:left-0 lg:min-w-full lg:z-20 lg:rounded-lg lg:shadow-lg lg:dark:bg-slate-800 dark:border-slate-700 lg:hidden">
                        <a
                            class="block lg:flex items-center relative cursor-pointer navbar-item-label dark:text-white dark:hover:text-slate-400 py-2 px-3">
                            <div class="flex items-center"><!--v-if--><span
                                    class="inline-flex justify-center items-center w-6 h-6 transition-colors"><svg
                                        viewBox="0 0 24 24" width="16" height="16" class="inline-block">
                                        <path fill="currentColor"
                                            d="M12,4A4,4 0 0,1 16,8A4,4 0 0,1 12,12A4,4 0 0,1 8,8A4,4 0 0,1 12,4M12,14C16.42,14 20,15.79 20,18V20H4V18C4,15.79 7.58,14 12,14Z">
                                        </path>
                                    </svg></span><span class="px-2 transition-colors">My Profile</span><!--v-if--></div>
                            <!--v-if-->
                        </a>
                        <div
                            class="block lg:flex items-center relative cursor-pointer navbar-item-label dark:text-white dark:hover:text-slate-400 py-2 px-3">
                            <div class="flex items-center"><!--v-if--><span
                                    class="inline-flex justify-center items-center w-6 h-6 transition-colors"><svg
                                        viewBox="0 0 24 24" width="16" height="16" class="inline-block">
                                        <path fill="currentColor"
                                            d="M12,8A4,4 0 0,1 16,12A4,4 0 0,1 12,16A4,4 0 0,1 8,12A4,4 0 0,1 12,8M12,10A2,2 0 0,0 10,12A2,2 0 0,0 12,14A2,2 0 0,0 14,12A2,2 0 0,0 12,10M10,22C9.75,22 9.54,21.82 9.5,21.58L9.13,18.93C8.5,18.68 7.96,18.34 7.44,17.94L4.95,18.95C4.73,19.03 4.46,18.95 4.34,18.73L2.34,15.27C2.21,15.05 2.27,14.78 2.46,14.63L4.57,12.97L4.5,12L4.57,11L2.46,9.37C2.27,9.22 2.21,8.95 2.34,8.73L4.34,5.27C4.46,5.05 4.73,4.96 4.95,5.05L7.44,6.05C7.96,5.66 8.5,5.32 9.13,5.07L9.5,2.42C9.54,2.18 9.75,2 10,2H14C14.25,2 14.46,2.18 14.5,2.42L14.87,5.07C15.5,5.32 16.04,5.66 16.56,6.05L19.05,5.05C19.27,4.96 19.54,5.05 19.66,5.27L21.66,8.73C21.79,8.95 21.73,9.22 21.54,9.37L19.43,11L19.5,12L19.43,13L21.54,14.63C21.73,14.78 21.79,15.05 21.66,15.27L19.66,18.73C19.54,18.95 19.27,19.04 19.05,18.95L16.56,17.95C16.04,18.34 15.5,18.68 14.87,18.93L14.5,21.58C14.46,21.82 14.25,22 14,22H10M11.25,4L10.88,6.61C9.68,6.86 8.62,7.5 7.85,8.39L5.44,7.35L4.69,8.65L6.8,10.2C6.4,11.37 6.4,12.64 6.8,13.8L4.68,15.36L5.43,16.66L7.86,15.62C8.63,16.5 9.68,17.14 10.87,17.38L11.24,20H12.76L13.13,17.39C14.32,17.14 15.37,16.5 16.14,15.62L18.57,16.66L19.32,15.36L17.2,13.81C17.6,12.64 17.6,11.37 17.2,10.2L19.31,8.65L18.56,7.35L16.15,8.39C15.38,7.5 14.32,6.86 13.12,6.62L12.75,4H11.25Z">
                                        </path>
                                    </svg></span><span class="px-2 transition-colors">Settings</span><!--v-if--></div>
                            <!--v-if-->
                        </div>
                        <div
                            class="block lg:flex items-center relative cursor-pointer navbar-item-label dark:text-white dark:hover:text-slate-400 py-2 px-3">
                            <div class="flex items-center"><!--v-if--><span
                                    class="inline-flex justify-center items-center w-6 h-6 transition-colors"><svg
                                        viewBox="0 0 24 24" width="16" height="16" class="inline-block">
                                        <path fill="currentColor"
                                            d="M20,8L12,13L4,8V6L12,11L20,6M20,4H4C2.89,4 2,4.89 2,6V18A2,2 0 0,0 4,20H20A2,2 0 0,0 22,18V6C22,4.89 21.1,4 20,4Z">
                                        </path>
                                    </svg></span><span class="px-2 transition-colors">Messages</span><!--v-if--></div>
                            <!--v-if-->
                        </div>
                        <hr class="hidden lg:block lg:my-0.5 dark:border-slate-700 border-t border-gray-100">
                        <div
                            class="block lg:flex items-center relative cursor-pointer navbar-item-label dark:text-white dark:hover:text-slate-400 py-2 px-3">
                            <div class="flex items-center"><!--v-if--><span
                                    class="inline-flex justify-center items-center w-6 h-6 transition-colors"><svg
                                        viewBox="0 0 24 24" width="16" height="16" class="inline-block">
                                        <path fill="currentColor"
                                            d="M16,17V14H9V10H16V7L21,12L16,17M14,2A2,2 0 0,1 16,4V6H14V4H5V20H14V18H16V20A2,2 0 0,1 14,22H5A2,2 0 0,1 3,20V4A2,2 0 0,1 5,2H14Z">
                                        </path>
                                    </svg></span><span class="px-2 transition-colors">Log Out</span><!--v-if--></div>
                            <!--v-if-->
                        </div>
                    </div>
                </div>
                <div
                    class="block lg:flex items-center relative cursor-pointer navbar-item-label dark:text-white dark:hover:text-slate-400 py-2 px-3 lg:w-16 lg:justify-center">
                    <div class="flex items-center"><!--v-if--><span
                            class="inline-flex justify-center items-center w-6 h-6 transition-colors"><svg
                                viewBox="0 0 24 24" width="16" height="16" class="inline-block">
                                <path fill="currentColor"
                                    d="M7.5,2C5.71,3.15 4.5,5.18 4.5,7.5C4.5,9.82 5.71,11.85 7.53,13C4.46,13 2,10.54 2,7.5A5.5,5.5 0 0,1 7.5,2M19.07,3.5L20.5,4.93L4.93,20.5L3.5,19.07L19.07,3.5M12.89,5.93L11.41,5L9.97,6L10.39,4.3L9,3.24L10.75,3.12L11.33,1.47L12,3.1L13.73,3.13L12.38,4.26L12.89,5.93M9.59,9.54L8.43,8.81L7.31,9.59L7.65,8.27L6.56,7.44L7.92,7.35L8.37,6.06L8.88,7.33L10.24,7.36L9.19,8.23L9.59,9.54M19,13.5A5.5,5.5 0 0,1 13.5,19C12.28,19 11.15,18.6 10.24,17.93L17.93,10.24C18.6,11.15 19,12.28 19,13.5M14.6,20.08L17.37,18.93L17.13,22.28L14.6,20.08M18.93,17.38L20.08,14.61L22.28,17.15L18.93,17.38M20.08,12.42L18.94,9.64L22.28,9.88L20.08,12.42M9.63,18.93L12.4,20.08L9.87,22.27L9.63,18.93Z">
                                </path>
                            </svg></span><span class="px-2 transition-colors lg:hidden">Light/Dark</span><!--v-if-->
                    </div><!--v-if-->
                </div>
                <div
                    class="block lg:flex items-center relative cursor-pointer navbar-item-label dark:text-white dark:hover:text-slate-400 py-2 px-3 lg:w-16 lg:justify-center">
                    <button @click="logout" href="/" class="flex items-center"><!--v-if-->
                        <span
                            class="inline-flex justify-center items-center w-6 h-6 transition-colors">
                            <svg
                                viewBox="0 0 24 24" width="16" height="16" class="inline-block">
                                <path fill="currentColor"
                                    d="M16,17V14H9V10H16V7L21,12L16,17M14,2A2,2 0 0,1 16,4V6H14V4H5V20H14V18H16V20A2,2 0 0,1 14,22H5A2,2 0 0,1 3,20V4A2,2 0 0,1 5,2H14Z">
                                </path>
                            </svg>
                        </span>
                        <span class="px-2 transition-colors lg:hidden">Log out</span><!--v-if-->
                    </button>
                    <!--v-if-->
                </div>
            </div>
        </div>
    </nav>
</template>

<style scoped></style>