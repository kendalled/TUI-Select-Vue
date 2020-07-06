<template>
  <nav class="top-0 z-10 bg-white sm:sticky" @keydown.escape="closeAll">
    <div class="relative z-20 border-b border-gray-200">
      <div class="px-2 mx-auto max-w-7xl sm:px-4 lg:px-8">
        <div class="flex justify-between h-16">
          <div class="flex px-2 lg:px-0">
            <!-- extra div to add flyout click handler -->
            <div class="flex items-center h-full" @click="closeAll">
              <nuxt-link title="Lapel Pins and Coins - Home" to="/" class="flex items-center flex-shrink-0 rounded-md focus:outline-none">
                <span class="sr-only">Home</span>
                <img class="block w-auto h-7 lg:hidden" src="~/static/lapel.svg" alt="">
                <img data-not-lazy class="hidden w-auto mt-0.5 lg:block h-7" src="~/static/lapel.svg" alt="">
              </nuxt-link>
            </div>
            <div class="hidden antialiased lg:ml-8 lg:flex">
              <button type="button" :class="[selected === 1 ? 'border-blue-500 text-gray-900 focus:border-blue-700' : 'text-gray-500']" class="inline-flex items-center pt-1 space-x-1 text-sm font-medium leading-5 transition duration-150 ease-in-out border-b-2 border-transparent group hover:text-gray-900 hover:border-gray-300 focus:border-gray-300 focus:outline-none focus:text-gray-900" @click="togglePinFlyout">
                <span>Lapel Pins</span>
                <!-- Item active: "text-gray-600", Item inactive: "text-gray-400" -->
                <svg class="w-5 h-5 text-gray-400 transition duration-150 ease-in-out group-hover:text-gray-500 group-focus:text-gray-500" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z" clip-rule="evenodd" />
                </svg>
              </button>
              <button type="button" :class="[selected === 2 ? 'border-blue-500 text-gray-900 focus:border-blue-700' : 'text-gray-500']" class="inline-flex items-center pt-1 ml-8 space-x-1 text-sm font-medium leading-5 transition duration-150 ease-in-out border-b-2 border-transparent group hover:text-gray-900 hover:border-gray-300 focus:border-gray-300 focus:outline-none focus:text-gray-900" @click="toggleCoinFlyout">
                <span>Challenge Coins</span>
                <!-- Item active: "text-gray-600", Item inactive: "text-gray-400" -->
                <svg class="w-5 h-5 text-gray-400 transition duration-150 ease-in-out group-hover:text-gray-500 group-focus:text-gray-500" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z" clip-rule="evenodd" />
                </svg>
              </button>
              <nuxt-link to="/keychains" :class="[selected === 3 ? 'border-blue-500 text-gray-900 focus:border-blue-700' : 'text-gray-500']" class="inline-flex items-center px-1 pt-1 ml-8 text-sm font-medium leading-5 text-gray-500 transition duration-150 ease-in-out border-b-2 border-transparent hover:text-gray-700 hover:border-gray-300 focus:outline-none focus:text-gray-700 focus:border-gray-300">
                Keychains
              </nuxt-link>
              <nuxt-link to="/blog" :class="[selected === 4 ? 'border-blue-500 text-gray-900 focus:border-blue-700' : 'text-gray-500']" class="inline-flex items-center px-1 pt-1 ml-8 text-sm font-medium leading-5 text-gray-500 transition duration-150 ease-in-out border-b-2 border-transparent hover:text-gray-700 hover:border-gray-300 focus:outline-none focus:text-gray-700 focus:border-gray-300">
                Blog<span class="hidden xl:inline xl:ml-1"> Posts</span>
              </nuxt-link>
            </div>
          </div>
          <div class="items-center justify-end flex-1 hidden px-2 lg:ml-6 lg:flex">
            <!-- TODO: add search here (button blurs if you go to quote) -->
            <nuxt-link id="quoteButton" to="/quote" class="inline-flex items-center px-4 py-2 text-sm font-medium leading-5 text-blue-700 transition duration-150 ease-in-out bg-blue-100 border border-transparent rounded-md focus:outline-none focus:border-blue-300 focus:shadow-outline-blue hover:bg-blue-50 active:bg-blue-200">
              Free Quote
            </nuxt-link>
          </div>
          <div class="flex items-center lg:hidden">
            <button aria-label="Menu Toggle" class="inline-flex items-center justify-center p-2 text-gray-400 transition duration-150 ease-in-out rounded-md hover:text-gray-500 hover:bg-gray-100 focus:outline-none focus:bg-gray-100 focus:text-gray-500" @click="mobileOpen = !mobileOpen">
              <svg class="w-6 h-6" stroke="currentColor" fill="none" viewBox="0 0 24 24">
                <path
                  :class="[mobileOpen ? 'hidden' : 'inline-flex']"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M4 6h16M4 12h16M4 18h16"
                />
                <path
                  :class="[!mobileOpen ? 'hidden' : 'inline-flex']"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M6 18L18 6M6 6l12 12"
                />
              </svg>
            </button>
          </div>
          <div class="hidden lg:ml-4 lg:flex lg:items-center">
            <!-- phone -->
            <button id="phone-button" aria-label="Contact Button" class="flex-shrink-0 p-1 text-gray-400 transition duration-150 ease-in-out border-2 border-transparent rounded-full hover:text-gray-500 focus:outline-none focus:text-gray-500 focus:bg-gray-100" @click="testScroll('contact-section')">
              <svg
                class="w-6 h-6"
                fill="none"
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                stroke="currentColor"
                viewBox="0 0 24 24"
              ><path d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z" /></svg>
            </button>
            <!-- bell
            <button class="flex-shrink-0 p-1 text-gray-400 transition duration-150 ease-in-out border-2 border-transparent rounded-full hover:text-gray-500 focus:outline-none focus:text-gray-500 focus:bg-gray-100">
              <svg
                class="w-6 h-6"
                fill="none"
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                stroke="currentColor"
                viewBox="0 0 24 24"
              ><path d="M15 17h5l-1.405-1.405A2.032 2.032 0 0118 14.158V11a6.002 6.002 0 00-4-5.659V5a2 2 0 10-4 0v.341C7.67 6.165 6 8.388 6 11v3.159c0 .538-.214 1.055-.595 1.436L4 17h5m6 0v1a3 3 0 11-6 0v-1m6 0H9" /></svg>
            </button> -->
            <!-- dots -->
            <div class="relative flex-shrink-0 ml-4">
              <div>
                <button aria-label="Expand quick links" class="flex items-center text-gray-400 hover:text-gray-600 focus:outline-none focus:text-gray-600" @click="open = !open">
                  <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20">
                    <path d="M10 6a2 2 0 110-4 2 2 0 010 4zM10 12a2 2 0 110-4 2 2 0 010 4zM10 18a2 2 0 110-4 2 2 0 010 4z" />
                  </svg>
                </button>
              </div>
              <!-- todo: simplify closing, add aria roles -->
              <!-- <div
                v-if="(pinFlyoutOpen || coinFlyoutOpen)"
                class="fixed bottom-0 left-0 right-0 focus:outline-none"
                style="height: 55.68%;"
                tabindex="-1"
                aria-label="Closes flyout menus"
                @click="closeAll"
              /> -->
              <div
                v-if="open"
                class="fixed inset-0 focus:outline-none"
                tabindex="-1"
                aria-label="Closes navbar by clicking outside"
                @click="open = false"
              />
              <transition
                enter-class="transform scale-95 opacity-0"
                enter-active-class="transition duration-200 ease-out"
                enter-to-class="transform scale-100 opacity-100"
                leave-class="transform scale-100 opacity-100"
                leave-active-class="transition duration-75 ease-in"
                leave-to-class="transform scale-95 opacity-0"
              >
                <div
                  v-show="open"
                  class="absolute right-0 w-48 mt-2 origin-top-right rounded-md shadow-lg"
                >
                  <div class="py-1 bg-white rounded-md shadow-xs">
                    <nuxt-link to="/checkout" class="block px-4 py-2 text-sm leading-5 text-gray-700 transition duration-150 ease-in-out hover:bg-gray-100 focus:outline-none focus:bg-gray-100">
                      Checkout
                    </nuxt-link>
                    <a href="#" class="block px-4 py-2 text-sm leading-5 text-gray-700 transition duration-150 ease-in-out hover:bg-gray-100 focus:outline-none focus:bg-gray-100">Settings</a>
                    <nuxt-link to="/login" class="block px-4 py-2 text-sm leading-5 text-gray-700 transition duration-150 ease-in-out hover:bg-gray-100 focus:outline-none focus:bg-gray-100">
                      Sign In
                    </nuxt-link>
                  </div>
                </div>
              </transition>
            </div>
          </div>
        </div>
      </div>
      <transition
        enter-active-class="transition duration-200 ease-out"
        enter-class="-translate-y-1 opacity-0"
        enter-to-class="translate-y-0 opacity-100"
        leave-active-class="transition duration-150 ease-in"
        leave-class="translate-y-0 opacity-100"
        leave-to-class="-translate-y-1 opacity-0"
      >
        <div v-show="mobileOpen" class="absolute w-full transform bg-white border-t border-gray-200 shadow-lg lg:hidden">
          <div class="pt-2 pb-3">
            <nuxt-link to="/pins" title="Professinally designed lapel pins" :class="[selected === 1 ? 'text-blue-700 border-blue-500 bg-blue-50 focus:text-blue-800 focus:bg-blue-100 focus:border-blue-700' : 'text-gray-600 border-transparent hover:text-gray-800 hover:bg-gray-50 hover:border-gray-300 focus:text-gray-800 focus:bg-gray-50 focus:border-gray-300', 'block py-2 pl-3 pr-4 text-base font-medium transition duration-150 ease-in-out border-l-4 focus:outline-none']">
              Lapel Pins
            </nuxt-link>
            <nuxt-link to="/coins" :class="[selected === 2 ? 'text-blue-700 border-blue-500 bg-blue-50 focus:text-blue-800 focus:bg-blue-100 focus:border-blue-700' : 'text-gray-600 border-transparent hover:text-gray-800 hover:bg-gray-50 hover:border-gray-300 focus:text-gray-800 focus:bg-gray-50 focus:border-gray-300', 'mt-1 block py-2 pl-3 pr-4 text-base font-medium transition duration-150 ease-in-out border-l-4 focus:outline-none']" title="Professinally designed challenge coins">
              Challenge Coins
            </nuxt-link>
            <nuxt-link to="/keychains" title="Professinally designed keychains" :class="[selected === 3 ? 'text-blue-700 border-blue-500 bg-blue-50 focus:text-blue-800 focus:bg-blue-100 focus:border-blue-700' : 'text-gray-600 border-transparent hover:text-gray-800 hover:bg-gray-50 hover:border-gray-300 focus:text-gray-800 focus:bg-gray-50 focus:border-gray-300', 'mt-1 block py-2 pl-3 pr-4 text-base font-medium transition duration-150 ease-in-out border-l-4 focus:outline-none']">
              Keychains
            </nuxt-link>
            <nuxt-link to="/blog" title="Our weekly blog posts" :class="[selected === 4 ? 'text-blue-700 border-blue-500 bg-blue-50 focus:text-blue-800 focus:bg-blue-100 focus:border-blue-700' : 'text-gray-600 border-transparent hover:text-gray-800 hover:bg-gray-50 hover:border-gray-300 focus:text-gray-800 focus:bg-gray-50 focus:border-gray-300', 'mt-1 block py-2 pl-3 pr-4 text-base font-medium transition duration-150 ease-in-out border-l-4 focus:outline-none']">
              Blog Posts
            </nuxt-link>
          </div>
          <div class="pt-4 pb-3 border-t border-gray-200">
            <div class="flex items-center px-4">
              <div class="flex-shrink-0">
                <span class="inline-block w-10 h-10 overflow-hidden bg-gray-100 border-2 border-gray-300 rounded-full">
                  <svg class="w-full h-full text-gray-300" fill="currentColor" viewBox="0 0 24 24">
                    <path d="M24 20.993V24H0v-2.996A14.977 14.977 0 0112.004 15c4.904 0 9.26 2.354 11.996 5.993zM16.002 8.999a4 4 0 11-8 0 4 4 0 018 0z" />
                  </svg>
                </span>
              </div>
              <div class="ml-3">
                <div class="text-base font-medium leading-6 text-gray-800">
                  Your Account
                </div>
                <div class="text-sm font-medium leading-5 text-gray-500">
                  you@example.com
                </div>
              </div>
            </div>
            <div class="mt-3">
              <nuxt-link to="/checkout" class="block px-4 py-2 text-base font-medium text-gray-500 transition duration-150 ease-in-out hover:text-gray-800 hover:bg-gray-100 focus:outline-none focus:text-gray-800 focus:bg-gray-100">
                Checkout
              </nuxt-link>
              <a href="#" class="block px-4 py-2 mt-1 text-base font-medium text-gray-500 transition duration-150 ease-in-out hover:text-gray-800 hover:bg-gray-100 focus:outline-none focus:text-gray-800 focus:bg-gray-100">Settings</a>
              <nuxt-link to="/login" class="block px-4 py-2 mt-1 text-base font-medium text-gray-500 transition duration-150 ease-in-out hover:text-gray-800 hover:bg-gray-100 focus:outline-none focus:text-gray-800 focus:bg-gray-100">
                Sign In
              </nuxt-link>
            </div>
          </div>
        </div>
      </transition>
    </div>
    <!-- Flyout menu component -->
    <FlyoutBetter
      :opened="pinFlyoutOpen"
      :category="'pin'"
      :links="pinListOne"
      :links2="pinListTwo"
      :blogs="pBlogs"
      @close="pinFlyoutOpen = false"
    />
    <FlyoutBetter
      :opened="coinFlyoutOpen"
      :category="'coin'"
      :links="coinListOne"
      :links2="coinListTwo"
      :blogs="cBlogs"
      @close="coinFlyoutOpen = false"
    />
  </nav>
