<template>
  <section class="max-w-5xl w-full">
    <h1 class="font-bold text-gray-800 mb-4">
      Try clicking each of the dots
    </h1>
    <!-- Transition group A -->
    <p class="font-semibold text-gray-800">
      Manually keyed children (A)
    </p>
    <transition-group
      enter-active-class="transition-all duration-150 ease-in-out"
      enter-class="opacity-0"
      enter-to-class="opacity-100"
      leave-active-class="transition-all duration-150 ease-in-out"
      leave-class="opacity-100"
      leave-to-class="opacity-0"
    >
      <div v-if="showDiv" key="theDiv" class="inline-block bg-gray-500 rounded-full h-16 w-16 hover:bg-gray-300 cursor-pointer transition-colors duration-150 ease-in-out" @click="showDiv = !showDiv" />
      <span v-if="showDiv2" key="theSpan" class="inline-block bg-gray-500 rounded-full h-16 w-16 hover:bg-gray-300 cursor-pointer transition-colors duration-150 ease-in-out" @click="showDiv2 = !showDiv2" />
    </transition-group>

    <!-- Transition group B -->
    <p class="font-semibold text-gray-800">
      Iteravely keyed children with v-for (B)
    </p>
    <transition-group
      enter-active-class="transition-all duration-150 ease-in-out"
      enter-class="opacity-0"
      enter-to-class="opacity-100"
      leave-active-class="transition-all duration-150 ease-in-out"
      leave-class="opacity-100"
      leave-to-class="opacity-0"
    >
      <div v-for="elem in filteredList" :key="elem" class="cursor-pointer hover:bg-blue-300 transition-colors duration-150 ease-in-out inline-block bg-blue-500 rounded-full h-16 w-16" @click="filterList = !filterList" />
    </transition-group>
  </section>
</template>

<script>
export default {
  name: 'TransitionGroupExample',
  data () {
    return {
      showDiv: true,
      showDiv2: true,
      myList: [
        'Option1',
        'Option2',
        'Option3'
      ],
      filterList: false
    }
  },
  computed: {
    filteredList () {
      const arr = [...this.myList]
      return (this.filterList ? arr.splice(1, 2) : arr)
    }
  }
}
</script>
