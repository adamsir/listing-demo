<template>
  <div class="my-4 py-8 px-8 max-w-sm bg-white rounded-xl shadow-md space-y-2 sm:py-4 sm:flex sm:items-center sm:space-y-0 sm:space-x-6">
    <img class="block mx-auto rounded-full sm:mx-0 sm:flex-shrink-0" width="80" height="80" :src="`//placehold.it/80x80?text=${getInitials(payload.name)}`" alt="Woman's Face">
    <div class="text-center space-y-2 sm:text-left">
      <div>
        <p class="text-lg text-black font-semibold" v-text="payload.name"></p>
        <p class="text-gray-500 font-medium" v-text="payload.gender"></p>
      </div>
      <button @click="showDialog(true)" class="px-4 py-1 text-sm text-purple-600 font-semibold rounded-full border border-purple-200 hover:text-white hover:bg-purple-600 hover:border-transparent focus:outline-none focus:ring-2 focus:ring-purple-600 focus:ring-offset-2">View raw</button>
    </div>
  </div>
  <Dialog 
    title="Raw Sample"
    :visible="detailVisible" 
    @visibility="showDialog" >
    <detail :payload="payload" />
  </Dialog>
</template>

<script lang="ts">
  import { defineAsyncComponent } from 'vue'

  export default {
    data() {
      return {
        detailVisible: false,
      }
    },
    props: {
      payload: Object
    },
    components: {
      Dialog: defineAsyncComponent(() =>
        import('@/components/Dialog.vue')
      ),
      Detail: defineAsyncComponent(() =>
        import('@/components/CardDetail.vue')
      )
    },
    methods: {
      getInitials(arg) {
        return arg.substr(0, 2).toUpperCase()
      },
      showDialog(arg) {
        this.detailVisible = arg
      }
    }
  }
</script>
