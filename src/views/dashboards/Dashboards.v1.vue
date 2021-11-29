<script setup>
import {
    dashboardOne,
    dashboardTwo,
    splineAreaWidgetTwo,
    splineAreaWidgetThree,
} from '@/data/dashboard.v1.js'
import Breadcrumbs from '@/components/Breadcrumbs.vue'
</script>

<template>
    <div class="container mx-auto">
        <Breadcrumbs parentTitle="Dashboard" subParentTitle="Dashboard v1" />
        <div class="grid grid-cols-12 gap-5">
            <div
                class="
                    col-span-12
                    xl:col-span-3
                    lg:col-span-6
                    md:col-span-6
                    sm:col-span-6
                "
            >
                <BaseCard>
                    <div class="flex align-center">
                        <i class="i-Add-User text-6xl text-purple-200"></i>
                        <div class="m-auto">
                            <p class="text-gray-400">New Leads</p>
                            <p class="text-xl text-primary">205</p>
                        </div>
                    </div>
                </BaseCard>
            </div>
            <div
                class="
                    col-span-12
                    xl:col-span-3
                    lg:col-span-6
                    md:col-span-6
                    sm:col-span-6
                "
            >
                <BaseCard>
                    <div class="flex align-center">
                        <i class="i-Financial text-6xl text-purple-200"></i>
                        <div class="m-auto">
                            <p class="text-gray-400">Sales</p>
                            <p class="text-xl text-primary">$4021</p>
                        </div>
                    </div>
                </BaseCard>
            </div>
            <div
                class="
                    col-span-12
                    xl:col-span-3
                    lg:col-span-6
                    md:col-span-6
                    sm:col-span-6
                "
            >
                <BaseCard>
                    <div class="flex align-center">
                        <i
                            class="i-Checkout-Basket text-6xl text-purple-200"
                        ></i>
                        <div class="m-auto">
                            <p class="text-gray-400">Orders</p>
                            <p class="text-xl text-primary">$80</p>
                        </div>
                    </div>
                </BaseCard>
            </div>
            <div
                class="
                    col-span-12
                    xl:col-span-3
                    lg:col-span-6
                    md:col-span-6
                    sm:col-span-6
                "
            >
                <BaseCard>
                    <div class="flex align-center">
                        <i class="i-Money-2 text-6xl text-purple-200"></i>
                        <div class="m-auto">
                            <p class="text-gray-400">Expenses</p>
                            <p class="text-xl text-primary">$1200</p>
                        </div>
                    </div>
                </BaseCard>
            </div>
            <div class="col-span-12 xl:col-span-8 md:col-span-6">
                <BaseCard>
                    <h4 class="card-title mb-4">This Year Sales</h4>
                    <apexchart
                        type="bar"
                        height="255"
                        :options="dashboardOne.chartOptions"
                        :series="dashboardOne.series"
                    ></apexchart>
                </BaseCard>
            </div>
            <div class="col-span-12 xl:col-span-4 md:col-span-6">
                <BaseCard>
                    <h4 class="card-title mb-4">Sales By Countries</h4>
                    <apexchart
                        type="pie"
                        height="290"
                        :options="dashboardTwo.chartOptions"
                        :series="dashboardTwo.series"
                    ></apexchart>
                </BaseCard>
            </div>
            <div
                class="
                    col-span-12
                    xl:col-span-3
                    lg:col-span-3
                    md:col-span-6
                    sm:col-span-6
                "
            >
                <BaseCard noPadding class="overflow-hidden">
                    <div class="p-5">
                        <div class="text-gray-500">Last Month Sales</div>
                        <p class="text-primary text-2xl m-0">$40250</p>
                    </div>
                    <div id="basicArea-chart">
                        <apexchart
                            type="area"
                            height="270"
                            :options="splineAreaWidgetTwo.chartOptions"
                            :series="splineAreaWidgetTwo.series"
                        />
                    </div>
                </BaseCard>
            </div>

            <div
                class="
                    col-span-12
                    xl:col-span-3
                    lg:col-span-3
                    md:col-span-6
                    sm:col-span-6
                "
            >
                <BaseCard noPadding class="overflow-hidden">
                    <div class="p-5">
                        <div class="text-gray-500">Last Week Sales</div>
                        <p class="text-warning text-2xl m-0">$10250</p>
                    </div>
                    <div id="basicArea-chart">
                        <apexchart
                            type="area"
                            height="270"
                            :options="splineAreaWidgetThree.chartOptions"
                            :series="splineAreaWidgetThree.series"
                        />
                    </div>
                </BaseCard>
            </div>

            <div class="col-span-12 xl:col-span-6 lg:col-span-6">
                <BaseCard>
                    <div class="card-title mb-4">Top Selling Products</div>

                    <div class="flex flex-col items-center mb-4 md:flex-row">
                        <img
                            class="avatar-md mr-2 rounded w-20 h-20"
                            src="/images/products/headphone-4.jpg"
                            alt=""
                        />
                        <div class="flex-grow text-center md:text-left">
                            <h5>
                                <router-link
                                    to=""
                                    class="text-gray-800 hover:text-primary"
                                >
                                    Wireless Headphone E23
                                </router-link>
                            </h5>
                            <p class="text-gray-400 text-xs mb-3 md:mb-0">
                                Lorem ipsum dolor sit amet consectetur.
                            </p>
                            <div
                                class="
                                    flex
                                    justify-center
                                    mb-4
                                    md:justify-start md:mb-0
                                "
                            >
                                <p class="text-primary text-sm mr-2">$450</p>
                                <p
                                    class="
                                        text-gray-400
                                        line-through
                                        text-sm
                                        mr-2
                                    "
                                >
                                    $500
                                </p>
                            </div>
                        </div>
                        <BaseBtn
                            sm
                            class="
                                border border-primary
                                text-primary
                                rounded-full
                                hover:bg-primary hover:text-white
                            "
                            >View Details</BaseBtn
                        >
                    </div>
                    <div class="flex flex-col items-center mb-4 md:flex-row">
                        <img
                            class="avatar-md mr-2 rounded w-20 h-20"
                            src="/images/products/headphone-4.jpg"
                            alt=""
                        />
                        <div class="flex-grow text-center md:text-left">
                            <h5>
                                <router-link
                                    to=""
                                    class="text-gray-800 hover:text-primary"
                                >
                                    Wireless Headphone E23
                                </router-link>
                            </h5>
                            <p class="text-gray-400 text-xs mb-3 md:mb-0">
                                Lorem ipsum dolor sit amet consectetur.
                            </p>
                            <div
                                class="
                                    flex
                                    justify-center
                                    mb-4
                                    md:justify-start md:mb-0
                                "
                            >
                                <p class="text-primary text-sm mr-2">$450</p>
                                <p
                                    class="
                                        text-gray-400
                                        line-through
                                        text-sm
                                        mr-2
                                    "
                                >
                                    $500
                                </p>
                            </div>
                        </div>
                        <BaseBtn
                            sm
                            class="
                                border border-primary
                                text-primary
                                rounded-full
                                hover:bg-primary hover:text-white
                            "
                            >View Details</BaseBtn
                        >
                    </div>
                    <div class="flex flex-col items-center mb-4 md:flex-row">
                        <img
                            class="avatar-md mr-2 rounded w-20 h-20"
                            src="/images/products/headphone-4.jpg"
                            alt=""
                        />
                        <div class="flex-grow text-center md:text-left">
                            <h5>
                                <router-link
                                    to=""
                                    class="text-gray-800 hover:text-primary"
                                >
                                    Wireless Headphone E23
                                </router-link>
                            </h5>
                            <p class="text-gray-400 text-xs mb-3 md:mb-0">
                                Lorem ipsum dolor sit amet consectetur.
                            </p>
                            <div
                                class="
                                    flex
                                    justify-center
                                    mb-4
                                    md:justify-start md:mb-0
                                "
                            >
                                <p class="text-primary text-sm mr-2">$450</p>
                                <p
                                    class="
                                        text-gray-400
                                        line-through
                                        text-sm
                                        mr-2
                                    "
                                >
                                    $500
                                </p>
                            </div>
                        </div>
                        <BaseBtn
                            sm
                            class="
                                border border-primary
                                text-primary
                                rounded-full
                                hover:bg-primary hover:text-white
                            "
                            >View Details</BaseBtn
                        >
                    </div>
                </BaseCard>
            </div>
            <div
                class="
                    col-span-12
                    xl:col-span-3
                    lg:col-span-3
                    md:col-span-6
                    sm:col-span-6
                "
            >
                <BaseCard class="text-center">
                    <img
                        class="
                            w-20
                            h-20
                            m-auto
                            shadow-lg
                            avatar-md
                            rounded-full
                        "
                        src="/images/faces/2.jpg"
                        alt=""
                    />
                    <p class="text-base mt-4">Jhon Doe</p>
                    <p class="text-xs text-gray-400">Top Buyer</p>
                    <p class="my-2 text-sm text-gray-500 mb-3">
                        Lorem ipsum dolor sit amet consectetur adipisicing elit.
                        Recusandae cumque.
                    </p>
                    <BaseBtn sm class="bg-primary text-white rounded-full">
                        Contact Jessica
                    </BaseBtn>
                    <div class="mt-4">
                        <router-link to="" class="mr-2 hover:text-primary">
                            <i class="i-Linkedin-2 text-xs"></i>
                        </router-link>
                        <router-link to="" class="mr-2 hover:text-primary">
                            <i class="i-Facebook-2 text-xs"></i>
                        </router-link>
                        <router-link to="" class="mr-2 hover:text-primary">
                            <i class="i-Twitter text-xs"></i>
                        </router-link>
                    </div>
                </BaseCard>
            </div>
            <div
                class="
                    col-span-12
                    xl:col-span-3
                    lg:col-span-3
                    md:col-span-6
                    sm:col-span-6
                "
            >
                <BaseCard class="text-center">
                    <img
                        class="
                            w-20
                            h-20
                            m-auto
                            shadow-lg
                            avatar-md
                            rounded-full
                        "
                        src="/images/faces/9.jpg"
                        alt=""
                    />
                    <p class="text-base mt-4">Jhon Doe</p>
                    <p class="text-xs text-gray-400">Top Buyer</p>
                    <p class="my-2 text-sm text-gray-500 mb-3">
                        Lorem ipsum dolor sit amet consectetur adipisicing elit.
                        Recusandae cumque.
                    </p>
                    <BaseBtn sm class="bg-primary text-white rounded-full">
                        Contact Jessica
                    </BaseBtn>
                    <div class="mt-4">
                        <router-link to="" class="mr-2 hover:text-primary">
                            <i class="i-Linkedin-2 text-xs"></i>
                        </router-link>
                        <router-link to="" class="mr-2 hover:text-primary">
                            <i class="i-Facebook-2 text-xs"></i>
                        </router-link>
                        <router-link to="" class="mr-2 hover:text-primary">
                            <i class="i-Twitter text-xs"></i>
                        </router-link>
                    </div>
                </BaseCard>
            </div>
            <div class="col-span-12 card xl:col-span-6 lg:col-span-12">
                <BaseCard>
                    <div class="flex justify-between p-4">
                        <div class="card-title">User Activity</div>
                        <span
                            class="
                                rounded-full
                                flex
                                items-center
                                text-white
                                bg-warning
                                px-4
                                text-xs
                            "
                            >Updated Daily</span
                        >
                    </div>
                    <div class="divide-y divide-gray-200">
                        <div class="p-3">
                            <div class="flex justify-between">
                                <div>
                                    <p class="text-xs text-gray-400">
                                        Pages / Visit
                                    </p>
                                    <p class="text-lg font-normal mb-0">2065</p>
                                </div>
                                <div>
                                    <p class="text-xs text-gray-400">
                                        New / user
                                    </p>
                                    <p class="text-lg font-normal mb-0">465</p>
                                </div>
                                <div>
                                    <p class="text-xs text-gray-400">
                                        Last week
                                    </p>
                                    <p class="text-lg font-normal mb-0">
                                        23456
                                    </p>
                                </div>
                            </div>
                        </div>
                        <div class="p-3">
                            <div class="flex justify-between">
                                <div>
                                    <p class="text-xs text-gray-400">
                                        Pages / Visit
                                    </p>
                                    <p class="text-lg font-normal mb-0">1829</p>
                                </div>
                                <div>
                                    <p class="text-xs text-gray-400">
                                        New / user
                                    </p>
                                    <p class="text-lg font-normal mb-0">735</p>
                                </div>
                                <div>
                                    <p class="text-xs text-gray-400">
                                        Last week
                                    </p>
                                    <p class="text-lg font-normal mb-0">
                                        92565
                                    </p>
                                </div>
                            </div>
                        </div>
                        <div class="p-3">
                            <div class="flex justify-between">
                                <div>
                                    <p class="text-xs text-gray-400">
                                        Pages / Visit
                                    </p>
                                    <p class="text-lg font-normal mb-0">3165</p>
                                </div>
                                <div>
                                    <p class="text-xs text-gray-400">
                                        New / user
                                    </p>
                                    <p class="text-lg font-normal mb-0">165</p>
                                </div>
                                <div>
                                    <p class="text-xs text-gray-400">
                                        Last week
                                    </p>
                                    <p class="text-lg font-normal mb-0">
                                        32165
                                    </p>
                                </div>
                            </div>
                        </div>
                    </div>
                </BaseCard>
            </div>
            <div class="col-span-12">
                <BaseCard>
                    <template v-slot:cardHeader>
                        <div class="card-header">
                            <div class="card-title py-3">Recent Orders</div>
                        </div>
                    </template>
                    <div
                        class="
                            block
                            w-full
                            overflow-x-auto
                            whitespace-nowrap
                            borderless
                            hover
                        "
                    >
                        <div
                            class="
                                dataTable-wrapper dataTable-loading
                                no-footer
                                fixed-columns
                            "
                        >
                            <div
                                class="
                                    dataTable-container
                                    block
                                    w-full
                                    overflow-x-auto
                                    whitespace-nowrap
                                    borderless
                                    hover
                                "
                            >
                                <table
                                    class="
                                        table-3
                                        dataTable-table
                                        max-w-full
                                        w-full
                                    "
                                >
                                    <thead>
                                        <tr class="">
                                            <th
                                                class="
                                                    text-left
                                                    border-b
                                                    pb-3
                                                    mb-3
                                                    text-gray-500
                                                    font-semibold
                                                "
                                            >
                                                Order Id
                                            </th>
                                            <th
                                                class="
                                                    text-left
                                                    border-b
                                                    pb-3
                                                    mb-3
                                                    text-gray-500
                                                    font-semibold
                                                "
                                            >
                                                Buyer Name
                                            </th>
                                            <th
                                                class="
                                                    text-left
                                                    border-b
                                                    pb-3
                                                    mb-3
                                                    text-gray-500
                                                    font-semibold
                                                "
                                            >
                                                Product
                                            </th>
                                            <th
                                                class="
                                                    text-left
                                                    border-b
                                                    pb-3
                                                    mb-3
                                                    text-gray-500
                                                    font-semibold
                                                "
                                            >
                                                Status
                                            </th>
                                            <th
                                                class="
                                                    text-left
                                                    border-b
                                                    pb-3
                                                    mb-3
                                                    text-gray-500
                                                    font-semibold
                                                "
                                            >
                                                Shipping Cost
                                            </th>
                                            <th
                                                class="
                                                    text-left
                                                    border-b
                                                    pb-3
                                                    mb-3
                                                    text-gray-500
                                                    font-semibold
                                                "
                                            >
                                                Date
                                            </th>
                                            <th
                                                class="
                                                    text-left
                                                    border-b
                                                    pb-3
                                                    mb-3
                                                    text-gray-500
                                                    font-semibold
                                                "
                                            >
                                                Action
                                            </th>
                                        </tr>
                                    </thead>
                                    <tbody>
                                        <tr
                                            class="
                                                hover:bg-gray-100
                                                cursor-pointer
                                            "
                                            v-for="(n, index) in 8"
                                            :key="index"
                                        >
                                            <td class="text-xs py-5 px-4">
                                                {{ index + 1 }}
                                            </td>

                                            <td class="text-xs">
                                                Jhon {{ index + 1 }}
                                            </td>
                                            <td class="py-5">
                                                <div class="flex">
                                                    <img
                                                        class="
                                                            w-9
                                                            h-9
                                                            rounded-full
                                                            mr-2
                                                        "
                                                        src="/images/products/speaker-1.jpg"
                                                        alt=""
                                                    />
                                                    <img
                                                        class="
                                                            w-9
                                                            h-9
                                                            rounded-full
                                                            mr-2
                                                        "
                                                        src="/images/products/headphone-1.jpg"
                                                        alt=""
                                                    />
                                                </div>
                                            </td>
                                            <td class="py-5">
                                                <span
                                                    class="
                                                        px-3
                                                        py-1
                                                        rounded-full
                                                        text-primary
                                                        border border-primary
                                                        mr-3
                                                        text-xs
                                                    "
                                                    >Delivered</span
                                                >
                                            </td>
                                            <td class="py-5">
                                                {{ 3.34 * index + 1 }}%
                                            </td>
                                            <td class="py-5">12-02-20</td>
                                            <td class="py-5">
                                                <BaseBtn
                                                    rounded
                                                    class="
                                                        border border-primary
                                                        text-primary
                                                        hover:bg-primary
                                                        hover:text-white
                                                    "
                                                >
                                                    View
                                                </BaseBtn>
                                            </td>
                                        </tr>
                                    </tbody>
                                </table>
                            </div>
                            <div class="dataTable-bottom">
                                <div class="dataTable-info">
                                    Showing 1 to 8 of 8 entries
                                </div>
                                <nav class="dataTable-pagination">
                                    <ul class="dataTable-pagination-list"></ul>
                                </nav>
                            </div>
                        </div>
                    </div>
                </BaseCard>
            </div>
        </div>
    </div>
</template>
