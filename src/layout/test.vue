<script setup>
import { useStore } from 'vuex'
import { ref, onMounted, onBeforeUnmount } from 'vue'
import { useRoute } from 'vue-router';
import {
Disclosure,
DisclosureButton,
DisclosurePanel,
} from '@headlessui/vue'
let store = useStore()
const route = useRoute();

let selectedParentMenu = ref('')
let isMenuOver = ref(false)



onMounted(() => {
    toggleSelectedParentMenu()  
    document.addEventListener("click", returnSelectedParentMenu);
})

// beforeDestroy 
onBeforeUnmount(() => {
    document.removeEventListener("click", returnSelectedParentMenu);
}) 

const returnSelectedParentMenu = () => {
      if (!isMenuOver.value) {
        toggleSelectedParentMenu();
      }
    

}
const removeOverlay = () => {
    store.dispatch('largeSidebar/changeSecondarySidebarPropertiesViaMenuItem');
    // if (window.innerWidth <= 1200) {
    //     this.changeSidebarProperties();
    // }
    toggleSelectedParentMenu();
   
}

let toggleSelectedParentMenu = () => {
    let currentParentUrl = route.path.split("/").filter(x => x !== "")[0]
   
    if (currentParentUrl !== undefined || currentParentUrl !== null) {
        selectedParentMenu.value = currentParentUrl.toLowerCase();
       
    } else {
        selectedParentMenu.value = "dashboards";
    }

}
let toggleSubMenu = (e) => {
    let hasSubmenu = e.target.dataset.submenu;
    let parent = e.target.dataset.item;
   
    
    if (hasSubmenu) {
        selectedParentMenu.value = parent;
        store.dispatch('largeSidebar/changeSecondarySidebarPropertiesViaMenuItem', true)

    } 
    else {
        selectedParentMenu.value = parent;
        store.dispatch('largeSidebar/changeSecondarySidebarPropertiesViaMenuItem', false)    
    }
    
}



