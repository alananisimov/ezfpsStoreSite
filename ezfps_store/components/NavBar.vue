<template>
  <div class=" isolate relative inset-x-0 z-[60]">
    <header class="">
    <nav class="mx-auto flex z-50 max-w-7xl items-center justify-between p-6 lg:px-8" aria-label="Global">
      <div class="flex lg:flex-1 relative">
        <a class="-m-1.5 p-1.5">
          <span class="sr-only">ezfps project</span>
          <NuxtLink to="/"><NuxtImg class="h-8 w-auto" format="webp" height="96" width="96" src="/favicon_small.jpg" alt="ezfps logo"/></NuxtLink>
        </a>
      </div>
      <div class="flex lg:hidden">
        <button v-if="mobileMenuOpen == false" type="button" class="-m-2.5 inline-flex items-center justify-center rounded-md p-2.5 text-gray-700" @click="mobileMenuOpen = true">
          <span class="sr-only">Open main menu</span>
          <Bars3Icon class="h-6 w-6" aria-hidden="true" />
        </button>
      </div>
      <PopoverGroup class="hidden lg:flex lg:gap-x-12 ">
        <Popover class="relative">
          <PopoverButton class="flex items-center gap-x-1 text-sm font-semibold leading-6 text-gray-900">
            Наши продукты
            <ChevronDownIcon class="h-5 w-5 flex-none text-gray-400" aria-hidden="true" />
          </PopoverButton>

          <transition enter-active-class="transition ease-out duration-200" enter-from-class="opacity-0 translate-y-1" enter-to-class="opacity-100 translate-y-0" leave-active-class="transition ease-in duration-150" leave-from-class="opacity-100 translate-y-0" leave-to-class="opacity-0 translate-y-1">
            <PopoverPanel class="absolute -left-8 top-full z-10 mt-3 w-screen max-w-md overflow-hidden rounded-3xl bg-white shadow-lg ring-1 ring-gray-900/5">
              <div class="p-4">
                <div v-for="item in products" :key="item.name" class="group relative flex items-center gap-x-6 rounded-lg p-4 text-sm leading-6 hover:bg-gray-50">
                  <div class="flex h-11 w-11 flex-none items-center justify-center rounded-lg bg-gray-50 group-hover:bg-white">
                    <component :is="item.icon" class="h-6 w-6 text-gray-600 group-hover:text-indigo-600" aria-hidden="true" />
                  </div>
                  <div class="flex-auto">
                    <a @click="navigateTo(item.href, {external: item.external})" class="block font-semibold text-gray-900">
                      {{ item.name }}
                      <span class="absolute inset-0" />
                    </a>
                    <p class="mt-1 text-gray-600">{{ item.description }}</p>
                  </div>
                </div>
              </div>
              <div class="grid grid-cols-2 divide-x divide-gray-900/5 bg-gray-50">
                <a v-for="item in callsToAction" :key="item.name" @click="navigateTo(item.href, {external: item.external})" class="flex items-center justify-center gap-x-2.5 p-3 text-sm font-semibold leading-6 text-gray-900 hover:bg-gray-100">
                  <component :is="item.icon" class="h-5 w-5 flex-none text-gray-400" aria-hidden="true" />
                  {{ item.name }}
                </a>
              </div>
            </PopoverPanel>
          </transition>
        </Popover>

        <NuxtLink to="/subscribtion"><a class="text-sm font-semibold leading-6 text-gray-900">Купить подписку</a></NuxtLink>
        <NuxtLink to="/about"><a class="text-sm font-semibold leading-6 text-gray-900 cursor-pointer">О нас</a></NuxtLink>
        <NuxtLink><a href="https://docs.ezfps.store"><a class="text-sm font-semibold leading-6 text-gray-900">Документация</a></a></NuxtLink>
      </PopoverGroup>
      <div class="hidden lg:flex lg:flex-1 lg:justify-end gap-x-3">
        <NuxtLink to="/profile"><span v-if="user" class=" text-gray-700 text-sm font-medium mr-2 px-2.5 py-0.5 rounded border border-gray-500 mx-5 cursor-pointer">Аккаунт</span></NuxtLink>
        <NuxtLink to="/signin"><a v-if="user == null" class="text-sm font-semibold leading-6 text-gray-900 cursor-pointer">Войти <span aria-hidden="true">&rarr;</span></a></NuxtLink>
        <a @click="log_out" v-if="user" class="text-sm font-semibold leading-6 text-gray-900 cursor-pointer">Выйти <span aria-hidden="true">&rarr;</span></a>
      </div>
    </nav>
    <Dialog as="div" class="lg:hidden" @close="mobileMenuOpen = false" :open="mobileMenuOpen">
      <div class="fixed inset-0 z-10"></div>
      <DialogPanel class="fixed inset-y-0 right-0 z-50 w-full overflow-y-auto bg-white px-6 py-6 sm:max-w-sm sm:ring-1 sm:ring-gray-900/10">
        <div class="flex items-center justify-between">
          <a href="#" class="-m-1.5 p-1.5">
            <span class="sr-only">ezfps</span>
            <NuxtLink to="/"><NuxtImg class="h-8 w-auto" format="webp" src="/favicon_small.jpg" height="96" width="96" alt="ezfps logo" /></NuxtLink>
          </a>
          <button type="button" class="-m-2.5 rounded-md p-2.5 text-gray-700" @click="mobileMenuOpen = false">
            <span class="sr-only">Close menu</span>
            <XMarkIcon class="h-6 w-6" aria-hidden="true" />
          </button>
        </div>
        <div class="mt-6 flow-root">
          <div class="-my-6 divide-y divide-gray-500/10">
            <div class="space-y-2 py-6">
              <Disclosure as="div" class="-mx-3" v-slot="{ open }">
                <DisclosureButton class="flex w-full items-center justify-between rounded-lg py-2 pl-3 pr-3.5 text-base font-semibold leading-7 text-gray-900 hover:bg-gray-50">
                  Наши продукты
                  <ChevronDownIcon :class="[open ? 'rotate-180' : '', 'h-5 w-5 flex-none']" aria-hidden="true" />
                </DisclosureButton>
                
                <DisclosurePanel class="mt-2 space-y-2">
                  <NuxtLink v-for="item in [...products, ...callsToAction]" :to="item.href"> <DisclosureButton @click="closeMenu()" :key="item.name" as="a" class="block rounded-lg py-2 pl-6 pr-3 text-sm font-semibold leading-7 text-gray-900 hover:bg-gray-50">{{ item.name }}</DisclosureButton></NuxtLink>
                </DisclosurePanel>
              </Disclosure>
              <NuxtLink to="/subscribtion"><a class="-mx-3 block rounded-lg px-3 py-2 text-base font-semibold leading-7 text-gray-900 hover:bg-gray-50" @click="closeMenu()">Купить подписку</a></NuxtLink>
              <NuxtLink to="/about"><a class="-mx-3 block rounded-lg px-3 py-2 text-base font-semibold leading-7 text-gray-900 hover:bg-gray-50" @click="closeMenu()">О нас</a></NuxtLink>
              <NuxtLink><a href="https://docs.ezfps.store"><a class="-mx-3 block rounded-lg px-3 py-2 text-base font-semibold leading-7 text-gray-900 hover:bg-gray-50" @click="closeMenu()">Документация</a></a></NuxtLink>
            </div>
            <div class="py-6">
              <NuxtLink href="/profile"><a @click="closeMenu()" v-if="user" class="-mx-3 block rounded-lg px-3 py-2.5 text-base font-semibold leading-7 text-gray-900 hover:bg-gray-50">Аккаунт</a></NuxtLink>
              <NuxtLink to="/signin"> <a v-if="user == null" class="-mx-3 block rounded-lg px-3 py-2.5 text-base font-semibold leading-7 text-gray-900 hover:bg-gray-50" @click="closeMenu()">Войти</a></NuxtLink>
              <a @click="log_out() && closeMenu()" v-if="user" class="-mx-3 block rounded-lg px-3 py-2.5 text-base font-semibold leading-7 text-gray-900 hover:bg-gray-50">Выйти</a>
            </div>
          </div>
        </div>
      </DialogPanel>
    </Dialog>
  </header>

      
        
      
     
        
    </div>

