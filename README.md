# TUI-Select-Vue &nbsp; ⌨️ 
Vue.js Implementation of TUI components, plug and play. (Fully accessible!) <br> <br>
<b>Custom select:</b> Look at CustomSelect.vue, MultiSelect.vue <br>
<b>Wide Slideover:</b> Look at WideSlide.vue

# Note
Replace 'Lapel Pins', 'Challenge Coins', and 'Keychains' with any options you choose, then *pass them as a prop* from a parent component. Example below. After that, feel free to delete my sample choices and replace with your own.

EX: ParentComponent.vue

```
NOTE: You need 'v-click-outside' installed for click.away events to work
...
<CustomSelect :options="choiceList" />
<CustomMultiSelect :options="choiceList" />
...
data () {
  return {
    choiceList: [
      'Choice one',
      'Choice two',
      'Choice three'
    ]
   }
} ```