</script>
<template>
    <div 
        class="side-content-wrap"
        @mouseenter="isMenuOver = true"
        @mouseleave="isMenuOver = false"
        @touchstart="isMenuOver = true"
    >
        <div class="side-content-wrap">
            <div
                :class="
                    store.state.largeSidebar.sidebarToggleProperties
                        .isSideNavOpen === true
                        ? 'open'
                        : ''
                "
                class="sidebar-left"
            >
                <perfect-scrollbar>
                    <ul class="navigation-left">
                        <li 
                            @mouseenter="toggleSubMenu" 
                            class="nav-item" 
                            :class="selectedParentMenu == 'dashboards' ? 'active' : ''"
                            data-item="dashboards"
                            :data-submenu=true
                        >
                            <a class="nav-item-hold" href="#">
                                <i class="i-Bar-Chart text-3xl"></i>
                                <p>Dashboard</p>
                            </a>
                        </li>
                        <li 
                            @mouseenter="toggleSubMenu" 
                            class="nav-item" 
                            :class="selectedParentMenu == 'apps' ? 'active' : ''"
                            data-item="apps"
                            :data-submenu=true
                        >
                            <a class="nav-item-hold" href="#"
                                ><i class="i-Computer-Secure text-3xl"></i>
                                <p>Apps</p>
                            </a>
                        </li>
                        <li 
                            @mouseenter="toggleSubMenu" 
                            class="nav-item" 
                            :class="selectedParentMenu == 'components' ? 'active' : ''"
                            data-item="components"
                            :data-submenu=true
                        >
                            <a class="nav-item-hold" href="#"
                                ><i class="i-Wallet text-3xl"></i>
                                <p>Components</p>
                            </a>
                        </li>
                        <li 
                            @mouseenter="toggleSubMenu" 
                            class="nav-item" 
                            data-item="widgets"
                            :data-submenu=true
                        >
                            <a class="nav-item-hold" href="#"
                                ><i class="i-Atom text-3xl"></i>
                                <p>Widgets</p>
                            </a>
                        </li>
                        <!-- <li 
                            @mouseenter="toggleSubMenu" 
                            class="nav-item" 
                            :class="selectedParentMenu == 'components' ? 'active' : ''"
                            data-item="components"
                            :data-submenu=true
                        >
                            <a class="nav-item-hold" href="#"
                                ><i class="i-Wallet text-3xl"></i>
                                <p>Components</p>
                            </a>
                        </li> -->
                        <li 
                            @mouseenter="toggleSubMenu" 
                            class="nav-item" 
                            :class="selectedParentMenu == 'profile' ? 'active' : ''"
                            data-item="profile"
                            :data-submenu=true
                        >
                            <a class="nav-item-hold" href="#"
                                ><i class="i-Find-User text-3xl"></i>
                                <p>Profile</p>
                            </a>
                        </li>
                        <li class="nav-item" data-item="sessions">
                            <a class="nav-item-hold" href="#"
                                ><i class="i-Administrator text-3xl"></i>
                                <p>Session</p>
                            </a>
                        </li>
                        <li class="nav-item" data-item="charts">
                            <a class="nav-item-hold" href="#"
                                ><i class="i-Pie-Chart-2 text-3xl"></i>
                                <p>Charts</p>
                            </a>
                        </li>
                        <li  
                          class="nav-item" 
                          data-item="vuexDemo"
                          :class="selectedParentMenu == 'vuexDemo' ? 'active' : ''"
                          :data-submenu=true
                        >
                            <router-link to="/vuexDemo" class="nav-item-hold" href="#"
                                ><i class="i-Pie-Chart-2 text-3xl"></i>
                                <p>Doc</p>
                            </router-link>
                        </li>
                    </ul>
                </perfect-scrollbar>
            </div>

            <div 
                :class="{ open: store.state.largeSidebar.sidebarToggleProperties.isSecondarySideNavOpen }"
                class="sidebar-left-secondary shadow"
            >
                <ul
                    class="mb-4 childNav"
                    data-parent="dashboards"
                    :class="selectedParentMenu  == 'dashboards' ? 'block' : 'hidden'"
                >
                    <li>
                        <router-link tag="a" to="/dashboards/dashboard-version-one">
                            <i class="nav-icon i-Clock mr-2"></i>
                            <span class="item-name">
                                Version One
                            </span>
                        </router-link>
                    </li>
                    <li>
                        <router-link tag="a" class to="/dashboards/dashboard-version-two">
                            <i class="nav-icon i-Clock-4 mr-2"></i>
                            <span class="item-name">
                                Version Two
                            </span>
                        </router-link>
                    </li>
                    <li>
                        <router-link tag="a" class to="/dashboards/dashboard-version-three">
                            <i class="nav-icon i-Over-Time mr-2"></i>
                            <span class="item-name">
                                Version Three
                            </span>
                        </router-link>
                    </li>
                    <li>
                        
                        <router-link tag="a" class to="/dashboards/dashboard-version-four">
                            <i class="nav-icon i-Over-Time mr-2"></i>
                            <span class="item-name">
                                Version Four
                            </span>
                        </router-link>
                    </li>
                    <li>
                        <router-link tag="a" class to="/dashboards/dashboard-version-five">
                            <i class="nav-icon i-Clock text-base mr-2"></i>
                            <span class="item-name">
                                Version Five
                            </span>
                        </router-link>
                    </li>
                </ul>
                <ul
                    class="mb-4 childNav"
                    data-parent="apps"
                    
                    :class="selectedParentMenu == 'apps' ? 'block' : 'hidden'"
                >
                    <li>
                        <a class="flex" href="apps/app.event-calendar.html"
                            ><i class="nav-icon i-Calendar-4 text-base mr-2"></i
                            ><span class="item-name">Calendar</span></a
                        >
                    </li>
                    <li>
                        <a class="flex" href="apps/chat.html"
                            ><i class="nav-icon i-Book text-base mr-2"></i
                            ><span class="item-name">Chat</span></a
                        >
                    </li>
                    <li class="dropdown-sidemenu">
                        <a class="submenuLi"
                            ><i
                                class="nav-icon i-Bar-Chart-2 text-base mr-2"
                            ></i
                            ><span class="item-name">Contact</span
                            ><i class="dd-arrow i-Arrow-Down"></i
                        ></a>
                        <ul class="submenu">
                            <li class="hover:bg-gray-100">
                                <a
                                    class="
                                        hover:text-purple-500
                                        flex
                                        items-center
                                    "
                                    href="apps/app.contact-table.html"
                                >
                                    <span
                                        class="
                                            material-icons
                                            text-xs text-gray-800
                                            mr-2
                                        "
                                        >radio_button_unchecked</span
                                    >
                                    <p>Contact Table</p>
                                </a>
                            </li>
                            <li class="hover:bg-gray-100">
                                <a
                                    class="
                                        hover:text-purple-500
                                        flex
                                        items-center
                                    "
                                    href="apps/app.contact-list.html"
                                >
                                    <span
                                        class="
                                            material-icons
                                            text-xs text-gray-800
                                            mr-2
                                        "
                                        >radio_button_unchecked</span
                                    >
                                    <p>Contact List</p>
                                </a>
                            </li>
                            <li class="hover:bg-gray-100">
                                <a
                                    class="
                                        hover:text-purple-500
                                        flex
                                        items-center
                                    "
                                    href="apps/app.contact-grid.html"
                                >
                                    <span
                                        class="
                                            material-icons
                                            text-xs text-gray-800
                                            mr-2
                                        "
                                        >radio_button_unchecked</span>
                                    <p>Contact Grid</p>
                                </a>
                            </li>
                        </ul>
                    </li>
                    <li class="dropdown-sidemenu">
                        <Disclosure v-slot="{ open }">
                            <DisclosureButton
                                class="submenuLi hover:text-purple-500 items-center flex justify-between w-full px-6 py-2 text-sm text-left  hover:bg-gray-100 focus:outline-none focus-visible:ring focus-visible:ring-purple-500 focus-visible:ring-opacity-75"
                            >
                                <div class="flex items-center">
                                    <i class="nav-icon i-Bar-Chart-2 text-base mr-2"></i>
                                    <span>Contact</span>
                                </div>
                                <svg xmlns="http://www.w3.org/2000/svg"
                                     :class="open ? 'transform rotate-90 ' : ''"
                                     class="h-4 w-4 submenuli-icon transition duration-300 ease-in-out" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
                                </svg>
                                
                            </DisclosureButton>
                            <transition
                                enter-active-class="transition duration-100 ease-out"
                                enter-from-class="transform scale-95 opacity-0"
                                enter-to-class="transform scale-100 opacity-100"
                                leave-active-class="transition duration-75 ease-out"
                                leave-from-class="transform scale-100 opacity-100"
                                leave-to-class="transform scale-95 opacity-0"
                            >
                                <DisclosurePanel class="px-6 py-2 pb-2 text-sm text-gray-500 bg-gray-50 text-xs">
                                   <ul class="">
                                       <li class="py-2 hover:text-purple-500"> 
                                           <router-link to="" class="flex align-center submneu-nested-link">
                                               <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mr-2" viewBox="0 0 20 20" fill="currentColor">
                                                 <path fill-rule="evenodd" d="M5 10a1 1 0 011-1h8a1 1 0 110 2H6a1 1 0 01-1-1z" clip-rule="evenodd" />
                                               </svg>
                                               Contact Table
                                           </router-link>
                                       </li>
                                       <li class="py-2"> 
                                           <router-link to="" class="flex align-center submneu-nested-link">
                                               <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mr-2" viewBox="0 0 20 20" fill="currentColor">
                                                 <path fill-rule="evenodd" d="M5 10a1 1 0 011-1h8a1 1 0 110 2H6a1 1 0 01-1-1z" clip-rule="evenodd" />
                                               </svg>
                                               Contact Table Two
                                           </router-link>
                                       </li>
                                       <li class="py-2"> 
                                           <router-link to="/contact/contact-grid" class="flex align-center submneu-nested-link">
                                               <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mr-2" viewBox="0 0 20 20" fill="currentColor">
                                                 <path fill-rule="evenodd" d="M5 10a1 1 0 011-1h8a1 1 0 110 2H6a1 1 0 01-1-1z" clip-rule="evenodd" />
                                               </svg>
                                               Contact Grid
                                           </router-link>
                                       </li>
                                   </ul>


                                </DisclosurePanel>
                            </transition>
                            </Disclosure>
                    </li>
                    <li class="dropdown-sidemenu">
                        <a class="submenuLi"
                            ><i
                                class="nav-icon i-Bar-Chart-2 text-base mr-2"
                            ></i
                            ><span class="item-name">Ecommerce</span
                            ><i class="dd-arrow i-Arrow-Down"></i
                        ></a>
                        <ul class="submenu">
                            <li class="hover:bg-gray-100">
                                <a
                                    class="
                                        hover:text-purple-500
                                        flex
                                        items-center
                                    "
                                    href="apps/app.ecommerce.html"
                                >
                                    <span
                                        class="
                                            material-icons
                                            text-xs text-gray-800
                                            mr-2
                                        "
                                        >radio_button_unchecked</span
                                    >
                                    <p>Product</p>
                                </a>
                            </li>
                            <li class="hover:bg-gray-100">
                                <a
                                    class="
                                        hover:text-purple-500
                                        flex
                                        items-center
                                    "
                                    href="apps/app.ecommerce-list.html"
                                >
                                    <span
                                        class="
                                            material-icons
                                            text-xs text-gray-800
                                            mr-2
                                        "
                                        >radio_button_unchecked</span
                                    >
                                    <p>Cart</p>
                                </a>
                            </li>
                            <li class="hover:bg-gray-100">
                                <a
                                    class="
                                        hover:text-purple-500
                                        flex
                                        items-center
                                    "
                                    href="apps/app.ecommerce-payment-view.html"
                                >
                                    <span
                                        class="
                                            material-icons
                                            text-xs text-gray-800
                                            mr-2
                                        "
                                        >radio_button_unchecked</span
                                    >
                                    <p>Checkout</p>
                                </a>
                            </li>
                        </ul>
                    </li>
                    <li>
                        <a class="flex" href="apps/app.inbox.html"
                            ><i class="nav-icon i-Add-Cart text-base mr-2"></i
                            ><span class="item-name">Inbox</span></a
                        >
                    </li>
                    <li class="dropdown-sidemenu">
                        <a class="submenuLi"
                            ><i
                                class="nav-icon i-Bar-Chart-2 text-base mr-2"
                            ></i
                            ><span class="item-name">Invoice</span
                            ><i class="dd-arrow i-Arrow-Down"></i
                        ></a>
                        <ul class="submenu">
                            <li class="hover:bg-gray-100">
                                <a
                                    class="
                                        hover:text-primary-400
                                        flex
                                        items-center
                                    "
                                    href="apps/app.create-invoice.html"
                                >
                                    <span
                                        class="
                                            material-icons
                                            text-xs text-gray-800
                                            mr-2
                                        "
                                        >radio_button_unchecked</span
                                    >
                                    <p>Create Invoice</p>
                                </a>
                            </li>
                            <li class="hover:bg-gray-100">
                                <a
                                    class="
                                        hover:text-primary-400
                                        flex
                                        items-center
                                    "
                                    href="apps/app.print-invoice.html"
                                >
                                    <span
                                        class="
                                            material-icons
                                            text-xs text-gray-800
                                            mr-2
                                        "
                                        >radio_button_unchecked</span
                                    >
                                    <p>print Invoice</p>
                                </a>
                            </li>
                            <li class="hover:bg-gray-100">
                                <a
                                    class="
                                        hover:text-primary-400
                                        flex
                                        items-center
                                    "
                                    href="apps/app.invoice-list.html"
                                >
                                    <span
                                        class="
                                            material-icons
                                            text-xs text-gray-800
                                            mr-2
                                        "
                                        >radio_button_unchecked</span
                                    >
                                    <p>List Invoice</p>
                                </a>
                            </li>
                        </ul>
                    </li>
                    <li>
                        <a class="flex" href="apps/app.todo-list.html"
                            ><i class="nav-icon i-Book text-base mr-2"></i
                            ><span class="item-name">Todo List</span></a
                        >
                    </li>
                </ul>
                <ul
                    class="mb-4 childNav"
                    data-parent="components"
                    :class="selectedParentMenu == 'components' ? 'block' : 'hidden'"
                >
                    <!-- <li>
                        <a href="components/components.animation.html"
                            ><i class="nav-icon i-Clock-4 text-base mr-2"></i
                            ><span class="item-name">Animation</span></a
                        >
                        
                    </li>
                    <li>
                        <a href="components/components.alert.html"
                            ><i class="nav-icon i-Over-Time text-base mr-2"></i
                            ><span class="item-name">Alert</span></a
                        >
                    </li>
                    <li>
                        <a href="components/components.avatar.html"
                            ><i class="nav-icon i-Clock text-base mr-2"></i
                            ><span class="item-name">Avatars</span></a
                        >
                    </li>
                    <li>
                        <a href="components/components.badge.html"
                            ><i class="nav-icon i-Clock text-base mr-2"></i
                            ><span class="item-name">Badge</span></a
                        >
                    </li> -->
                    <li>
                        <router-link tag="a" class to="/components/button">
                            <i class="nav-icon i-Clock mr-2"></i>
                            <span class="item-name">
                                Buttons
                            </span>
                        </router-link>
                    </li>
                    <li>
                        <router-link tag="a" class to="/components/badges">
                            <i class="nav-icon i-Clock mr-2"></i>
                            <span class="item-name">
                                Badges
                            </span>
                        </router-link>
                    </li>
                    <li>
                        <router-link tag="a" class to="/components/accordions">
                            <i class="nav-icon i-Split-Horizontal-2-Window mr-2"></i>
                            <span class="item-name">
                                Accordions
                            </span>
                        </router-link>
                    </li>
                    <li>
                        <router-link tag="a" class to="/components/alerts">
                            <i class="nav-icon i-Bell1 mr-2"></i>
                            <span class="item-name">
                                Alerts
                            </span>
                        </router-link>
                    </li>
                    <li>
                        <router-link tag="a" class to="/components/tabs">
                            <i class="nav-icon i-New-Tab mr-2"></i>
                            <span class="item-name">
                                Tabs
                            </span>
                        </router-link>
                    </li>
                    <li>
                        <router-link tag="a" class to="/components/typography">
                            <i class="nav-icon i-Width-Window mr-2"></i>
                            <span class="item-name">
                                Typoghraphy
                            </span>
                        </router-link>
                    </li>
                    <li>
                        <a href="datatables/basic/table.datatables.html"
                            ><i class="nav-icon i-Clock-3 text-base mr-2"></i
                            ><span class="item-name">Datatable Basic</span></a
                        >
                    </li>
                    <li>
                        <a href="components/components.forms.html"
                            ><i class="nav-icon i-Clock text-base mr-2"></i
                            ><span class="item-name">Forms</span></a
                        >
                    </li>
                    <li>
                        <a href="components/components.modal.html"
                            ><i class="nav-icon i-Clock text-base mr-2"></i
                            ><span class="item-name">Modal</span></a
                        >
                    </li>
                    <li>
                        <a href="components/components.pagination.html"
                            ><i class="nav-icon i-Clock text-base mr-2"></i
                            ><span class="item-name">Pagination</span></a
                        >
                    </li>
                    <li>
                        <a href="components/components.progressbar.html"
                            ><i class="nav-icon i-Clock text-base mr-2"></i
                            ><span class="item-name">Progressbar</span></a
                        >
                    </li>
                </ul>
                <ul
                    class="mb-4 childNav hidden"
                    data-parent="widgets"
                    
                >
                    <li>
                        <a href="widgets/widgets.charts.html"
                            ><i class="nav-icon i-Clock-3 text-base mr-2"></i
                            ><span class="item-name">Charts</span></a
                        >
                    </li>
                    <li>
                        <a href="widgets/widgets.general.html"
                            ><i class="nav-icon i-Clock-3 text-base mr-2"></i
                            ><span class="item-name">General</span></a
                        >
                    </li>
                </ul>
                <ul
                    class="mb-4 childNav"
                    data-parent="profile"
                    :class="selectedParentMenu == 'profile' ? 'block' : 'hidden'"
                >
                    
                    <li>
                        <a href="pages/profile/profile.v1.html"
                            ><i class="nav-icon i-Find-User text-base mr-2"></i
                            ><span class="item-name">Profile Ver 1.0</span></a
                        >
                    </li>
                    <li>
                    
                        <router-link tag="a" class to="/profile/profileTwo">
                            <i class="nav-icon i-Find-User text-base mr-2"></i>
                            <span class="item-name">
                                Profile Ver 2.0
                            </span>
                        </router-link>
                    </li>
                </ul>
                <ul
                    class="mb-4 childNav hidden"
                    data-parent="sessions"
                    
                >
                    <li>
                        <a href="pages/sessions/signin.html"
                            ><i
                                class="nav-icon i-Checked-User text-base mr-2"
                            ></i
                            ><span class="item-name">Sign In</span></a
                        >
                    </li>
                    <li>
                        <a href="pages/sessions/signin2.html"
                            ><i
                                class="nav-icon i-Checked-User text-base mr-2"
                            ></i
                            ><span class="item-name">Sign In 2</span></a
                        >
                    </li>
                    <li>
                        <a href="pages/sessions/signin3.html"
                            ><i
                                class="nav-icon i-Checked-User text-base mr-2"
                            ></i
                            ><span class="item-name">Sign In 3</span></a
                        >
                    </li>
                    <li>
                        <a href="pages/sessions/signin4.html"
                            ><i
                                class="nav-icon i-Checked-User text-base mr-2"
                            ></i
                            ><span class="item-name">Sign In 4</span></a
                        >
                    </li>
                    <li>
                        <a href="pages/sessions/signup.html"
                            ><i
                                class="nav-icon i-Checked-User text-base mr-2"
                            ></i
                            ><span class="item-name">Sign Up 1</span></a
                        >
                    </li>
                    <li>
                        <a href="pages/sessions/signup2.html"
                            ><i
                                class="nav-icon i-Checked-User text-base mr-2"
                            ></i
                            ><span class="item-name">Sign Up 2</span></a
                        >
                    </li>
                    <li>
                        <a href="pages/sessions/signup3.html"
                            ><i
                                class="nav-icon i-Checked-User text-base mr-2"
                            ></i
                            ><span class="item-name">Sign Up 3</span></a
                        >
                    </li>
                    <li>
                        <a href="pages/sessions/signup4.html"
                            ><i
                                class="nav-icon i-Checked-User text-base mr-2"
                            ></i
                            ><span class="item-name">Sign Up 4</span></a
                        >
                    </li>
                    <li>
                        <a href="pages/sessions/404.html"
                            ><i
                                class="nav-icon i-Checked-User text-base mr-2"
                            ></i
                            ><span class="item-name">404</span></a
                        >
                    </li>
                    <li>
                        <a href="pages/sessions/forgot.html"
                            ><i
                                class="nav-icon i-Checked-User text-base mr-2"
                            ></i
                            ><span class="item-name">forgot</span></a
                        >
                    </li>
                </ul>
                <ul
                    class="mb-4 childNav hidden"
                    data-parent="charts"
                    
                >
                    <li>
                        <a href="charts/apexCharts/apexCharts.bar.html"
                            ><i
                                class="nav-icon i-Bar-Chart-2 text-base mr-2"
                            ></i
                            ><span class="item-name">Bar</span></a
                        >
                    </li>
                    <li>
                        <a href="charts/apexCharts/apexCharts.bubble.html"
                            ><i
                                class="nav-icon i-Bar-Chart-2 text-base mr-2"
                            ></i
                            ><span class="item-name">Bubble</span></a
                        >
                    </li>
                    <li>
                        <a href="charts/apexCharts/apexCharts.area.html"
                            ><i
                                class="nav-icon i-Bar-Chart-2 text-base mr-2"
                            ></i
                            ><span class="item-name">Charts</span></a
                        >
                    </li>
                    <li>
                        <a href="charts/apexCharts/apexCharts.candleStick.html"
                            ><i
                                class="nav-icon i-Bar-Chart-2 text-base mr-2"
                            ></i
                            ><span class="item-name">Candle Stick</span></a
                        >
                    </li>
                    <li>
                        <a href="charts/apexCharts/apexCharts.column.html"
                            ><i
                                class="nav-icon i-Bar-Chart-2 text-base mr-2"
                            ></i
                            ><span class="item-name">Column</span></a
                        >
                    </li>
                    <li>
                        <a href="charts/apexCharts/apexCharts.line.html"
                            ><i
                                class="nav-icon i-Bar-Chart-2 text-base mr-2"
                            ></i
                            ><span class="item-name">Line</span></a
                        >
                    </li>
                    <li>
                        <a href="charts/apexCharts/apexCharts.pie.html"
                            ><i
                                class="nav-icon i-Bar-Chart-2 text-base mr-2"
                            ></i
                            ><span class="item-name">Pie</span></a
                        >
                    </li>
                    <li>
                        <a href="charts/apexCharts/apexCharts.radar.html"
                            ><i
                                class="nav-icon i-Bar-Chart-2 text-base mr-2"
                            ></i
                            ><span class="item-name">Radar</span></a
                        >
                    </li>
                    <li>
                        <a href="charts/apexCharts/apexCharts.radialBar.html"
                            ><i
                                class="nav-icon i-Bar-Chart-2 text-base mr-2"
                            ></i
                            ><span class="item-name">RadialBar</span></a
                        >
                    </li>
                    <li>
                        <a href="charts/apexCharts/apexCharts.sparkline.html"
                            ><i
                                class="nav-icon i-Bar-Chart-2 text-base mr-2"
                            ></i
                            ><span class="item-name">Sparkline</span></a
                        >
                    </li>
                    <li>
                        <a href="charts/apexCharts/apexCharts.scatter.html"
                            ><i
                                class="nav-icon i-Bar-Chart-2 text-base mr-2"
                            ></i
                            ><span class="item-name">Scatter</span></a
                        >
                    </li>
                    <li class="dropdown-sidemenu">
                        <a href="#"
                            ><i
                                class="nav-icon i-Bar-Chart-2 text-base mr-2"
                            ></i
                            ><span class="item-name">Scatter</span
                            ><i class="dd-arrow i-Arrow-Down"></i
                        ></a>
                        <ul class="submenu">
                            <li>
                                <a class="hover:text-purple-500" href="#"
                                    >Submneu One</a
                                >
                            </li>
                            <li>
                                <a class="hover:text-purple-500" href="#"
                                    >Submneu Two</a
                                >
                            </li>
                        </ul>
                    </li>
                    <li class="dropdown-sidemenu">
                        <a href="#"><i class="nav-icon i-Bar-Chart-2 text-base mr-2"></i
                            ><span class="item-name">Scatter</span
                            ><i class="dd-arrow i-Arrow-Down"></i
                        ></a>
                        <ul class="submenu">
                            <li>
                                <a class="hover:text-purple-500" href="#">test One</a>
                            </li>
                            <li>
                                <a class="hover:text-purple-500" href="#">test Two</a>
                            </li>
                        </ul>
                    </li>
                </ul>
            </div>
        </div>
        
        <div
            @click="removeOverlay()"
            class="sidebar-overlay"
            :class="{ open: store.state.largeSidebar.sidebarToggleProperties.isSecondarySideNavOpen }"
        ></div>
    </div>
