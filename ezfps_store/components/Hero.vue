<template>
  <div class="relative isolate">
    <div class="absolute inset-x-0 -top-40 -z-10 transform-gpu overflow-hidden blur-3xl sm:-top-80" aria-hidden="true">
        <div class="relative left-[calc(50%-11rem)] aspect-[1155/678] w-[36.125rem] -translate-x-1/2 rotate-[30deg] bg-gradient-to-tr from-[#ff80b5] to-[#fca889] opacity-30 sm:left-[calc(50%-30rem)] sm:w-[72.1875rem]" style="clip-path: polygon(74.1% 44.1%, 100% 61.6%, 97.5% 26.9%, 85.5% 0.1%, 80.7% 2%, 72.5% 32.5%, 60.2% 62.4%, 52.4% 68.1%, 47.5% 58.3%, 45.2% 34.5%, 27.5% 76.7%, 0.1% 64.9%, 17.9% 100%, 27.6% 76.8%, 76.1% 97.7%, 74.1% 44.1%)" />
      </div>
  <div class="overflow-hidden bg-transparent  sm:mt-10 pb-16 sm:pt-0 sm:py-0 sm:pb-16 text-center my-16 mt-auto">
    <div class="mx-auto max-w-7xl px-6 ">
      <div class="mx-auto grid max-w-2xl grid-cols-1 gap-x-8 gap-y-16 sm:gap-y-20">
        <div class="">
          <div class=" my-16 sm:my-24 max-[400px]:my-auto">
            <NuxtLink href="https://docs.ezfps.store/guide"><a
                class="hidden sm:inline-flex justify-between items-center py-1 px-1 pr-4 sm:mb-7 text-sm text-gray-700 sm:ring-1 sm:ring-gray-900/10 rounded-full"
                role="alert">
                <span
                  class="text-xs bg-gradient-to-r to-red-600 from-orange-400 rounded-full text-white px-4 py-1.5 mr-3 ">Новинка</span>
                <span class="text-sm font-medium inline-flex">ezfps вышел. <span class="hidden sm:flex ml-1">Зацени
                    сейчас!</span></span>
                <svg class="ml-2 w-5 h-5" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg">
                  <path fill-rule="evenodd"
                    d="M7.293 14.707a1 1 0 010-1.414L10.586 10 7.293 6.707a1 1 0 011.414-1.414l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414 0z"
                    clip-rule="evenodd"></path>
                </svg>
              </a></NuxtLink>
            <h1 class="mb-4 text-5xl font-extrabold tracking-tight leading-none text-gray-900 md:text-5xl lg:text-6xl">
              Интуитивно понятный <span
                class="text-transparent bg-clip-text bg-gradient-to-r to-red-600 from-orange-400">оптимизатор ПК</span></h1>
            <p class=" mb-8 text-lg font-normal text-gray-500 lg:text-xl sm:px-16 dark:text-gray-400">Наш главный проект
              ezfps app помогает оптимизировать пк для игр и других приложений.</p>
              
            <div class=" flex flex-col space-y-4 sm:flex-row sm:justify-center sm:space-y-0 sm:space-x-4 py-5 sm:py-0">
              <a @click="()=>navigateTo('/download')"
                class="cursor-pointer inline-flex justify-center items-center py-3 px-7 text-base font-medium text-center text-white rounded-lg border border-orange-600 hover:bg-orange-200 focus:ring-4 focus:ring-orange-400 dark:focus:ring-primary-900 mx-2 sm:mx-0">
                <span class="inline-flex text-orange-600 font-bold">Скачать для <span class="inline-flex mt-0.5">
                    <MacosLogo class="ml-4" />
                    <LinuxLogo class="ml-2" />
                    <WindowsLogo class="ml-2" />
                  </span> </span>
              <svg class="ml-3 -mr-1 w-5 h-5 fill-orange-500" fill="" viewBox="0 0 20 20"
                xmlns="http://www.w3.org/2000/svg">
                <path fill-rule="evenodd"
                  d="M10.293 3.293a1 1 0 011.414 0l6 6a1 1 0 010 1.414l-6 6a1 1 0 01-1.414-1.414L14.586 11H3a1 1 0 110-2h11.586l-4.293-4.293a1 1 0 010-1.414z"
                  clip-rule="evenodd"></path>
              </svg>
            </a>
            <a href="https://t.me/ezfps_bot"
              class="inline-flex justify-center items-center py-3 px-7 text-base font-medium text-center text-white rounded-lg bg-orange-500 hover:bg-orange-600 focus:ring-4 focus:ring-orange-400 dark:focus:ring-primary-900 mx-2 sm:mx-0 ">
              Начать бесплатный период
              <svg class="ml-2 -mr-1 w-5 h-5" fill="currentColor" viewBox="0 0 20 20"
                xmlns="http://www.w3.org/2000/svg">
                <path fill-rule="evenodd"
                  d="M10.293 3.293a1 1 0 011.414 0l6 6a1 1 0 010 1.414l-6 6a1 1 0 01-1.414-1.414L14.586 11H3a1 1 0 110-2h11.586l-4.293-4.293a1 1 0 010-1.414z"
                  clip-rule="evenodd"></path>
              </svg>
            </a>

          </div>
          
        </div>
      </div>
      <!-- <div class="hidden lg:block">
      <Pudge />
      </div> -->
    </div>
  </div>
</div>
<div class="absolute inset-x-0 top-[calc(100%-13rem)] -z-10 transform-gpu overflow-hidden blur-3xl sm:top-[calc(100%-30rem)]" aria-hidden="true">
        <div class="relative left-[calc(50%+3rem)] aspect-[1155/678] w-[36.125rem] -translate-x-1/2 bg-gradient-to-tr from-[#ff80b5] to-[#f88030] opacity-30 sm:left-[calc(50%+36rem)] sm:w-[72.1875rem]" style="clip-path: polygon(74.1% 44.1%, 100% 61.6%, 97.5% 26.9%, 85.5% 0.1%, 80.7% 2%, 72.5% 32.5%, 60.2% 62.4%, 52.4% 68.1%, 47.5% 58.3%, 45.2% 34.5%, 27.5% 76.7%, 0.1% 64.9%, 17.9% 100%, 27.6% 76.8%, 76.1% 97.7%, 74.1% 44.1%)" />
      </div>
</div>
</template>