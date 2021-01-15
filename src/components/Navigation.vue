<template>
  <div class="relative max-w-7xl mx-auto">
    <div class="relative pt-6 px-4 sm:px-6 lg:px-8">
      <nav class="relative flex items-center justify-between sm:h-10 lg:justify-start" aria-label="Global">
        <div class="flex items-center flex-grow flex-shrink-0 lg:flex-grow-0">
          <div class="flex items-center justify-between w-full md:w-auto">
            <a href="#">
              <span class="sr-only">Workflow</span>
              <img class="h-8 w-auto sm:h-10" src="https://tailwindui.com/img/logos/workflow-mark-indigo-600.svg">
            </a>
          </div>
        </div>
        <div class="flex md:items-center md:block md:ml-10 md:pr-4 md:space-x-8">              
          <router-link to="/" class="font-medium text-gray-500 hover:text-gray-900">Home</router-link>
          <router-link to="/about" class="font-medium text-gray-500 hover:text-gray-900">Listing</router-link>
        </div>
      </nav>
    </div>
  </div>
</template>
