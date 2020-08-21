<template>
  <div v-if="showWrapper" class="fixed inset-0 overflow-hidden">
    <div class="absolute inset-0 overflow-hidden">
      <transition
        appear
        enter-active-class="duration-300 ease-in-out"
        enter-class="opacity-0"
        enter-to-class="opacity-100"
        leave-active-class="duration-500 ease-in-out"
        leave-class="opacity-100"
        leave-to-class="opacity-0"
      >
        <div v-if="slideOpen" class="absolute inset-0 transition-opacity bg-gray-700 bg-opacity-75" />
      </transition>
      <section class="absolute inset-y-0 right-0 flex max-w-full pl-10 sm:pl-16">
        <!--
        Slide-over panel, show/hide based on slide-over state.
        -->
        <transition
          appear
          enter-active-class="transition duration-500 ease-in-out transform sm:duration-700"
          enter-class="translate-x-full"
          enter-to-class="translate-x-0"
          leave-active-class="transition duration-500 ease-in-out transform sm:duration-700"
          leave-class="translate-x-0"
          leave-to-class="translate-x-full"
          @after-leave="showWrapper = false"
        >
          <div v-if="slideOpen" v-click-outside="closeSlide" class="w-screen max-w-2xl">
            <div class="flex flex-col h-full overflow-y-scroll bg-white shadow-xl">
              <div class="flex-1">
                <!-- Header -->
                <header class="px-4 py-6 bg-gray-50 sm:px-6">
                  <div class="flex items-start justify-between space-x-3">
                    <div class="space-y-1">
                      <h2 class="text-lg font-medium leading-7 text-gray-900">
                        New project
                      </h2>
                      <p class="text-sm leading-5 text-gray-500">
                        Get started by filling in the information below to create your new project.
                      </p>
                    </div>
                    <div class="flex items-center h-7">
                      <button aria-label="Close panel" class="text-gray-400 transition duration-150 ease-in-out hover:text-gray-500" @click="closeSlide">
                        <svg class="w-6 h-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                        </svg>
                      </button>
                    </div>
                  </div>
                </header>

                <!-- Divider container -->
                <div class="py-6 space-y-6 sm:py-0 sm:space-y-0 sm:divide-y sm:divide-gray-200">
                  <!-- Project name -->
                  <div class="px-4 space-y-1 sm:space-y-0 sm:grid sm:grid-cols-3 sm:gap-4 sm:px-6 sm:py-5">
                    <div>
                      <label for="project_name" class="block text-sm font-medium leading-5 text-gray-900 sm:mt-px sm:pt-2">
                        Project name
                      </label>
                    </div>
                    <div class="sm:col-span-2">
                      <div class="rounded-md shadow-sm">
                        <input id="project_name" class="block w-full form-input sm:text-sm sm:leading-5" placeholder="">
                      </div>
                    </div>
                  </div>

                  <!-- Project description -->
                  <div class="px-4 space-y-1 sm:space-y-0 sm:grid sm:grid-cols-3 sm:gap-4 sm:px-6 sm:py-5">
                    <div>
                      <label for="project_description" class="block text-sm font-medium leading-5 text-gray-900 sm:mt-px sm:pt-2">
                        Description
                      </label>
                    </div>
                    <div class="sm:col-span-2">
                      <div class="flex rounded-md shadow-sm">
                        <textarea id="project_description" rows="3" class="block w-full transition duration-150 ease-in-out form-textarea sm:text-sm sm:leading-5" />
                      </div>
                    </div>
                  </div>

                  <!-- Team members -->
                  <div class="px-4 space-y-2 sm:space-y-0 sm:grid sm:grid-cols-3 sm:gap-4 sm:items-center sm:px-6 sm:py-5">
                    <div>
                      <h3 class="text-sm font-medium leading-5 text-gray-900">
                        Team Members
                      </h3>
                    </div>
                    <div class="sm:col-span-2">
                      <div class="flex space-x-2">
                        <a href="#" class="flex-shrink-0 transition duration-150 ease-in-out rounded-full hover:opacity-75 focus:outline-none focus:shadow-outline">
                          <img class="inline-block w-8 h-8 rounded-full" src="https://images.unsplash.com/photo-1491528323818-fdd1faba62cc?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="Tom Warner">
                        </a>

                        <a href="#" class="flex-shrink-0 transition duration-150 ease-in-out rounded-full hover:opacity-75 focus:outline-none focus:shadow-outline">
                          <img class="inline-block w-8 h-8 rounded-full" src="https://images.unsplash.com/photo-1550525811-e5869dd03032?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="Tom Warner">
                        </a>

                        <a href="#" class="flex-shrink-0 transition duration-150 ease-in-out rounded-full hover:opacity-75 focus:outline-none focus:shadow-outline">
                          <img class="inline-block w-8 h-8 rounded-full" src="https://images.unsplash.com/photo-1500648767791-00dcc994a43e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="Tom Warner">
                        </a>

                        <a href="#" class="flex-shrink-0 transition duration-150 ease-in-out rounded-full hover:opacity-75 focus:outline-none focus:shadow-outline">
                          <img class="inline-block w-8 h-8 rounded-full" src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="Tom Warner">
                        </a>

                        <a href="#" class="flex-shrink-0 transition duration-150 ease-in-out rounded-full hover:opacity-75 focus:outline-none focus:shadow-outline">
                          <img class="inline-block w-8 h-8 rounded-full" src="https://images.unsplash.com/photo-1586297098710-0382a496c814?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="Tom Warner">
                        </a>

                        <button type="button" class="inline-flex items-center justify-center flex-shrink-0 w-8 h-8 text-gray-400 transition duration-150 ease-in-out border-2 border-gray-200 border-dashed rounded-full hover:text-gray-500 hover:border-gray-300 focus:text-gray-500 focus:border-gray-300 focus:outline-none" aria-label="Add team member">
                          <svg class="w-5 h-5" viewBox="0 0 20 20" fill="currentColor">
                            <path fill-rule="evenodd" d="M10 3a1 1 0 011 1v5h5a1 1 0 110 2h-5v5a1 1 0 11-2 0v-5H4a1 1 0 110-2h5V4a1 1 0 011-1z" clip-rule="evenodd" />
                          </svg>
                        </button>
                      </div>
                    </div>
                  </div>

                  <!-- Privacy -->
                  <fieldset>
                    <div class="px-4 space-y-2 sm:space-y-0 sm:grid sm:grid-cols-3 sm:gap-4 sm:items-start sm:px-6 sm:py-5">
                      <div>
                        <legend class="text-sm font-medium leading-5 text-gray-900">
                          Privacy
                        </legend>
                      </div>
                      <div class="space-y-5 sm:col-span-2">
                        <div class="space-y-5 sm:mt-0">
                          <div class="relative flex items-start">
                            <div class="absolute flex items-center h-5">
                              <input
                                id="public_access"
                                aria-describedby="public_access_description"
                                type="radio"
                                name="privacy"
                                class="w-4 h-4 text-blue-600 transition duration-150 ease-in-out form-radio"
                                checked
                              >
                            </div>
                            <div class="text-sm leading-5 pl-7">
                              <label for="public_access" class="font-medium text-gray-900">
                                Public access
                              </label>
                              <p id="public_access_description" class="text-gray-500">
                                Everyone with the link will see this project
                              </p>
                            </div>
                          </div>

                          <div class="relative flex items-start">
                            <div class="absolute flex items-center h-5">
                              <input id="restricted_access" aria-describedby="restricted_access_description" type="radio" name="privacy" class="w-4 h-4 text-blue-600 transition duration-150 ease-in-out form-radio">
                            </div>
                            <div class="text-sm leading-5 pl-7">
                              <label for="restricted_access" class="font-medium text-gray-900">
                                Private to Project Members
                              </label>
                              <p id="restricted_access_description" class="text-gray-500">
                                Only members of this project would be able to access
                              </p>
                            </div>
                          </div>

                          <div class="relative flex items-start">
                            <div class="absolute flex items-center h-5">
                              <input id="private_access" aria-describedby="private_access_description" type="radio" name="privacy" class="w-4 h-4 text-blue-600 transition duration-150 ease-in-out form-radio">
                            </div>
                            <div class="text-sm leading-5 pl-7">
                              <label for="private_access" class="font-medium text-gray-900">
                                Private to you
                              </label>
                              <p id="private_access_description" class="text-gray-500">
                                You are the only one able to access this project
                              </p>
                            </div>
                          </div>
                        </div>
                        <hr class="border-gray-200">
                        <div class="flex flex-col space-y-4 space-between sm:flex-row sm:items-center sm:space-between sm:space-y-0">
                          <div class="flex-1">
                            <a class="group flex items-center text-sm leading-5 text-blue-600 hover:text-blue-900 focus:text-blue-900 font-medium space-x-2.5" href="#">
                              <svg class="w-5 h-5 text-blue-500 group-hover:text-blue-900 group-focus:text-blue-900" viewBox="0 0 20 20" fill="currentColor">
                                <path fill-rule="evenodd" d="M12.586 4.586a2 2 0 112.828 2.828l-3 3a2 2 0 01-2.828 0 1 1 0 00-1.414 1.414 4 4 0 005.656 0l3-3a4 4 0 00-5.656-5.656l-1.5 1.5a1 1 0 101.414 1.414l1.5-1.5zm-5 5a2 2 0 012.828 0 1 1 0 101.414-1.414 4 4 0 00-5.656 0l-3 3a4 4 0 105.656 5.656l1.5-1.5a1 1 0 10-1.414-1.414l-1.5 1.5a2 2 0 11-2.828-2.828l3-3z" clip-rule="evenodd" />
                              </svg>
                              <span>
                                Copy link
                              </span>
                            </a>
                          </div>
                          <div>
                            <a class="group flex items-center text-sm leading-5 text-gray-500 hover:text-gray-900 focus:text-gray-900 space-x-2.5" href="#">
                              <svg class="w-5 h-5 text-gray-400 group-hover:text-gray-500" viewBox="0 0 20 20" fill="currentColor">
                                <path fill-rule="evenodd" d="M18 10a8 8 0 11-16 0 8 8 0 0116 0zm-8-3a1 1 0 00-.867.5 1 1 0 11-1.731-1A3 3 0 0113 8a3.001 3.001 0 01-2 2.83V11a1 1 0 11-2 0v-1a1 1 0 011-1 1 1 0 100-2zm0 8a1 1 0 100-2 1 1 0 000 2z" clip-rule="evenodd" />
                              </svg>
                              <span>
                                Learn more about sharing
                              </span>
                            </a>
                          </div>
                        </div>
                      </div>
                    </div>
                  </fieldset>
                </div>
              </div>

              <!-- Action buttons -->
              <div class="flex-shrink-0 px-4 py-5 border-t border-gray-200 sm:px-6">
                <div class="flex justify-end space-x-3">
                  <span class="inline-flex rounded-md shadow-sm">
                    <button type="button" class="px-4 py-2 text-sm font-medium leading-5 text-gray-700 transition duration-150 ease-in-out border border-gray-300 rounded-md hover:text-gray-500 focus:outline-none focus:border-blue-300 focus:shadow-outline-blue active:bg-gray-50 active:text-gray-800">
                      Cancel
                    </button>
                  </span>
                  <span class="inline-flex rounded-md shadow-sm">
                    <button type="submit" class="inline-flex justify-center px-4 py-2 text-sm font-medium leading-5 text-white transition duration-150 ease-in-out bg-blue-600 border border-transparent rounded-md hover:bg-blue-500 focus:outline-none focus:border-blue-700 focus:shadow-outline-blue active:bg-blue-700">
                      Create
                    </button>
                  </span>
                </div>
              </div>
            </div>
          </div>
        </transition>
      </section>
    </div>
  </div>
</template>

<script>
import vClickOutside from 'v-click-outside'
export default {
  name: 'WideSlide',
  directives: {
    clickOutside: vClickOutside.directive
  },
  props: {
    shown: {
      type: Boolean,
      default: false
    }
  },
  data () {
    return {
      slideOpen: false,
      showWrapper: false
    }
  },
  watch: {
    shown (newVal) {
      if (newVal) {
        this.showWrapper = true
        this.slideOpen = true
      }
    }
  },
  methods: {
    closeSlide () {
      // only needs to change this variable,
      // as showWrapper will change after the animation completes
      this.slideOpen = false
      this.$emit('closed')
    }
  }
}
</script>
