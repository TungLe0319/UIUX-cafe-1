
<script setup>
import Button from './Globals/Button.vue';
</script>
<template>
  <div class="w-full min-h-screen flex items-center justify-center bg-black">
          <div class="md:w-2/3 w-full px-4 text-white flex flex-col">
              <div class="w-full text-7xl font-bold">
                  <h1 class="w-full md:w-2/3">How can we help you.</h1>
              </div>
              <div class="flex mt-8 flex-col md:flex-row md:justify-between">
                  <p class="w-full md:w-2/3 text-gray-400">Fostering success through dedicated service. Navigate questions with our committed assistance, ensuring your experience is met with tailored solutions for a enjoyable time. </p>
                  <div class="w-44 pt-6 md:pt-0">
                      <Button class="bg-emerald-500 justify-center text-center rounded-lg shadow px-10 py-3 flex items-center">Contact US</Button>
                  </div>
              </div>
              <div class="flex flex-col">
                  <div class="flex mt-24 mb-12 flex-row justify-between">
                      <div class="">
                          
                      </div>
                      <a class="hidden md:block cursor-pointer text-gray-600 hover:text-white uppercase">About</a>
                      <a class="hidden md:block cursor-pointer text-gray-600 hover:text-white uppercase">Services</a>
                      <a class="hidden md:block cursor-pointer text-gray-600 hover:text-white uppercase">Why us</a>
                      <a class="hidden md:block cursor-pointer text-gray-600 hover:text-white uppercase">Contact</a>
                      <div class="flex flex-row space-x-8 items-center justify-between">
                       
                         <a href="/">
                              <Icon name="uil:facebook" class="text-4xl"  />                           
                            </a>
                         <a href="/">
                              <Icon name="uil:instagram" class="text-4xl"  />                           
                            </a>
                          <a href="/">
                            <Icon name="uil:youtube" class="text-4xl"  />                           
                          </a>
                      </div>
                  </div>
                  <hr class="border-emerald-600"/>
                  <p class="w-full text-center my-12 text-gray-600">Copyright © 2023 Lorem Co.</p>
              </div>
          </div>
      </div>
</template>


<style lang="css" scoped>
a{
  @apply hover:-translate-y-1 transition-all duration-200
}
</style>