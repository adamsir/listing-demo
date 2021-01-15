<template>
  <div class="py-8 px-8 bg-white rounded-xl sm:py-4 flex flex-row flex-wrap justify-items-center max-h-screen overflow-y-scroll">
    <div v-for="(item, index) of items" :key="index" class="my-2 mx-2">
      <div v-text="item.key"></div>
      <strong v-text="item.value"></strong>
    </div>
  </div>
</template>

<script lang="ts">
  const normalizeData = (obj) => {
    let arr = []

    Object.entries  (obj).map((item) => {
      arr.push({
        key: item[0],
        value: item[1]
      })
    })

    return arr
  }

  export default {
    data() {
      return {
        items: {}
      }
    },
    props: {
      payload: {
        type: Object,
        default: {}
      }
    },
    methods: {

    },
    beforeMount() {
      this.items = normalizeData(this.payload)
    }
  }
</script>