</template>

<script>
// import { auth } from '~/plugins/firebase.js'
import FlyoutBetter from '~/components/FlyoutBetter'
export default {
  name: 'FullNav',
  components: {
    FlyoutBetter
  },
  data () {
    return {
      links: [
        {
          type: 'Lapel Pins',
          list1: [
            {
              title: 'Hard Enamel',
              ref: '/pins/hard-enamel'
            },
            {
              title: 'Soft Enamel',
              ref: '/pins/soft-enamel'
            },
            {
              title: 'Die Struck',
              ref: '/pins/die-struck'
            },
            {
              title: 'Offset Printed',
              ref: '/pins/offset-printed'
            },
            {
              title: 'Silk Screen',
              ref: '/pins/silk-screen'
            }
          ],
          list2: [
            {
              title: 'Lapel Pins',
              ref: '/pins'
            },
            {
              title: 'Medical Pins',
              ref: '/pins/medical'
            },
            {
              title: 'Sports Pins',
              ref: '/pins/sports-trading'
            },
            {
              title: 'Gaming Pins',
              ref: '/pins/video-game'
            },
            {
              title: 'School Pins',
              ref: '/pins/school'
            },
            {
              title: 'Heart Pins',
              ref: '/pins/heart'
            },
            {
              title: 'Angel Pins',
              ref: '/pins/angel'
            },
            {
              title: 'Space Pins',
              ref: '/pins/space'
            },
            {
              title: 'Star Pins',
              ref: '/pins/star'
            },
            {
              title: 'Animal Pins',
              ref: '/pins/animal'
            },
            {
              title: 'Safety Pins',
              ref: '/pins/safety'
            },
            {
              title: 'Rainbow Pins',
              ref: '/pins/rainbow'
            },
            {
              title: 'Holiday Pins',
              ref: '/pins/holiday'
            },
            {
              title: 'Tie Pins',
              ref: '/pins/tie'
            },
            {
              title: 'State Flag Pins',
              ref: '/pins/state-flag'
            },
            {
              title: 'LGBTQ Pins',
              ref: '/pins/lgbtq-pride'
            },
            {
              title: 'World Flag Pins',
              ref: '/pins/world-flag'
            },
            {
              title: 'Fashion Pins',
              ref: '/pins/fashion'
            },
            {
              title: 'Religious Pins',
              ref: '/pins/religious'
            },
            {
              title: 'Public Servant Pins',
              ref: '/pins/public-servant'
            },
            {
              title: 'American Flag Pins',
              ref: '/pins/american-flag'
            },
            {
              title: 'TV Show Pins',
              ref: '/pins/tv-show'
            },
            {
              title: 'Movie Pins',
              ref: '/pins/movie'
            },
            {
              title: 'Varsity Pins',
              ref: '/pins/varsity'
            },
            {
              title: 'Political Pins',
              ref: '/pins/political'
            }
          ]
        },
        {
          type: 'Challenge Coins',
          list1: [
            {
              title: 'Antique Gold',
              ref: '/coins'
            },
            {
              title: 'Antique Silver',
              ref: '/coins'
            },
            {
              title: 'Antique Copper',
              ref: '/coins'
            },
            {
              title: 'Polished Nickel',
              ref: '/coins'
            },
            {
              title: 'Dual Plated',
              ref: '/coins'
            }
          ],
          list2: [
            {
              title: 'Challenge Coins',
              ref: '/coins'
            },
            {
              title: 'Nursing Coins',
              ref: '/coins/nursing'
            },
            {
              title: 'Fire Coins',
              ref: '/coins/fire-department'
            },
            {
              title: 'Police Coins',
              ref: '/coins/police'
            },
            {
              title: 'Military Coins',
              ref: '/coins/military'
            },
            {
              title: 'US Marine Coins',
              ref: '/coins/marines'
            }
          ]
        }
      ],
      pBlogs: [
        {
          title: 'The History of Nursing Pins',
          desc: 'Nursing pins have played a vital role in healthcare for over twenty years. Learn about their interesting backstory.',
          img: 'https://a.storyblok.com/f/78493/1024x1024/42b3b9c66f/nursingpins.jpg',
          href: '/blog/history-of-nursing-pins'
        },
        {
          title: 'A Complete History of Disney Pins',
          desc: 'An in-depth overview of the origins, changes, and loyal community behind Disney\'s famous lapel pins.',
          img: 'https://a.storyblok.com/f/78493/800x502/85cb1da038/disneypinssmall.jpg',
          href: '/blog/disney-pins'
        }
      ],
      cBlogs: [
        {
          title: 'A Complete History of Challenge Coins',
          desc: 'Nursing pins have played a vital role in the military for over 80 years. Learn about their interesting backstory.',
          img: require('~/static/coinblog2.jpg'),
          href: '/blog'
        },
        {
          title: 'How to Make Challenge Coins',
          desc: 'An in-depth overview of the origins, changes, and loyal community behind challenge coins - with a tutorial.',
          img: require('~/static/coinblog1.jpg'),
          href: '/blog/'
        }
      ],
      mobileOpen: false,
      // dropdown
      open: false,
      // flyouts
      pinFlyoutOpen: false,
      coinFlyoutOpen: false,
      flyoutOpen: false
    }
  },
  computed: {
    selected () {
      const path = this.$route.path
      const ind = path.lastIndexOf('/') || path.length
      const startingPath = path.substr(0, ind)
      return startingPath === '/' ? 0 : startingPath === '/pins' ? 1 : startingPath === '/coins' ? 2 : startingPath === '/keychains' ? 3 : startingPath === '/blog' ? 4 : startingPath === '/quote' ? 5 : -1
    },
    path () {
      return this.$route.path
    },
    pinListOne () {
      return this.links[0].list1
    },
    pinListTwo () {
      return this.links[0].list2
    },
    coinListOne () {
      return this.links[1].list1
    },
    coinListTwo () {
      return this.links[1].list2
    }
  },
  watch: {
    selected (newVal, oldVal) {
      // todo: adjust timing
      if (newVal !== oldVal) {
        this.closeAll()
      }
      // blur quote button on route change
      if (newVal === 5) {
        document.getElementById('quoteButton').blur()
      }
    },
    path (newVal, oldVal) {
      if (newVal !== oldVal) {
        this.pinFlyoutOpen = false
        this.coinFlyoutOpen = false
        this.mobileOpen = false
      }
    }
  },
  methods: {
    closeAll () {
      this.open = false
      this.coinFlyoutOpen = false
      this.pinFlyoutOpen = false
      this.flyoutOpen = false
    },
    // TODO: fix logic
    togglePinFlyout () {
      // handle all pin only events
      this.pinFlyoutOpen = !this.pinFlyoutOpen
      if (this.coinFlyoutOpen) {
        this.coinFlyoutOpen = !this.coinFlyoutOpen
      }
    },
    toggleCoinFlyout () {
      // handle all pin only events
      this.coinFlyoutOpen = !this.coinFlyoutOpen
      if (this.pinFlyoutOpen) {
        this.pinFlyoutOpen = !this.pinFlyoutOpen
      }
    },
    testScroll (elem) {
      if (process.browser) {
        document.getElementById(elem).scrollIntoView({ behavior: 'smooth', block: 'center' })
        document.getElementById('phone-button').blur()
      }
    }
  }
  // mounted () {
  //   const user = auth.currentUser
  //   if (user != null) {
  //     // this.email = user.email
  //     // this.displayName = user.displayName
  //     this.userPhoto = user.photoURL
  //   }
  // }
}
</script>
