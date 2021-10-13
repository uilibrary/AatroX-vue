<script setup>
    import Breadcrumb from '@/components/Breadcrumbs.vue'
    import { ref } from 'vue'
    import { TabGroup, TabList, Tab, TabPanels, TabPanel } from '@headlessui/vue'
    let categories = ref(['Timeline', 'About', 'Friends', 'Photos'])
</script>

<template>
 
  <div class="container mx-auto">
    <Breadcrumb parentTitle='Profile' subParentTitle='ProfileV2' />
   

    
    <BaseCard noPadding class="user-profile overflow-hidden relative">
        <div class="header-cover"></div>
        <div class="flex justify-center z-10 -m-10">
            <div class="text-center"><img class="relative z-1 w-20 h-20 m-auto rounded-full border-2 border-white" src="/images/faces/1.jpg" />
                <p class="text-2xl">Timothy Carlson</p>
                <p class="text-gray-600">Digital Marketer</p>
            </div>
        </div>
        <div class="mt-20 p-5">
         
          <TabGroup>
            <TabList class="flex bg-white justify-center">
              <Tab
                v-for="category in categories"
                as="template"
                :key="category"
                v-slot="{ selected }"
              >
                <button
                  class="font-semibold border-b-2 border-white"
                  :class="[
                    'px-3 py-1 text-sm leading-5 ',
                    'focus:outline-none',
                    selected
                      ? 'text-primary border-b-2 border-primary'
                      : 'text-gray-600',
                  ]"
                >
                  {{ category }}
                </button>
              </Tab>
            </TabList>

            <TabPanels class="mt-10">
              <TabPanel>
                <ul class="timeline clearfix">
                    <li class="timeline-line"></li>
                    <li class="timeline-item">
                        <div class="timeline-badge">
                            <div class="rounded-full flex items-center justify-center bg-purple-500 text-purple-100 font-bold h-10 w-10 mr-2">
                                <i class="i-Cloud-Picture"></i>
                            </div>
                        </div>
                        <BaseCard class="timeline-card">
                              <div class="mb-1">
                                  <strong class="mr-1">Timothy Carlson</strong> added a new photo
                                  <p class="text-muted">3 hours ago</p>
                              </div>
                              <img class="rounded mb-2" src="/images/photo-wide-1.jpg" alt="">
                              <div class="mb-3">
                                  <a href="#" class="mr-2 hover:text-purple-500">Like</a>
                                  <a href="#" class="hover:text-purple-500">Comment</a>
                              </div>
                              <div class="input-group flex flex-wrap">
                                  <input type="text" class="focus:outline-none w-full border border-gray px-3 py-2 rounded" placeholder="Write Comment" />
                              </div>
                        </BaseCard>
                        
                    </li>
                    <li class="timeline-item">
                        <div class="timeline-badge">
                            <img class="badge-img rounded-full" src="/images/faces/1.jpg" alt="">
                        </div>
                        <BaseCard class="timeline-card">
                          <div class="mb-1">
                              <strong class="mr-1">Timothy Carlson</strong> updated his sattus
                              <p class="text-muted">16 hours ago</p>
                          </div>
                          <p class="my-4">Lorem ipsum dolor sit amet consectetur adipisicing elit. Modi dicta beatae illo illum iusto iste mollitia explicabo quam officia. Quas ullam, quisquam architecto aspernatur enim iure debitis dignissimos suscipit ipsa.
                          </p>
                          <div class="mb-3">
                              <a href="#" class="mr-2 hover:text-purple-500">Like</a>
                              <a href="#" class="hover:text-purple-500">Comment</a>
                          </div>
                          <div class="input-group flex flex-wrap">
                              <input type="text" class="focus:outline-none w-full border border-gray px-3 py-2 rounded" placeholder="Write Comment" />
                          </div>
                        </BaseCard>
                       
                    </li>
                </ul>
                <ul class="timeline clearfix">
                    <li class="timeline-line"></li>
                    <li class="timeline-group text-center">
                        
                        <BaseBtn class="bg-primary text-white">
                          <i class="i-Calendar-4"></i> 2021
                        </BaseBtn>
                    </li>
                </ul>
                <ul class="timeline clearfix">
                    <li class="timeline-line"></li>
                    <li class="timeline-item">
                        <div class="timeline-badge">
                            <div class="rounded-full flex items-center justify-center bg-red-500 text-red-100 font-bold h-10 w-10 mr-2">
                                <i class="i-Love-User"></i>
                            </div>
                        </div>
                        <BaseCard class="timeline-card">
                            <div class="mb-1">
                                <strong class="mr-1">New followers</strong>
                                <p class="text-muted">2 days ago</p>
                            </div>
                            <p class="my-4"><a href="#" class="hover:text-purple-500">Henry krick</a> and 16 others followed you</p>
                            <div class="mb-3">
                                <a href="#" class="mr-1 hover:text-purple-500">Like</a>
                                <a href="#" class="hover:text-purple-500">Comment</a>
                            </div>        
                            <input type="text" class="focus:outline-none w-full border border-gray px-3 py-2 rounded" placeholder="Write Comment" />
                        </BaseCard>
                      
                    </li>
                    <li class="timeline-item">
                        <div class="timeline-badge">
                            <div class="rounded-full flex items-center justify-center bg-purple-500 text-purple-100 font-bold h-10 w-10 mr-2">
                                <i class="i-Cloud-Picture"></i>
                            </div>
                        </div>
                        <BaseCard class="timeline-card">
                            <div div class="mb-1">
                                <strong class="mr-1">Timothy Carlson</strong> added a new photo
                                <p class="text-muted">2 days ago</p>
                            </div>
                            <img class="rounded mb-2" src="/images/photo-wide-2.jpg" alt="">
                            <div class="mb-3">
                                <a href="#" class="mr-1 hover:text-purple-500">Like</a>
                                <a href="#" class="hover:text-purple-500">Comment</a>
                            </div>
                            
                            <input type="text" class="focus:outline-none w-full border border-gray px-3 py-2 rounded" placeholder="Write Comment" />
                        </BaseCard>
                        
                    </li>
                </ul>
                <ul class="timeline clearfix">
                    <li class="timeline-line"></li>
                    <li class="timeline-group text-center">
                        <BaseBtn class="bg-yellow text-white">
                          <i class="i-Calendar-4"></i> Joined in 2013
                        </BaseBtn>
                    </li>
                </ul>
              </TabPanel>
              <TabPanel>
                <div class="p-5">
                  <p class="text-xl font-semibold mb-2">Personal Information</p>
                  <p class="border-b border-gray-300 pb-10 mb-8">Lorem ipsum dolor sit amet consectetur adipisicing elit. Eveniet, commodi quam! Provident quis voluptate asperiores ullam, quidem odio pariatur. Lorem ipsum, dolor sit amet consectetur adipisicing elit. Voluptatem, nulla eos? Cum non ex voluptate corporis id asperiores doloribus dignissimos blanditiis iusto qui repellendus deleniti aliquam, vel quae eligendi explicabo.</p>
                  <div class="grid grid-cols-12 gap-5 border-b border-gray-300 pb-10 mb-10">
                      <div class="col-span-12 sm:col-span-6 md:col-span-4">
                          <p class="text-purple-500 mb-1"><i class="i-Calendar text-base"></i><span class="ml-1">Birth Date</span></p><span>1, Jan 1994</span>
                      </div>
                      <div class="col-span-12 sm:col-span-6 md:col-span-4">
                          <p class="text-purple-500 mb-1"><i class="i-MaleFemale text-base"></i><span class="ml-1">Gender</span></p><span>1, Jan 1994</span>
                      </div>
                      <div class="col-span-12 sm:col-span-6 md:col-span-4">
                          <p class="text-purple-500 mb-1"><i class="i-Face-Style-4 text-base"></i><span class="ml-1">Profession</span></p><span>Digital Marketer</span>
                      </div>
                      <div class="col-span-12 sm:col-span-6 md:col-span-4">
                          <p class="text-purple-500 mb-1"><i class="i-Calendar text-base"></i><span class="ml-1">Birth Date</span></p><span>1, Jan 1994</span>
                      </div>
                      <div class="col-span-12 sm:col-span-6 md:col-span-4">
                          <p class="text-purple-500 mb-1"><i class="i-MaleFemale text-base"></i><span class="ml-1">Gender</span></p><span>1, Jan 1994</span>
                      </div>
                      <div class="col-span-12 sm:col-span-6 md:col-span-4">
                          <p class="text-purple-500 mb-1"><i class="i-Face-Style-4 text-base"></i><span class="ml-1">Profession</span></p><span>Digital Marketer</span>
                      </div>
                      <div class="col-span-12 sm:col-span-6 md:col-span-4">
                          <p class="text-purple-500 mb-1"><i class="i-Globe text-base"></i><span class="ml-1"> Lives In </span></p><span>8 Years</span>
                      </div>
                      <div class="col-span-12 sm:col-span-6 md:col-span-4">
                          <p class="text-purple-500 mb-1"><i class="i-Edit-Map text-base"></i><span class="ml-1">Email</span></p><span>example@ui-lib.com</span>
                      </div>
                      <div class="col-span-12 sm:col-span-6 md:col-span-4">
                          <p class="text-purple-500 mb-1"><i class="i-Professor text-base"></i><span class="ml-1"> Experience</span></p><span>8 Years</span>
                      </div>
                  </div>
                  <div class="my-5">
                      <p class="text-2xl">Timothy Carlson</p>
                      <p class="text-gray-600">Digital Marketer</p>
                  </div>
                  <div class="flex justify-around flex-wrap">
                      <div class="text-center mx-4 my-2"><i class="i-Plane text-4xl text-purple-500"></i>
                          <p class="text-base">Travelling </p>
                      </div>
                      <div class="text-center mx-4 my-2"><i class="i-Camera text-4xl text-purple-500"></i>
                          <p class="text-base">Photography </p>
                      </div>
                      <div class="text-center mx-4 my-2"><i class="i-Car-3 text-4xl text-purple-500"></i>
                          <p class="text-base">Driving </p>
                      </div>
                      <div class="text-center mx-4 my-2"><i class="i-Gamepad-2 text-4xl text-purple-500"></i>
                          <p class="text-base">Gaming </p>
                      </div>
                      <div class="text-center mx-4 my-2"><i class="i-Music-Note-2 text-4xl text-purple-500"></i>
                          <p class="text-base">Music </p>
                      </div>
                      <div class="text-center mx-4 my-2"><i class="i-Shopping-Bag text-4xl text-purple-500"></i>
                          <p class="text-base">Shopping </p>
                      </div>
                  </div>
                </div>
              </TabPanel>
              <TabPanel>
               <div class="grid grid-cols-12 gap-5">
                    <div class="col-span-12 xl:col-span-3 lg:col-span-4 md:col-span-6">
                        <BaseCard class="text-center">
                          <img class="w-20 h-20 m-auto rounded-full shadow-lg mb-3" src="/images/faces/16.jpg" alt="" srcset="" />
                                <h5 class="text-lg">Jassica Hike</h5>
                                <p>UI/UX Designer</p>
                                <p class="my-5">Lorem ipsum dolor sit amet consectetur adipisicing elit. Recusandae cumque.</p>
                                
                                <BaseBtn rounded class="bg-purple-500 text-white">Contact Jassica</BaseBtn>
                                <div class="card-socials-simple mt-4">
                                  <a class="mr-2 hover:text-purple-500" href="#">
                                    <i class="i-Linkedin-2"></i>
                                  </a>
                                  <a class="mr-2 hover:text-purple-500" href="#">
                                    <i class="i-Facebook-2"></i>
                                  </a>
                                  <a class="mr-2 hover:text-purple-500" href="#">
                                    <i class="i-Twitter"></i>
                                  </a>
                                </div>
                        </BaseCard>
                       
                    </div>
                    <div class="col-span-12 xl:col-span-3 lg:col-span-4 md:col-span-6">
                        <BaseCard class="text-center">
                           <div class="card-body text-center">
                                <img class="w-20 h-20 m-auto rounded-full shadow-lg mb-3" src="/images/faces/2.jpg" alt="" srcset="" />
                                <h5 class="text-lg">Frank Powell</h5>
                                <p>UI/UX Designer</p>
                                <p class="my-5">Lorem ipsum dolor sit amet consectetur adipisicing elit. Recusandae cumque.</p>
                                <BaseBtn rounded class="bg-purple-500 text-white">Contact Frank</BaseBtn>
                                <div class="card-socials-simple mt-4">
                                  <a class="mr-2 hover:text-purple-500" href="#">
                                    <i class="i-Linkedin-2"></i>
                                  </a>
                                  <a class="mr-2 hover:text-purple-500" href="#">
                                    <i class="i-Facebook-2"></i>
                                  </a>
                                  <a class="mr-2 hover:text-purple-500" href="#">
                                    <i class="i-Twitter"></i>
                                  </a>
                                </div>
                            </div>
                        </BaseCard>
                    </div>
                    <div class="col-span-12 xl:col-span-3 lg:col-span-4 md:col-span-6">
                        <BaseCard class="text-center">
                           <div class="card-body text-center">
                                <img class="w-20 h-20 m-auto rounded-full shadow-lg mb-3" src="/images/faces/3.jpg" alt="" srcset="" />
                                <h5 class="text-lg">Arthur Mendoza</h5>
                                <p>UI/UX Designer</p>
                                <p class="my-5">Lorem ipsum dolor sit amet consectetur adipisicing elit. Recusandae cumque.</p>
                                <BaseBtn rounded class="bg-purple-500 text-white">Contact Arthur</BaseBtn>
                                <div class="card-socials-simple mt-4">
                                  <a class="mr-2 hover:text-purple-500" href="#">
                                    <i class="i-Linkedin-2"></i>
                                  </a>
                                  <a class="mr-2 hover:text-purple-500" href="#">
                                    <i class="i-Facebook-2"></i>
                                  </a>
                                  <a class="mr-2 hover:text-purple-500" href="#">
                                    <i class="i-Twitter"></i>
                                  </a>
                                </div>
                            </div>
                        </BaseCard>
                       
                    </div>
                    <div class="col-span-12 xl:col-span-3 lg:col-span-4 md:col-span-6">
                      <BaseCard class="text-center">
                           <div class="card-body text-center">
                                <img class="w-20 h-20 m-auto rounded-full shadow-lg mb-3" src="/images/faces/4.jpg" alt="" srcset="" />
                                <h5 class="text-lg">Jacqueline Day </h5>
                                <p>UI/UX Designer</p>
                                <p class="my-5">Lorem ipsum dolor sit amet consectetur adipisicing elit. Recusandae cumque.</p>
                                <BaseBtn rounded class="bg-purple-500 text-white">Contact Jacqueline </BaseBtn>
                                <div class="card-socials-simple mt-4">
                                  <a class="mr-2 hover:text-purple-500" href="#">
                                    <i class="i-Linkedin-2"></i>
                                  </a>
                                  <a class="mr-2 hover:text-purple-500" href="#">
                                    <i class="i-Facebook-2"></i>
                                  </a>
                                  <a class="mr-2 hover:text-purple-500" href="#">
                                    <i class="i-Twitter"></i>
                                  </a>
                                </div>
                            </div>
                        </BaseCard>
                       
                        
                    </div>
                </div>
              </TabPanel>
              <TabPanel>
                <div class="grid grid-cols-12 gap-5">
                    <div  class="col-span-12 lg:col-span-4 md:col-span-6">
                        <BaseCard noPadding class="relative overflow-hidden">
                          <img class="w-full" src="/images/products/headphone-1.jpg" alt="" />
                          <div class="card-img-overlay-profile absolute bottom-0 p-4">
                              <div class="p-1 text-left font-light flex"><span class="mr-3 flex items-center text-white"><i class="i-Speach-Bubble-6 mr-1"></i>12</span><span class="flex items-center text-white"><i class="i-Calendar-4 mr-2"></i>03.12.2018</span></div>
                          </div>
                        </BaseCard>
                        
                    </div>
                    <div class="col-span-12 lg:col-span-4 md:col-span-6">
                        <BaseCard noPadding class="relative overflow-hidden">
                          <img class="w-full" src="/images/products/headphone-2.jpg" alt="" />
                          <div class="card-img-overlay-profile absolute bottom-0 p-4">
                              <div class="p-1 text-left font-light flex"><span class="mr-3 flex items-center text-white"><i class="i-Speach-Bubble-6 mr-1"></i>12</span><span class="flex items-center text-white"><i class="i-Calendar-4 mr-2"></i>03.12.2018</span></div>
                          </div>
                        </BaseCard>
                        
                    </div>
                    <div class="col-span-12 lg:col-span-4 md:col-span-6">
                        <BaseCard noPadding class="relative overflow-hidden">
                          <img class="w-full" src="/images/products/headphone-3.jpg" alt="" />
                          <div class="card-img-overlay-profile absolute bottom-0 p-4">
                              <div class="p-1 text-left font-light flex"><span class="mr-3 flex items-center text-white"><i class="i-Speach-Bubble-6 mr-1"></i>12</span><span class="flex items-center text-white"><i class="i-Calendar-4 mr-2"></i>03.12.2018</span></div>
                          </div>
                        </BaseCard>
                    </div>
                    <div class="col-span-12 lg:col-span-4 md:col-span-6">
                        <BaseCard noPadding class="relative overflow-hidden">
                          <img class="w-full" src="/images/products/iphone-1.jpg" alt="" />
                          <div class="card-img-overlay-profile absolute bottom-0 p-4">
                              <div class="p-1 text-left font-light flex"><span class="mr-3 flex items-center text-white"><i class="i-Speach-Bubble-6 mr-1"></i>12</span><span class="flex items-center text-white"><i class="i-Calendar-4 mr-2"></i>03.12.2018</span></div>
                          </div>
                        </BaseCard>
                       
                    </div>
                    <div class="col-span-12 lg:col-span-4 md:col-span-6">
                        <BaseCard noPadding class="relative overflow-hidden">
                          <img class="w-full" src="/images/products/iphone-2.jpg" alt="" />
                          <div class="card-img-overlay-profile absolute bottom-0 p-4">
                              <div class="p-1 text-left font-light flex"><span class="mr-3 flex items-center text-white"><i class="i-Speach-Bubble-6 mr-1"></i>12</span><span class="flex items-center text-white"><i class="i-Calendar-4 mr-2"></i>03.12.2018</span></div>
                          </div>
                        </BaseCard>
                    </div>
                    <div class="col-span-12 lg:col-span-4 md:col-span-6">
                        <BaseCard noPadding class="relative overflow-hidden">
                          <img class="w-full" src="/images/products/watch-1.jpg" alt="" />
                          <div class="card-img-overlay-profile absolute bottom-0 p-4">
                              <div class="p-1 text-left font-light flex"><span class="mr-3 flex items-center text-white"><i class="i-Speach-Bubble-6 mr-1"></i>12</span><span class="flex items-center text-white"><i class="i-Calendar-4 mr-2"></i>03.12.2018</span></div>
                          </div>
                        </BaseCard>
                        
                    </div>
                </div>
              </TabPanel>
            </TabPanels>
          </TabGroup>
        </div>
        
    </BaseCard>
