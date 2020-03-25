# Vue.js

[Vue.js Official Site](https://vuejs.org)

---

## Directives

| Component   | Expected Type                       | Description |
| ----------- | ----------------------------------- | ----------- |
| `v-text`    | String                              | -           |
| `v-html`    | String                              | -           |
| `v-show`    | Any                                 | -           |
| `v-if`      | Any                                 | -           |
| `v-else`    | None                                | -           |
| `v-else-if` | Any                                 | -           |
| `v-for`     | Array/Object/Number/String/Iterable | -           |
| `v-on`      | Function/Inline Statement/Object    | -           |
| `v-bind`    | Any/Object                          | -           |
| `v-model`   | Various                             | -           |
| `v-slot`    | Expression                          | -           |
| `v-pre`     | None                                | -           |
| `v-cloak`   | None                                | -           |
| `v-once`    | None                                | -           |

---

## Lifecycle Hooks
* All Lifecycle hooks automatically have their `this` context bound to the instance.
* DO NOT USE `() => {}` Arrow functions to define a lifecycle method.
  * Arrow functions bind the parent context.

```js
export default {
  // 1
  beforeCreate: function() { ... },
  // 2
  created: function() { ... },
  // 3
  beforeMount: function() { ... },
  // 4
  mounted: function() { ... },
  // 5
  beforeUpdate: function() { ... },
  // 6
  updated: function() { ... },
  // 7
  activated: function() { ... },
  // 8
  deactivated: function() { ... },
  // 9
  beforeDestroy: function() { ... },
  // 10
  destroyed: function() { ... },
  // 11
  errorCaptured: function() { ... }
}
```
