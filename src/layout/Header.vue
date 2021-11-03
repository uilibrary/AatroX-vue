<script setup>
import { onMounted, ref, watch, watchEffect } from 'vue'
import { Switch } from '@headlessui/vue'
import HeaderSearch from '../components/HeaderSearch.vue'
import { Menu, MenuButton, MenuItems, MenuItem } from '@headlessui/vue'
import { useStore } from 'vuex'

let store = useStore()

const sideBarToggle = () => {
    let sidenav = store.state.largeSidebar.sidebarToggleProperties.isSideNavOpen

    if (sidenav == false) {
        store.commit('largeSidebar/toggleSidebarProperties')
    } else {
        store.commit('largeSidebar/toggleSidebarProperties')
    }
}
</script>

<template>
    <div class="header-wrapper flex bg-white justify-between px-4">
        <div class="flex items-center">
            <div class="logo flex justify-center">
                <svg
                    class="fill-current text-purple-500"
                    width="80"
                    height="80"
                    viewBox="0 0 80 80"
                    fill="none"
                    xmlns="http://www.w3.org/2000/svg"
                >
                    <g clip-path="url(#clip4)">
                        <path
                            d="M51.7498 27.8766C51.9863 28.0882 52.2228 28.1629 52.5837 28.138C55.8571 27.8766 59.118 27.9264 62.3541 28.5985C63.6734 28.8723 64.9803 29.1337 66.3867 29.5071C65.7644 29.9178 65.0798 29.9801 64.47 30.117C62.7399 30.5028 61.1094 31.15 59.479 31.7723C56.1931 33.0294 53.0816 34.635 50.0944 36.4646C45.5888 39.2401 41.4193 42.4762 37.4614 45.9861C33.9017 49.1474 30.6159 52.5453 27.467 56.0925C26.5957 57.0758 25.7991 58.1337 24.903 59.1045C23.509 60.623 21.7292 61.2702 19.688 60.9839C17.0494 60.6105 15.2197 59.0921 14.3236 56.6028C13.7137 54.935 14.0249 53.2423 14.7717 51.6492C16.2155 48.55 17.6717 45.4509 19.1403 42.3642C21.0073 38.4062 22.8867 34.4483 24.7537 30.4904C26.0854 27.6526 27.3923 24.8024 28.7365 21.9646C29.8193 19.6745 30.8897 17.3719 32.0472 15.1191C33.5906 12.1071 36.7146 10.6758 39.8511 11.0492C42.4399 11.3603 44.4562 12.6672 45.7258 15.0071C46.9082 17.1852 47.8541 19.4878 48.9494 21.7032C49.0489 21.9024 49.1361 22.114 49.2232 22.3131C49.0863 22.2882 48.9245 22.2135 48.8 22.2384C47.7545 22.4874 46.7215 22.7985 45.7507 23.259C43.4481 24.3792 41.2824 25.711 39.2661 27.2916C36.8142 29.2208 34.6983 31.4736 32.8313 33.9504C31.5618 35.6183 30.5039 37.4354 29.5331 39.3024C29.4584 39.4517 29.3464 39.626 29.4833 39.7504C29.67 39.9122 29.7571 39.6633 29.8691 39.5762C29.9687 39.5015 30.0309 39.3895 30.118 39.3024C31.3253 38.12 32.4579 36.8504 33.8022 35.8174C35.5446 34.4732 37.3245 33.1788 39.291 32.1457C40.7597 31.374 42.2159 30.6148 43.809 30.0921C45.0412 29.6938 46.2485 29.2582 47.5056 28.947C48.464 28.6981 49.4348 28.5612 50.3931 28.3122C50.8661 28.2251 51.3391 28.1629 51.7498 27.8766Z"
                            fill="none"
                            class="fill-current text-purple-500"
                        ></path>
                        <path
                            d="M44.6056 55.2841C40.573 58.4828 37.0755 62.1918 34.1009 66.3863C33.9515 66.4111 33.9017 66.4983 33.9017 66.6352C33.8768 66.6725 33.8519 66.7099 33.827 66.7596C33.6403 66.797 33.5408 66.9214 33.5159 67.1081L33.4785 67.133C33.4537 67.1704 33.4288 67.2077 33.4039 67.2451C33.379 67.2948 33.3665 67.3446 33.3416 67.3944C33.2296 67.4691 33.1425 67.5687 33.1425 67.718L33.1052 67.7554C32.9185 67.9047 32.8064 67.8674 32.7691 67.6184C32.9931 66.3365 33.4785 65.1292 33.9391 63.9343C34.9472 61.3455 36.1172 58.8189 37.4738 56.3918C38.5069 54.5373 39.6768 52.7699 40.909 51.0399C43.0871 47.9781 45.564 45.1652 48.3519 42.6386C50.6047 40.6099 53.0318 38.7927 55.7326 37.3738C56.0313 37.212 56.218 37.2244 56.3674 37.5605C57.8361 40.697 59.3047 43.8335 60.7858 46.9699C61.5824 48.6751 62.3665 50.3802 63.188 52.0605C64.9927 55.7571 62.9764 59.827 59.5163 61.1214C57.4129 61.9056 55.409 61.5695 53.5296 60.3996C52.7953 59.939 51.9987 59.603 51.3142 59.0554C51.3391 58.7317 51.2768 58.4081 51.3764 58.0721C51.6751 57.1635 51.9489 56.2549 52.2725 55.3463C52.621 54.3506 53.0442 53.3674 53.5545 52.4588C54.0275 51.6249 54.5004 50.7785 55.1476 50.0442C55.2099 49.9695 55.297 49.8699 55.1974 49.7828C55.1476 49.7455 55.0481 49.7455 54.9734 49.7579C54.5253 49.8202 54.127 50.0442 53.7039 50.1935C52.3472 50.6665 51.0528 51.2888 49.7957 51.9734C48.5884 52.633 47.4185 53.3674 46.2858 54.1639C45.7382 54.5622 45.203 54.9729 44.6056 55.2841Z"
                            fill="none"
                            class="fill-current text-purple-500"
                        ></path>
                        <path
                            d="M51.7498 27.8772C51.3391 28.1635 50.8661 28.2257 50.3932 28.3502C49.4348 28.5991 48.464 28.736 47.5056 28.985C46.2485 29.3086 45.0412 29.7317 43.809 30.13C42.2283 30.6403 40.7597 31.412 39.291 32.1837C37.3369 33.2167 35.5447 34.4987 33.8022 35.8553C32.4704 36.8884 31.3378 38.1704 30.118 39.3403C30.0309 39.4274 29.9562 39.5395 29.8691 39.6141C29.7571 39.7013 29.6575 39.9502 29.4833 39.7884C29.3464 39.6639 29.4584 39.4897 29.5331 39.3403C30.4914 37.4734 31.5618 35.6562 32.8313 33.9884C34.7107 31.5116 36.8142 29.2588 39.2661 27.3296C41.2824 25.7365 43.4481 24.4047 45.7507 23.297C46.709 22.824 47.7545 22.5253 48.8 22.2764C48.9245 22.2515 49.0738 22.3262 49.2232 22.3511C50.1069 24.1558 51.0279 25.9729 51.7498 27.8772Z"
                            fill="none"
                            class="fill-current text-purple-500"
                        ></path>
                        <path
                            d="M44.6056 55.2841C45.203 54.9605 45.7382 54.5498 46.2983 54.164C47.4309 53.3674 48.6009 52.6331 49.8082 51.9734C51.0652 51.2764 52.3597 50.6665 53.7163 50.1936C54.1395 50.0442 54.5378 49.8202 54.9858 49.758C55.0605 49.7455 55.1725 49.7331 55.2099 49.7829C55.3095 49.87 55.2223 49.9695 55.1601 50.0442C54.5129 50.7661 54.0399 51.6249 53.567 52.4588C53.0567 53.3674 52.6335 54.3382 52.285 55.3464C51.9614 56.255 51.6876 57.1635 51.3889 58.0721C51.2768 58.3957 51.3515 58.7318 51.3266 59.0554C49.9202 58.2464 48.5262 57.4498 47.1322 56.6408C46.4477 56.2425 45.7258 55.8816 45.0786 55.4086C44.9541 55.309 44.7674 55.3215 44.6056 55.2841Z"
                            fill="none"
                            class="fill-current text-purple-500"
                        ></path>
                        <path
                            d="M32.7691 67.6309C32.794 67.8798 32.906 67.9171 33.1051 67.7678C33.0304 68.2656 32.6944 68.5892 32.3832 69C32.4455 68.4897 32.4828 68.0167 32.7691 67.6309Z"
                            fill="none"
                            class="fill-current text-purple-500"
                        ></path>
                        <path
                            d="M33.5159 67.1206C33.5408 66.9339 33.6279 66.8094 33.827 66.7721C33.7897 66.9463 33.7399 67.1081 33.5159 67.1206Z"
                            fill="none"
                            class="fill-current text-purple-500"
                        ></path>
                        <path
                            d="M33.1425 67.7305C33.1425 67.5811 33.2296 67.4815 33.3417 67.4069C33.3417 67.5562 33.3043 67.6807 33.1425 67.7305Z"
                            fill="none"
                            class="fill-current text-purple-500"
                        ></path>
                        <path
                            d="M33.9017 66.6476C33.9017 66.5107 33.9515 66.4111 34.1009 66.3987C34.1009 66.5231 34.0138 66.5978 33.9017 66.6476Z"
                            fill="none"
                            class="fill-current text-purple-500"
                        ></path>
                        <path
                            d="M33.4039 67.2451C33.4288 67.2077 33.4537 67.1704 33.4785 67.1331C33.4537 67.1704 33.4288 67.2077 33.4039 67.2451Z"
                            fill="none"
                            class="fill-current text-purple-500"
                        ></path>
                    </g>
                    <defs>
                        <clipPath id="clip4">
                            <rect
                                width="52.3867"
                                height="58"
                                fill="white"
                                transform="translate(14 11)"
                            ></rect>
                        </clipPath>
                    </defs>
                </svg>
            </div>
            <div class="mx-0 sm:mx-3">
                <button
                    @click="sideBarToggle"
                    class="
                        menu-toggle
                        cursor-pointer
                        text-gray-500
                        align-middle
                        focus:outline-none
                    "
                    type="button"
                >
                    <svg
                        xmlns="http://www.w3.org/2000/svg"
                        class="h-6 w-6"
                        fill="none"
                        viewBox="0 0 24 24"
                        stroke="currentColor"
                    >
                        <path
                            stroke-linecap="round"
                            stroke-linejoin="round"
                            stroke-width="2"
                            d="M4 6h16M4 12h16M4 18h16"
                        />
                    </svg>
                </button>
            </div>
            <!-- mega-menu  -->

            <Menu as="div" class="relative inline-block text-left">
                <div>
                    <MenuButton
                        class="
                            btn-sm
                            mx-3
                            md:block
                            hidden
                            focus:outline-none
                            dropdown-button
                        "
                    >
                        <div class="flex items-center">
                            <p class="mr-2">Mega Menu</p>
                            <svg
                                xmlns="http://www.w3.org/2000/svg"
                                class="h-4 w-4 text-gray-500"
                                fill="none"
                                viewBox="0 0 24 24"
                                stroke="currentColor"
                            >
                                <path
                                    stroke-linecap="round"
                                    stroke-linejoin="round"
                                    stroke-width="2"
                                    d="M19 9l-7 7-7-7"
                                />
                            </svg>
                        </div>
                    </MenuButton>
                </div>

                <MenuItems
                    class="
                        absolute
                        mega-menu
                        left-0
                        mt-2
                        overflow-hidden
                        origin-top-right
                        bg-white
                        rounded-md
                        custom-box-shadow
                        focus:outline-none
                    "
                >
                    <div class="">
                        <MenuItem>
                            <div class="grid grid-cols-12 gap-5">
                                <div
                                    class="
                                        col-span-4
                                        bg-gradient-to-r
                                        from-purple-500
                                        to-purple-700
                                    "
                                >
                                    <div class="p-4">
                                        <p
                                            class="
                                                text-2xl text-white
                                                font-semibold
                                                mb-3
                                            "
                                        >
                                            Mega Menu Sidebar
                                        </p>
                                        <p class="text-white mb-4">
                                            Lorem ipsum dolor sit amet
                                            consectetur, adipisicing elit.
                                            Asperiores natus laboriosam fugit,
                                            consequatur.
                                        </p>
                                        <p class="text-white mb-4">
                                            Lorem ipsum dolor sit amet
                                            consectetur, adipisicing elit.
                                            Exercitationem odio amet eos dolore
                                            suscipit placeat.
                                        </p>
                                        <BaseBtn
                                            class="
                                                border border-yellow-500
                                                text-yellow-500
                                                hover:bg-yellow-500
                                                hover:text-white
                                            "
                                            rounded
                                            >Learn More</BaseBtn
                                        >
                                    </div>
                                </div>
                                <div class="col-span-4">
                                    <div class="p-4">
                                        <p
                                            class="
                                                text-purple-500
                                                border-b border-purple-500
                                                inline-block
                                                mb-4
                                            "
                                        >
                                            Features
                                        </p>
                                        <div
                                            class="
                                                menu-icon-grid
                                                flex
                                                justify-between
                                                flex-wrap
                                            "
                                        >
                                            <a
                                                class="
                                                    hover:bg-purple-500
                                                    hover:text-white
                                                    text-gray-600
                                                    p-5
                                                    inline-flex
                                                    flex-col
                                                    items-center
                                                    rounded
                                                    w-24
                                                "
                                                href="#"
                                            >
                                                <i class="i-Shop-4 text-2xl">
                                                </i
                                                >Home
                                            </a>
                                            <a
                                                class="
                                                    hover:bg-purple-500
                                                    hover:text-white
                                                    text-gray-600
                                                    p-5
                                                    inline-flex
                                                    flex-col
                                                    items-center
                                                    rounded
                                                    w-24
                                                "
                                                href="#"
                                            >
                                                <i
                                                    class="i-Library text-2xl"
                                                ></i
                                                >UI Kits
                                            </a>
                                            <a
                                                class="
                                                    hover:bg-purple-500
                                                    hover:text-white
                                                    text-gray-600
                                                    p-5
                                                    inline-flex
                                                    flex-col
                                                    items-center
                                                    rounded
                                                    w-24
                                                "
                                                href="#"
                                            >
                                                <i class="i-Drop text-2xl"></i
                                                >Apps
                                            </a>
                                            <a
                                                class="
                                                    hover:bg-purple-500
                                                    hover:text-white
                                                    text-gray-600
                                                    p-5
                                                    inline-flex
                                                    flex-col
                                                    items-center
                                                    rounded
                                                    w-24
                                                "
                                                href="#"
                                            >
                                                <i
                                                    class="
                                                        i-File-Clipboard-File--Text
                                                        text-2xl
                                                    "
                                                >
                                                </i
                                                >Forms
                                            </a>
                                            <a
                                                class="
                                                    hover:bg-purple-500
                                                    hover:text-white
                                                    text-gray-600
                                                    p-5
                                                    inline-flex
                                                    flex-col
                                                    items-center
                                                    rounded
                                                    w-24
                                                "
                                                href="#"
                                            >
                                                <i
                                                    class="
                                                        i-Checked-User
                                                        text-2xl
                                                    "
                                                ></i
                                                >Sessions
                                            </a>
                                            <a
                                                class="
                                                    hover:bg-purple-500
                                                    hover:text-white
                                                    text-gray-600
                                                    p-5
                                                    inline-flex
                                                    flex-col
                                                    items-center
                                                    rounded
                                                    w-24
                                                "
                                                href="#"
                                            >
                                                <i
                                                    class="i-Ambulance text-2xl"
                                                ></i
                                                >Support
                                            </a>
                                        </div>
                                    </div>
                                </div>
                                <div class="col-span-4">
                                    <div class="p-4">
                                        <p
                                            class="
                                                text-purple-500
                                                border-b border-purple-500
                                                inline-block
                                                mb-4
                                            "
                                        >
                                            Components
                                        </p>
                                        <ul class="links">
                                            <li>
                                                <a
                                                    class="
                                                        hover:text-purple-500
                                                        text-gray-600
                                                    "
                                                    href="#"
                                                    >Accordion
                                                </a>
                                            </li>
                                            <li>
                                                <a
                                                    class="
                                                        hover:text-purple-500
                                                        text-gray-600
                                                    "
                                                    href="#"
                                                    >Alerts
                                                </a>
                                            </li>
                                            <li>
                                                <a
                                                    class="
                                                        hover:text-purple-500
                                                        text-gray-600
                                                    "
                                                    href="#"
                                                    >Buttons
                                                </a>
                                            </li>
                                            <li>
                                                <a
                                                    class="
                                                        hover:text-purple-500
                                                        text-gray-600
                                                    "
                                                    href="#"
                                                    >Badges
                                                </a>
                                            </li>
                                            <li>
                                                <a
                                                    class="
                                                        hover:text-purple-500
                                                        text-gray-600
                                                    "
                                                    href="#"
                                                    >Carousels
                                                </a>
                                            </li>
                                            <li>
                                                <a
                                                    class="
                                                        hover:text-purple-500
                                                        text-gray-600
                                                    "
                                                    href="#"
                                                    >Lists
                                                </a>
                                            </li>
                                            <li>
                                                <a
                                                    class="
                                                        hover:text-purple-500
                                                        text-gray-600
                                                    "
                                                    href="#"
                                                    >Popover
                                                </a>
                                            </li>
                                            <li>
                                                <a
                                                    class="
                                                        hover:text-purple-500
                                                        text-gray-600
                                                    "
                                                    href="#"
                                                    >Tables
                                                </a>
                                            </li>
                                            <li>
                                                <a
                                                    class="
                                                        hover:text-purple-500
                                                        text-gray-600
                                                    "
                                                    href="#"
                                                    >Datatables
                                                </a>
                                            </li>
                                            <li>
                                                <a
                                                    class="
                                                        hover:text-purple-500
                                                        text-gray-600
                                                    "
                                                    href="#"
                                                    >Modals
                                                </a>
                                            </li>
                                            <li>
                                                <a
                                                    class="
                                                        hover:text-purple-500
                                                        text-gray-600
                                                    "
                                                    href="#"
                                                    >Sliders
                                                </a>
                                            </li>
                                            <li>
                                                <a
                                                    class="
                                                        hover:text-purple-500
                                                        text-gray-600
                                                    "
                                                    href="#"
                                                    >Tabs
                                                </a>
                                            </li>
                                        </ul>
                                    </div>
                                </div>
                            </div>
                        </MenuItem>
                    </div>
                </MenuItems>
            </Menu>

            <HeaderSearch />
        </div>
        <div class="flex items-center">
            <a
                class="
                    hidden
                    mr-0
                    btn btn-sm
                    hover:bg-gray-100
                    sm:block
                    rounded
                    p-1
                    md:mr-2
                "
                href="https://github.com/uilibrary/AatroX-vue"
                target="_blank"
            >
                <svg
                    width="24"
                    height="24"
                    fill="currentColor"
                    class="text-purple-600 text-opacity-50 transform"
                >
                    <path
                        fill-rule="evenodd"
                        clip-rule="evenodd"
                        d="M12 2C6.477 2 2 6.463 2 11.97c0 4.404 2.865 8.14 6.839 9.458.5.092.682-.216.682-.48 0-.236-.008-.864-.013-1.695-2.782.602-3.369-1.337-3.369-1.337-.454-1.151-1.11-1.458-1.11-1.458-.908-.618.069-.606.069-.606 1.003.07 1.531 1.027 1.531 1.027.892 1.524 2.341 1.084 2.91.828.092-.643.35-1.083.636-1.332-2.22-.251-4.555-1.107-4.555-4.927 0-1.088.39-1.979 1.029-2.675-.103-.252-.446-1.266.098-2.638 0 0 .84-.268 2.75 1.022A9.606 9.606 0 0112 6.82c.85.004 1.705.114 2.504.336 1.909-1.29 2.747-1.022 2.747-1.022.546 1.372.202 2.386.1 2.638.64.696 1.028 1.587 1.028 2.675 0 3.83-2.339 4.673-4.566 4.92.359.307.678.915.678 1.846 0 1.332-.012 2.407-.012 2.734 0 .267.18.577.688.48C19.137 20.107 22 16.373 22 11.969 22 6.463 17.522 2 12 2z"
                    ></path>
                </svg>
            </a>

            <Menu as="div" class="relative inline-block text-left">
                <div>
                    <MenuButton
                        class="
                            btn btn-sm
                            hover:bg-gray-100
                            rounded
                            w-full
                            px-4
                            py-2
                            text-sm
                            font-medium
                        "
                    >
                        <i class="i-Safe-Box text-gray-800 text-xl"></i>
                    </MenuButton>
                </div>

                <MenuItems
                    class="
                        absolute
                        right-0
                        w-40
                        mt-2
                        overflow-hidden
                        origin-top-right
                        bg-white
                        rounded-md
                        custom-box-shadow
                        focus:outline-none
                    "
                >
                    <div class="">
                        <MenuItem>
                            <div class="flex justify-between flex-wrap">
                                <a
                                    class="
                                        hover:bg-purple-500 hover:text-white
                                        text-gray-600
                                        p-4
                                        inline-flex
                                        flex-col
                                        items-center
                                        rounded
                                        w-20
                                    "
                                    href="#"
                                >
                                    <i class="i-Shop-4 text-2xl"> </i>Home
                                </a>
                                <a
                                    class="
                                        hover:bg-purple-500 hover:text-white
                                        text-gray-600
                                        p-4
                                        inline-flex
                                        flex-col
                                        items-center
                                        rounded
                                        w-20
                                    "
                                    href="#"
                                >
                                    <i class="i-Library text-2xl"></i>UI Kits
                                </a>
                                <a
                                    class="
                                        hover:bg-purple-500 hover:text-white
                                        text-gray-600
                                        p-4
                                        inline-flex
                                        flex-col
                                        items-center
                                        rounded
                                        w-20
                                    "
                                    href="#"
                                >
                                    <i class="i-Drop text-2xl"></i>Apps
                                </a>
                                <a
                                    class="
                                        hover:bg-purple-500 hover:text-white
                                        text-gray-600
                                        p-4
                                        inline-flex
                                        flex-col
                                        items-center
                                        rounded
                                        w-20
                                    "
                                    href="#"
                                >
                                    <i
                                        class="
                                            i-File-Clipboard-File--Text
                                            text-2xl
                                        "
                                    >
                                    </i
                                    >Forms
                                </a>
                                <a
                                    class="
                                        hover:bg-purple-500 hover:text-white
                                        text-gray-600
                                        p-4
                                        inline-flex
                                        flex-col
                                        items-center
                                        rounded
                                        w-20
                                    "
                                    href="#"
                                >
                                    <i class="i-Checked-User text-2xl"></i
                                    >Sessions
                                </a>
                                <a
                                    class="
                                        hover:bg-purple-500 hover:text-white
                                        text-gray-600
                                        p-4
                                        inline-flex
                                        flex-col
                                        items-center
                                        rounded
                                        w-20
                                    "
                                    href="#"
                                >
                                    <i class="i-Ambulance text-2xl"></i>Support
                                </a>
                            </div>
                        </MenuItem>
                    </div>
                </MenuItems>
            </Menu>
            <!-- notification-dropdown  -->
            <Menu as="div" class="relative inline-block text-left">
                <div>
                    <MenuButton
                        class="
                            btn btn-sm
                            hover:bg-gray-100
                            rounded
                            badge-top-container
                            inline-flex
                            justify-center
                            w-full
                            px-4
                            py-2
                            text-sm
                            font-medium
                        "
                    >
                        <span class="badge-count text-white bg-purple-500"
                            >3</span
                        >
                        <i class="i-Bell text-xl header-icon text-gray-800"></i>
                    </MenuButton>
                </div>

                <MenuItems
                    class="
                        absolute
                        right-0
                        w-44
                        mt-2
                        overflow-hidden
                        origin-top-right
                        bg-white
                        rounded-md
                        custom-box-shadow
                        focus:outline-none
                    "
                >
                    <div class="">
                        <MenuItem
                            v-for="(item, index) in 4"
                            :key="index"
                            v-slot="{ active }"
                        >
                            <button
                                :class="[
                                    active
                                        ? 'bg-purple-500 text-white'
                                        : 'text-gray-900',
                                    'group flex  items-center w-full px-4 py-2 text-sm',
                                ]"
                            >
                                <div class="flex flex-1 justify-between">
                                    <div>
                                        <h6>New Message</h6>
                                        <p
                                            :class="[
                                                active
                                                    ? 'text-gray-300'
                                                    : 'text-gray-500',
                                            ]"
                                        >
                                            How are you ?
                                        </p>
                                    </div>
                                    <div>
                                        <p
                                            :class="[
                                                active
                                                    ? 'text-gray-200'
                                                    : 'text-gray-400',
                                            ]"
                                        >
                                            10s
                                        </p>
                                    </div>
                                </div>
                            </button>
                        </MenuItem>
                    </div>
                </MenuItems>
            </Menu>

            <!-- profile-dropdown  -->
            <Menu as="div" class="relative inline-block text-left">
                <div>
                    <MenuButton
                        class="
                            inline-flex
                            justify-center
                            w-full
                            px-4
                            py-2
                            text-sm
                            font-medium
                        "
                    >
                        <img
                            class="avatar rounded-full"
                            src="/images/faces/1.jpg"
                            alt=""
                        />
                    </MenuButton>
                </div>

                <MenuItems
                    class="
                        absolute
                        right-0
                        w-44
                        mt-2
                        overflow-hidden
                        origin-top-right
                        bg-white
                        rounded-md
                        custom-box-shadow
                        focus:outline-none
                    "
                >
                    <div class="">
                        <MenuItem v-slot="{ active }">
                            <button
                                :class="[
                                    active
                                        ? 'bg-purple-500 text-white'
                                        : 'text-gray-900',
                                    'group flex  items-center w-full px-4 py-2 text-sm',
                                ]"
                            >
                                Account Settings
                            </button>
                        </MenuItem>
                        <MenuItem v-slot="{ active }">
                            <button
                                :class="[
                                    active
                                        ? 'bg-purple-500 text-white'
                                        : 'text-gray-900',
                                    'group flex  items-center w-full px-4 py-2 text-sm',
                                ]"
                            >
                                Billing History
                            </button>
                        </MenuItem>
                        <MenuItem v-slot="{ active }">
                            <button
                                :class="[
                                    active
                                        ? 'bg-purple-500 text-white'
                                        : 'text-gray-900',
                                    'group flex  items-center w-full px-4 py-2 text-sm',
                                ]"
                            >
                                Sign Out
                            </button>
                        </MenuItem>
                    </div>
                </MenuItems>
            </Menu>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.header-wrapper {
    position: fixed;
    top: 0;
    width: 100%;
    height: 80px;
    z-index: 100;
    box-shadow: 0 1px 15px rgb(0 0 0 / 4%), 0 1px 6px rgb(0 0 0 / 4%);
}
.mega-menu {
    width: 1200px;
}
ul.links {
    column-count: 2;
    li {
        margin-bottom: 8px;
    }
}
</style>
