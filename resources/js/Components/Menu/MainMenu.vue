<script setup>
import { Head, Link } from '@inertiajs/vue3';

</script>

<template>
    <div class="w-full z-50 bg-white border-b backdrop-blur-lg bg-opacity-80">
        <div class="mx-auto max-w-7xl px-6 sm:px-6 lg:px-8 ">
            <div class="relative flex h-16 justify-between">
                <Link class="flex flex-1 items-stretch justify-start" :href="route('home')">
                <a class="flex flex-shrink-0 items-center">
                    <img class="block h-12 w-auto" src="https://www.svgrepo.com/show/501888/donut.svg">
                </a>
                <p class="mt-auto mb-auto">YourPlan</p>
                </Link>
                <div v-if="!$page.props.auth.user" class="flex-shrink-0 flex px-2 py-3 items-center space-x-8">
                    <Link class="text-gray-700 hover:text-indigo-700 text-sm font-medium" :href="route('login')">
                    Login
                    </Link>
                    <Link
                        class="text-gray-800 bg-indigo-100 hover:bg-indigo-200 inline-flex items-center justify-center px-3 py-2 border border-transparent text-sm font-medium rounded-md shadow-sm"
                        :href="route('register')">
                    Register
                    </Link>
                </div>

                <div v-else class="mt-auto mb-auto">
                    <div class="dropdown dropdown-hover">
                        <div tabindex="0" role="button" class="btn m-1">Hola {{ $page.props.auth.user.name }}</div>
                        <ul tabindex="0" class="dropdown-content menu bg-base-100 rounded-box z-[1] w-52 p-2 shadow">
                            <li><Link :href="route('cabinet')" >My plan</Link></li>
                            <li><Link :href="route('dashboard')" >Profile</Link></li>
                            <li><Link :href="route('logout')" method="post">Logout</Link></li>
                        </ul>
                    </div>
                   
                </div>
            </div>
        </div>
        <!-- <h1>{{ $page.props.auth }}</h1> -->
    </div>
</template>
