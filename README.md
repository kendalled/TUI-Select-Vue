# TUI-Select-Vue
Vue.js Implementation of TUI (Props to Adam & Team!) custom select: look at CustomSelect.vue, MultiSelect.vue

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