</template>

<style lang="scss" scoped>
.submenuLi {
    &:hover {
        .submenuli-icon {
            color: #8B5CF6;
        }
    }
    .submenuli-icon {
        color: #9CA3AF;
    }
}
.submneu-nested-link {
    padding: 0 !important;
    color: #000 !important;
    &:hover {
        background-color: transparent !important;
        color: #8B5CF6 !important;
    }
}
.side-content-wrap {
    .sidebar-left {
        position: fixed;
        top: 80px;
        left: -120px;
        width: 120px;

        background: #fff;
        box-shadow: 0 4px 20px 1px rgba(0, 0, 0, 0.06),
            0 1px 4px rgba(0, 0, 0, 0.08);
        z-index: 90;
        transition: all 0.24s ease-in-out;
        &.open {
            left: 0;
            transition: all 0.24s ease-in-out;
        }
        .ps {
            height: calc(100vh - 80px);
        }
        .navigation-left {
            list-style: none;
            text-align: center;
            width: 120px;
            height: 100%;
            margin: 0;
            padding: 0;
            .nav-item,
            .nav-item-single {
                position: relative;
                display: block;
                width: 100%;
                overflow: hidden;
                cursor: pointer;
                &:hover {
                    .nav-item-hold {
                        @apply text-purple-500;
                    }
                    &:after {
                        content: '';
                        position: absolute;
                        width: 30px;
                        height: 30px;
                        bottom: -15px;
                        right: -15px;
                        transform: rotate(45deg);
                        @apply bg-purple-500;
                    }
                }

                &.active {
                    @apply text-purple-500;

                    &:after {
                        content: '';
                        position: absolute;
                        width: 30px;
                        height: 30px;
                        bottom: -15px;
                        right: -15px;
                        transform: rotate(45deg);
                        @apply bg-purple-500;
                    }
                }
                border-bottom: 1px solid #dee2e6;
                .nav-item-hold {
                    display: block;
                    width: 100%;
                    padding: 26px 0;
                    span.material-icons {
                        font-size: 2rem;
                    }
                }
            }
        }
    }
    .sidebar-left-secondary {
        position: fixed;
        top: 80px;
        left: calc(-220px - 20px);
        z-index: 89;
        height: calc(100vh - 80px);
        width: 220px;
        padding: 0.75rem 0;
        transition: all 0.24s ease-in-out;
        background: #fff;

        &.open {
            left: 120px;
            transition: all 0.24s ease-in-out;
        }
        ul.childNav {
            li {
                &.dropdown-sidemenu {
                    display: block;
                    transition: all 0.3s ease-in;
                    &.open {
                        a {
                            .dd-arrow {
                                transform: rotate(90deg);
                                transition: all 0.3s ease-in;
                            }
                            
                        }
                        ul.submenu {
                            display: block;
                            max-height: 1000px;
                            transition: all 0.3s ease-in;
                        }
                    }

                    a {
                        .dd-arrow {
                            margin-left: auto !important;
                            transition: all 0.3s ease-in;
                        }
                    }
                }

                // &.active {
                //     a {
                //         background-color: #f3f4f6;
                //         @apply text-purple-500;
                //     }
                // }
                a {
                    text-transform: capitalize;
                    display: flex;
                    align-items: center;
                    font-size: 13px;
                    cursor: pointer;
                    padding: 12px 24px;
                    transition: 0.15s all ease-in;
                    &:hover {
                        background-color: #f3f4f6;
                        @apply text-purple-500;
                    }
                    &.router-link-active.router-link-exact-active {
                        
                        @apply text-purple-500;
                    }
                }
                ul.submenu {
                    @apply bg-gray-50;
                    display: none;
                    max-height: 0px;
                    transition: all 0.3s ease-in;

                    &.open {
                        display: block;
                        transition: all 0.3s ease-in;
                    }
                    li {
                        a {
                            padding-left: 48px;
                        }
                    }
                }
            }
        }
    }
    .sidebar-overlay{
        display: none;
        position: fixed;
        width: calc( 100% - 120px - 220px);
        height: calc(100vh - 80px);
        bottom: 0;
        right: 0;
        background: rgba(0, 0, 0, 0);
        z-index: 101;
        cursor: w-resize;
        &.open {
            display: block;
        }
    }
}
</style>