</div>
</template>
<style lang="scss" scoped>
.user-profile {
 .header-cover {
   background-image: url("../../../images/photo-wide-5.jpeg") ;
   position: relative;
   background-size: cover;
   background-repeat: no-repeat;
   height: 300px;
 }
  &::after {
    content: "";
    width: 100%;
    height: 300px;
    position: absolute;
    background: rgba(0,0,0,.1)
  }
}



.timeline {
  position: relative;
  list-style: none;
  padding: 0;
  margin: 0;
  
  li.timeline-item {
      position: relative;
      width: 50%;
      display: inline-block;
      
      &:nth-child(even) {
          padding: 0 3rem 3rem 0;
          .timeline-badge {
              left: calc(100% - 24px);
          }
      }
      &:nth-child(odd) {
          float: right;
          padding: 0 0 3rem 3rem;
          margin-top: 6rem;
          .timeline-badge {
              right: calc(100% - 24px);
          }
      }
      .timeline-badge {
          position: absolute;
          width: 48px;
          height: 48px;
      }
      .badge-icon {
          display: inline-block;
          text-align: center;
          font-size: 22px;
          border-radius: 50%;
          height: 100%;
          width: 100%;
          line-height: 48px;
      }
      .badge-img {
          display: inline-block;
          border-radius: 50%;
          height: 100%;
          width: 100%;
      }
  }
  li.timeline-group {
      position: relative;
      z-index: 99;
      padding: 0 0 2rem 0;
  }
  .timeline-line {
      position: absolute;
      content: "";
      width: 1px;
      height: 100%;
      background: #D1D5DB;
      left: 0;
      right: 0;
      margin: auto;
  }
}
@media (max-width: 767px) {
  .user-profile {
      .header-cover {
          height: 200px;
      }
  }
  
  .timeline {
      .timeline-line {
        display: none !important;
      }
      li.timeline-item {
          width: 100%;
          padding: 4rem 0 3rem !important;
          &:nth-child(odd) {
              margin-top: 1rem;
          }
          .timeline-badge {
              left: 0 !important;
              right: 0 !important;
              top: -16px;
              margin: auto;
          }
      }
      
      li.timeline-group {
          padding: 0 0 3rem;
      }
  }
}



</style>
