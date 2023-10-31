<script setup lang="ts">
import { Disclosure, DisclosureButton, DisclosurePanel } from '@headlessui/vue'
import { Bars3Icon, XMarkIcon } from '@heroicons/vue/24/solid'

const path = () => {
  console.log(useRoute().path)
  return useRoute().path
}

const navigation = [
  { name: 'Home', path: '/' },
  { name: 'People', path: '/people' },
  { name: 'Planets', path: '/planets' },
  { name: 'Species', path: '/species' },
  { name: 'Starships', path: '/starships' },
  { name: 'Vehicles', path: '/vehicles' },
]
</script>

<template>
  <div>
    <Disclosure
      as="nav"
      class="bg-gray-800"
      v-slot="{ open }"
    >
      <div class="mx-auto max-w-7xl px-2 sm:px-6 lg:px-8">
        <div class="relative flex h-16 items-center justify-between">
          <div class=" inset-y-0 left-0 flex items-center sm:hidden absolute">
            <DisclosureButton
              class="relative inline-flex items-center justify-center rounded-md p-2 text-gray-400 hover:bg-gray-700 hover:text-white focus:outline-none focus:ring-2 focus:ring-inset focus:ring-white"
            >
              <span class="absolute -inset-0.5" />
              <span class="sr-only">Open main menu</span>
              <Bars3Icon
                v-if="!open"
                class="block h-6 w-6"
                aria-hidden="true"
              />
              <XMarkIcon
                v-else
                class="block h-6 w-6"
                aria-hidden="true"
              />
            </DisclosureButton>
          </div>
          <div class="flex flex-1 items-center sm:justify-between justify-center">
            <div class="flex flex-shrink-1 items-center text-center h-2 text-white font-black text-2xl">
              <NuxtLink to="/">
                STAR WARS
              </NuxtLink>
            </div>
            <div class="hidden sm:ml-6 sm:block">
              <div class="flex space-x-4">
                <NuxtLink
                  v-for="item in navigation"
                  :key="item.name"
                  :to="item.path"
                  :class="{ active: path() === item.path }"
                  class="text-gray-300 hover:bg-gray-700 hover:text-white rounded-md px-3 py-2 text-sm font-medium"
                >
                  {{ item.name }}
                </NuxtLink>
              </div>
            </div>
          </div>
        </div>
      </div>

      <DisclosurePanel class="sm:hidden">
        <div class="space-y-1 px-2 pb-3 pt-2 flex flex-col">
          <DisclosureButton
            v-for="item in navigation"
            :key="item.name"
          >
            <NuxtLink
              :to="item.path"
              :class="{ active: path() === item.path }"
              class="text-gray-300 hover:bg-gray-700 hover:text-white rounded-md px-3 py-2 leading-8 font-medium"
            >
              {{ item.name }}
            </NuxtLink>
          </DisclosureButton>
        </div>
      </DisclosurePanel>
    </Disclosure>
    <slot />
  </div>
</template> 

<style>
.active {
  --tw-bg-opacity: 1;
  background-color: rgb(17 24 39 / var(--tw-bg-opacity));
  --tw-text-opacity: 1;
  color: rgb(255 255 255 / var(--tw-text-opacity))
}
</style>


