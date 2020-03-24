# Vue.js

[Vue.js Official Site](https://vuejs.org)


## Directives
  * `v-text`
    * Expects: `String`
  * `v-html`
    * Expects: `String`
  * `v-show`
    * Expects: `Any`
  * `v-if`
    * Expects: `Any`
  * `v-else`
    * Expects: `None`
  * `v-else-if`
    * Expects: `Any`
  * `v-for`
    * Expects: `Array | Object | Number | String | Iterable`
  * `v-on`
    * Expects: `Function | Inline Statement | Object`
  * `v-bind`
    * Expects: `Any (with Argument) | Object (without Argument)`
  * `v-model`
    * Expects: `Various`
  * `v-slot`
    * Expects: `Js Expression`
  * `v-pre`
    * Expects: `None`
  * `v-cloak`
    * Expects: `None`
  * `v-once`
    * Expects: `None`


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