</template>

<script setup>
import { ref } from 'vue'
import {
  Dialog,
  DialogPanel,
  Disclosure,
  DisclosureButton,
  DisclosurePanel,
  Popover,
  PopoverButton,
  PopoverGroup,
  PopoverPanel,
} from '@headlessui/vue'
import {
  Bars3Icon,
  XMarkIcon,
  ComputerDesktopIcon,
  ShoppingBagIcon,
  DevicePhoneMobileIcon
} from '@heroicons/vue/24/outline'

import { ChevronDownIcon } from '@heroicons/vue/20/solid'

const supabase = useSupabaseClient()
const { data: { user } } = await supabase.auth.getUser()
async function log_out(){
  const { error } = await supabase.auth.signOut()
  if (error) throw error
  navigateTo("/")
}
const closeMenu = () => {
  mobileMenuOpen.value = false
}
supabase.auth.onAuthStateChange((event, session) => {
  console.log(event, session)
})

const products = [
  { name: 'ezfps app', description: 'Современный оптимизатор ПК', href: '/download', icon: ComputerDesktopIcon, external: false },
  { name: 'telegram bot', description: 'Купить доступ к нашему оптимизатору', href: 'https://t.me/ezfps_bot', icon: ShoppingBagIcon, external: true },
  { name: 'mobile optimizer: скоро', description: 'Оптимизируй свой телефон без проблем', href: '#', icon: DevicePhoneMobileIcon, external: false }
]

const callsToAction = [
  
]

const mobileMenuOpen = ref(false)
</script>
<style>
.page-enter-active,
.page-leave-active {
  transition: all 0.4s;
}
.page-enter-from,
.page-leave-to {
  opacity: 0;
  filter: blur(1rem);
}
</style>