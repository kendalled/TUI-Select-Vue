# TUI-Select-Vue
NOTE: You need vue-click-outside to handle click.away events<br>
Vue.js Implementation of TailwindUI custom select: look at CustomSelect.vue, MultiSelect.vue

# Note
Replace 'Lapel Pins', 'Challenge Coins', and 'Keychains' with any options you choose, then *pass them as a prop* from a parent component. Example below. After that, feel free to delete my sample choices and replace with your own.

EX: ParentComponent.vue
```
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
