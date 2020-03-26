# Element UI - Form Components

[Element UI Documentation](https://element.eleme.io/#/en-US)

* Radio
* RadioGroup
* Checkbox
* CheckboxGroup
* Input
* InputNumber
* Select
* Cascader
* Switch
* Slider
* TimePicker
* DatePicker
* DateTimePicker
* Upload
* Rate
* ColorPicker
* Transfer
* Form

---

## Radio

[Element UI - Radio](https://element.eleme.io/#/en-US/component/radio)

Usage: `<el-radio>`, `<el-radio-button>`

```html
<template>
  <el-radio v-model="radio" label="1">A</el-radio>
  <el-radio v-model="radio" label="2">B</el-radio>
<template>

<script>
export default {
  data () {
    return {
      radio: '1'
    };
  }
}
</script>
```

### Radio Attributes

| Attribute       | Type                  | Default | Values            | Description      |
| --------------- |:---------------------:|:-------:| ----------------- | ---------------- |
| `value/v-model` | String/Number/Boolean | -       | -                 | Binding Value    |
| `label`         | String/Number/Boolean | -       | -                 | Radio Value      |
| `disabled`      | Boolean               | false   | -                 | Radio Disabled   |
| `border`        | Boolean               | false   | -                 | Border for Radio |
| `size`          | String                | -       | medium/small/mini | Radio Size       |
| `name`          | String                | -       | -                 | Native `name`    |

### Radio Button Attributes

| Attribute  | Type          | Default | Values | Description    |
| ---------- |:-------------:|:-------:| ------ | -------------- |
| `label`    | String/Number | -       | -      | Radio Value    |
| `disabled` | Boolean       | false   | -      | Radio Disabled |
| `name`     | String        | -       | -      | Native `name`  |

### Radio Events

| Event Name | Parameters        | Description                       |
| ---------- | ----------------- | --------------------------------- |
| `change`   | Radio Label Value | Triggers when Bound value changes |

---

## RadioGroup

[Element UI - RadioGroup](https://element.eleme.io/#/en-US/component/radio)

Usage: `<el-radio-group>`

```html
<template>
  <el-radio-group v-model="radio">
    <el-radio :label="3">A</el-radio>
    <el-radio :label="6">B</el-radio>
    <el-radio :label="9">C</el-radio>
  </el-radio-group>
</template>

<script>
export default {
  data () {
    return {
      radio: 3
    };
  }
}
</script>
```

### Radio Group Attributes

| Attribute       | Type                  | Default | Values            | Description               |
| --------------- |:---------------------:|:-------:| ----------------- | ------------------------- |
| `value/v-model` | String/Number/Boolean | -       | -                 | Binding Value             |
| `size`          | String                | -       | medium/small/mini | Radio Button Sizes        |
| `disabled`      | Boolean               | false   | -                 | Nested Radios Disabled    |
| `text-color`    | String                | #ffffff | -                 | Font Color when Active    |
| `fill`          | String                | #409eff | -                 | Border and Bg when Active |

### Radio Group Events

| Event Name | Parameters        | Description                       |
| ---------- | ----------------- | --------------------------------- |
| `change`   | Radio Label Value | Triggers when Bound value changes |

---

## Checkbox

[Element UI - Checkbox](https://element.eleme.io/#/en-US/component/checkbox)

Usage: `<el-checkbox>`, `<el-checkbox-button>`

```html
<template>
  <el-checkbox v-model="checked">Option A</el-checkbox>
</template>

<script>
export default {
  data () {
    return {
      checked: true
    };
  }
}
</script>
```

### Checkbox Attributes

| Attribute       | Type                  | Default | Values            | Description                    |
| --------------- |:---------------------:|:-------:| ----------------- | ------------------------------ |
| `value/v-model` | String/Number/Boolean | -       | -                 | Binding Value                  |
| `label`         | String/Number/Boolean | -       | -                 | Value of Checkbox in Group     |
| `true-label`    | String/Number/Boolean | -       | -                 | Value of Checkbox if Checked   |
| `false-label`   | String/Number/Boolean | -       | -                 | Value of Checkbox if Unchecked |
| `disabled`      | Boolean               | false   | -                 | Checkbox Disabled              |
| `border`        | Boolean               | false   | -                 | Checkbox Border                |
| `size`          | String                | -       | medium/small/mini | Checkbox Size                  |
| `name`          | String                | -       | -                 | Native `name`                  |
| `checked`       | Boolean               | false   | -                 | If Checkbox Checked            |
| `indeterminate` | Boolean               | false   | -                 | Native `indeterminate`         |

### Checkbox Button Attributes

| Attribute       | Type                  | Default | Values            | Description                    |
| --------------- |:---------------------:|:-------:| ----------------- | ------------------------------ |
| `label`         | String/Number/Boolean | -       | -                 | Value of Checkbox in Group     |
| `true-label`    | String/Number/Boolean | -       | -                 | Value of Checkbox if Checked   |
| `false-label`   | String/Number/Boolean | -       | -                 | Value of Checkbox if Unchecked |
| `disabled`      | Boolean               | false   | -                 | Checkbox Disabled              |
| `name`          | String                | -       | -                 | Native `name`                  |
| `checked`       | Boolean               | false   | -                 | If Checkbox Checked            |

### Checkbox Events

| Event Name | Parameters    | Description                         |
| ---------- | ------------- | ----------------------------------- |
| `change`   | Updated Value | Triggers when Binding value changes |

---

## CheckboxGroup

[Element UI - Checkbox](https://element.eleme.io/#/en-US/component/checkbox)

Usage: `<el-checkbox-group>`

```html
<template>
  <el-checkbox-group v-model="checkList">
    <el-checkbox label="a">A</el-checkbox>
    <el-checkbox label="b">B</el-checkbox>
    <el-checkbox label="c">C</el-checkbox>
    <el-checkbox label="d" disabled>D</el-checkbox>
  </el-checkbox-group>
</template>

<script>
export default {
  data () {
    return {
      checkList: ['a','d']
    };
  }
}
</script>
```

### Checkbox Group Attributes

| Attribute       | Type    | Default | Values            | Description                |
| --------------- |:-------:|:-------:| ----------------- | -------------------------- |
| `value/v-model` | Array   | -       | -                 | Binding Value              |
| `size`          | String  | -       | medium/small/mini | Checkboxes Size or Border  |
| `disabled`      | Boolean | false   | -                 | Nested Checkboxes Disabled |
| `min`           | Number  | -       | -                 | Minimum Checkbox Checked   |
| `max`           | Number  | -       | -                 | Maximum Checkbox Checked   |
| `text-color`    | String  | #ffffff | -                 | Active Font Color          |
| `fill`          | String  | #409eff | -                 | Border and Bg when Active  |

### Checkbox Group Events

| Event Name | Parameters    | Description                         |
| ---------- | ------------- | ----------------------------------- |
| `change`   | Updated Value | Triggers when Binding value changes |

---

## Input

[Element UI - Input](https://element.eleme.io/#/en-US/component/input)

Usage: `<el-input>`, `<el-autocomplete>`

```html
<template>
  <el-input placeholder="Please type..." v-model="input"></el-input>
  <el-input type="textarea" :rows="2" placeholder="Please type..." v-model="area"></el-input>

  <!-- Slot: Use `slot` to distibute & Append/Prepend to Input -->
  <el-input placeholder="Enter URL..." v-model="url">
    <template slot="prepend">https://</template>
  </el-input>

  <!-- Autocomplete: Provide input suggestions -->
  <el-autocomplete
    v-model="search"
    :fetch-suggestions="querySearch"
    @select="handleSelect">
  </el-autocomplete>
</template>

<script>
export default {
  data () {
    return {
      input: '',
      area: '',
      url: '',
      search: ''
    };
  },
  methods: {
    querySearch() { ... },
    handleSelect(item) {
      console.log(item);
    }
  }
}
</script>
```

### Input Attributes

| Attribute         | Type           | Default | Values                           | Description             |
| ----------------- |:--------------:|:-------:| -------------------------------- | ----------------------- |
| `type`            | String         | text    | text, textarea, native types     | Type of Input           |
| `value/v-model`   | String/Number  | -       | -                                | Binding Value           |
| `maxlength`       | Number         | -       | -                                | Max-length of Input     |
| `minlength`       | Number         | -       | -                                | Min-length of Input     |
| `show-word-limit` | Boolean        | false   | -                                | Show Word Count         |
| `placeholder`     | String         | -       | -                                | Placeholder of Input    |
| `clearable`       | Boolean        | false   | -                                | Show Clear Button       |
| `show-password`   | Boolean        | false   | -                                | Show Password Input     |
| `disabled`        | Boolean        | false   | -                                | Input Disabled          |
| `size`            | String         | -       | medium/small/mini                | Size of Input           |
| `prefix-icon`     | String         | -       | -                                | Prefix Icon Class       |
| `suffix-icon`     | String         | -       | -                                | Suffix Icon Class       |
| `rows`            | Number         | 2       | -                                | Textarea Rows           |
| `autosize`        | Boolean/Object | false   | -                                | Textarea Height         |
| `autocomplete`    | String         | off     | on/off                           | Autocomplete Native     |
| `name`            | String         | -       | -                                | Name Native             |
| `readonly`        | Boolean        | false   | -                                | Readonly Native         |
| `max`             | -              | -       | -                                | Max Native              |
| `min`             | -              | -       | -                                | Min Native              |
| `step`            | -              | -       | -                                | Step Native             |
| `resize`          | String         | -       | none, both, horizontal, vertical | Resizability            |
| `autofocus`       | Boolean        | false   | -                                | Autofocus Native        |
| `form`            | String         | -       | -                                | Form Native             |
| `label`           | String         | -       | -                                | Label Text              |
| `tabindex`        | String         | -       | -                                | Input Tabindex          |
| `validate-event`  | Boolean        | true    | -                                | Trigger Form Validation |

### Input Slots

| Name      | Description              |
| --------- | ------------------------ |
| `prefix`  | Content as Input Prefix  |
| `suffix`  | Content as Input Suffix  |
| `prepend` | Content to Prepend Input |
| `append`  | Content to Append Input  |

### Input Events

| Event Name | Parameters             | Description                  |
| ---------- | ---------------------- | ---------------------------- |
| `blur`     | (event: Event)         | Triggers when Input Blurs    |
| `focus`    | (event: Event)         | Triggers when Input Focuses  |
| `change`   | (value: string|number) | Triggers on Unfocus or Enter |
| `input`    | (value: string|number) | Triggers on Value Change     |
| `clear`    | -                      | Triggers on Input Cleared    |

### Input Methods

| Method   | Parameters | Description                  |
| -------- | ---------- | ---------------------------- |
| `focus`  | -          | Focus Input Element          |
| `blur`   | -          | Blur Input Element           |
| `select` | -          | Select Text in Input Element |

### Autocomplete Attributes

| Attribute               | Type                      | Default      | Values | Description                            |
| ----------------------- |:-------------------------:|:------------:| ------ | -------------------------------------- |
| `placeholder`           | String                    | -            | -      | Placeholder Text                       |
| `clearable`             | Boolean                   | false        | -      | Show Clear Button                      |
| `disabled`              | Boolean                   | false        | -      | Autocomplete Disabled                  |
| `value-key`             | String                    | value        | -      | Key-name of Object Suggestion          |
| `icon`                  | String                    | -            | -      | Icon name                              |
| `value`                 | String                    | -            | -      | Binding Value                          |
| `debounce`              | Number                    | 300          | -      | Debounce delay when Typing             |
| `placement`             | String                    | bottom-start | top/top-start/top-end/bottom/bottom-start/bottom-end | Placement of Popup Menu |
| `fetch-suggestions`     | function(query, callback) | -            | -      | Fetch Input Suggestions                |
| `popper-class`          | String                    | -            | -      | Custom Class for Autocomplete Dropdown |
| `trigger-on-focus`      | Boolean                   | true         | -      | Show Suggestions when Input Focus      |
| `name`                  | String                    | -            | -      | Name Native                            |
| `select-when-unmatched` | Boolean                   | false        | -      | Emit `select` Event                    |
| `label`                 | String                    | -            | -      | Label Text                             |
| `prefix-icon`           | String                    | -            | -      | Prefix Icon Class                      |
| `suffix-icon`           | String                    | -            | -      | Suffix Icon Class                      |
| `hide-loading`          | Boolean                   | false        | -      | Hide Loading Icon                      |
| `popper-append-to-body` | Boolean                   | true         | -      | Append Dropdown to Body                |
| `highlight-first-item`  | Boolean                   | false        | -      | Highlight First Suggestion Item        |

### Autocomplete Slots

| Name      | Description              |
| --------- | ------------------------ |
| `prefix`  | Content as Input Prefix  |
| `suffix`  | Content as Input Suffix  |
| `prepend` | Content to Prepend Input |
| `append`  | Content to Append Input  |


### Autocomplete Scoped Slots

| Name | Description                                            |
| ---- | ------------------------------------------------------ |
| -    | Custom content for Input Suggestions. Scope `{ item }` |

### Autocomplete Events

| Event Name | Parameters               | Description                      |
| ---------- | ------------------------ | -------------------------------- |
| `select`   | Suggestion being Clicked | Triggers when Suggestion Clicked |

### Autocomplete Methods

| Method  | Parameters | Description         |
| ------- | ---------- | ------------------- |
| `focus` | -          | Focus Input Element |

---

## InputNumber

[Element UI - InputNumber](https://element.eleme.io/#/en-US/component/input-number)

Usage: `<el-input-number>`

```html
<template>
  <el-input-number
    v-model="num"
    @change="handleChange"
    :min="1"
    :max="10">
  </el-input-number>

  <!-- Step Increments -->
  <el-input-number
    v-model="step"
    :step="2">
  </el-input-number>

  <!-- Decimal Precision -->
  <el-input-number
    v-model="precision"
    :precision="2"
    :step="0.1"
    :max="10">
  </el-input-number>
</template>

<script>
export default {
  data () {
    return {
      num: 1,
      step: 0,
      precision: 1
    };
  },
  methods: {
    handleChange(value) {
      console.log(value);
    }
  }
}
</script>
```

### InputNumber Attributes

| Attribute            | Type    | Default     | Values      | Description              |
| -------------------- |:-------:|:-----------:| ----------- | ------------------------ |
| `value/v-model`      | Number  | 0           |             | Binding Value            |
| `min`                | Number  | `-Infinity` | -           | Minimum Allowed Value    |
| `max`                | Number  | `Infinity`  | -           | Maximum Allowed Value    |
| `step`               | Number  | 1           | -           | Incremental Step         |
| `step-stricly`       | Number  | false       | -           | Input Multiple of Step   |
| `precision`          | Number  | -           | -           | Precision Input Value    |
| `size`               | String  | -           | large/small | Size of Component        |
| `disabled`           | Boolean | false       | -           | Component Disabled       |
| `controls`           | Boolean | true        | -           | Enable Controls Button   |
| `controls-precision` | String  | -           | right       | Position Control Buttons |
| `name`               | String  | -           | -           | Name Native              |
| `label`              | String  | -           | -           | Label Text               |
| `placeholder`        | String  | -           | -           | Placeholder Text         |

### InputNumber Events

| Event Name | Parameters             | Description                 |
| ---------- | ---------------------- | --------------------------- |
| `change`   | currentValue, oldValue | Triggers when Value changes |
| `blur`     | (event: Event)         | Triggers when Input Blurs   |
| `focus`    | (event: Event)         | Triggers when Input Focuses |

### InputNumber Methods

| Method   | Parameters | Description                      |
| -------- | ---------- | -------------------------------- |
| `focus`  | -          | Focus Input Component            |
| `select` | -          | Select the Text in Input Element |

---

## Select

[Element UI - Select](https://element.eleme.io/#/en-US/component/select)

Usage: `<el-select>`

```html
<template>
  <el-select v-model="selectable" placeholder="Select...">
    <el-option
      v-for="item in options"
      :key="item.value"
      :label="item.label"
      :value="item.value">
    </el-option>
  </el-select>

  <!-- `el-option-group` -->
  <el-select v-model="selectable" placeholder="Select...">
    <el-option-group
      v-for="group in cities"
      :key="group.label"
      :label="group.label">
      <el-option
        v-for="item in group.options"
        :key="item.value"
        :label="item.label"
        :value="item.value">
      </el-option>
    </el-option-group>
  </el-select>
</template>

<script>
export default {
  data () {
    return {
      options: [
        { value: 1, label: 'One' },
        { value: 2, label: 'Two' },
        { value: 3, label: 'Three' },
        { value: 4, label: 'Four' },
      ],
      cities: [
        {
          label: 'Florida',
          options: [
            { value: 'miami', label: 'Miami' },
            { value: 'orlando', label: 'Orlando' }
          ]
        },
        {
          label: 'New York',
          options: [
            { value: 'manhattan', label: 'Manhattan' },
            { value: 'brooklyn', label: 'Brooklyn' }
          ]
        }
      ]
    };
  }
}
</script>
```

### Select Attributes

| Attribute               | Type                  | Default          | Values           | Description                 |
| ----------------------- |:---------------------:|:----------------:| ---------------- | --------------------------- |
| `value/v-model`         | Boolean/String/Number | -                | -                | Binding Value               |
| `multiple`              | Boolean               | false            | -                | Multiple Select             |
| `disabled`              | Boolean               | false            | -                | Select Disabled             |
| `value-key`             | String                | value            | -                | Identity Key-name for Value |
| `size`                  | String                | -                | large/small/mini | Size of Input               |
| `clearable`             | Boolean               | false            | -                | Clear Select                |
| `collapse-tags`         | Boolean               | false            | -                | Collapse Tags with Multiple |
| `multiple-limit`        | Number                | 0                | -                | Max Options Selectable      |
| `name`                  | String                | -                | -                | Name Native                 |
| `autocomplete`          | String                | off              | -                | Autocomplete Native         |
| `placeholder`           | String                | Select           | -                | Placeholder Text            |
| `filterable`            | Boolean               | false            | -                | Select Filterable           |
| `allow-create`          | Boolean               | false            | -                | Create New Items            |
| `filter-method`         | Function              | -                | -                | Custom Filter Method        |
| `remote`                | Boolean               | false            | -                | Remote Data Fetch           |
| `remote-method`         | Function              | -                | -                | Custom Remote Search Method |
| `loading`               | Boolean               | false            | -                | Select loading Data         |
| `loading-text`          | String                | Loading          | -                | Loading Display Text        |
| `no-match-text`         | String                | No Matching Data | -                | Empty Match Display Text    |
| `no-data-text`          | String                | No Data          | -                | Empty Results Display Text  |
| `popper-class`          | String                | -                | -                | Custom Class for Dropdown   |
| `reserve-keyword`       | Boolean               | false            | -                | Reserve Keyword             |
| `default-first-option`  | Boolean               | false            | -                | Select First Matching Item  |
| `popper-append-to-body` | Boolean               | true             | -                | Append Popper Menu to Body  |
| `automatic-dropdown`    | Boolean               | false            | -                | Option Menu Popup           |

### Select Events

| Event Name      | Parameters                   | Description                    |
| --------------- | ---------------------------- | ------------------------------ |
| `change`        | Selected Value               | Triggers when Value changes    |
| `visble-change` | Appear: true - Hidden: false | Triggers when Dropdown Appears |
| `remove-tag`    | Removed Tag Value            | Triggers when Tag removed      |
| `clear`         | -                            | Triggers when Clear clicked    |
| `blur`          | (event: Event)               | Triggers when Input blurs      |
| `focus`         | (event: Event)               | Triggers when Input Focuses    |

### Select Slots

| Name     | Description              |
| -------- | ------------------------ |
| `-`      | Option component list    |
| `prefix` | Content as Select prefix |
| `empty`  | Content when No Options  |

### Select Methods

| Method  | Parameters | Description           |
| ------- | ---------- | --------------------- |
| `focus` | -          | Focus Input Component |
| `blur`  | -          | Blur Input Component  |

### Option Group Attributes

| Attribute  | Type    | Default | Values | Description         |
| ---------- |:-------:|:-------:| ------ | ------------------- |
| `label`    | String  | -       | -      | Name of Group       |
| `disabled` | Boolean | false   | -      | Disable all options |

### Option Attributes

| Attribute  | Type                 | Default | Values | Description     |
| ---------- |:--------------------:|:-------:| ------ | --------------- |
| `value`    | String/Number/Object | -       | -      | Value of option |
| `label`    | String/Number        | -       | -      | Label of option |
| `disabled` | Boolean              | false   | -      | Option disabled |

---

## Cascader

[Element UI - Cascader](https://element.eleme.io/#/en-US/component/cascader)

Usage: `<el-cascader>`

***Cascader***
```html
<template>
  <el-cascader
    v-model="value"
    :options="options"
    @change="handleChange">
  </el-cascader>
</template>

<script>
export default {
  data () {
    return {
      value: [],
      options: [{
        value: 'guide',
        label: 'Guide',
        children: [
          {
            value: 'disciplines',
            label: 'Disciplines',
            children: [
              { value: 'consistency', label: 'Consistency' },
              { value: 'feedback', label: 'Feedback' }
            ]
          },
          {
            value: 'navigation',
            label: 'Navigation',
            children: [
              { value: 'side-nav', label: 'Side Navigation' },
              { value: 'top-nav', label: 'Top Navigation' }
            ]
          }
        ]
      }]
    };
  }
}
</script>
```

Usage: `<el->`

***CascaderPanel***
```html
<template>
</template>

<script>
export default {
  data () {
    return {

    };
  }
}
</script>
```

### Cascader Attributes

| Attribute         | Type                    | Default | Values            | Description                    |
| ----------------- |:-----------------------:|:-------:| ----------------- | ------------------------------ |
| `value/v-model`   | -                       | -       | -                 | Binding Value                  |
| `options`         | Array                   | -       | -                 | Data of Options                |
| `props`           | Object                  | -       | -                 | Configuration Options          |
| `size`            | String                  | -       | medium/small/mini | Size of Input                  |
| `placeholder`     | String                  | Select  | -                 | Placeholder Text               |
| `disabled`        | Boolean                 | false   | -                 | Cascader disabled              |
| `clearable`       | Boolean                 | false   | -                 | Clear Cascader                 |
| `show-all-levels` | Boolean                 | true    | -                 | All Levels of Value            |
| `collapse-tags`   | Boolean                 | false   | -                 | Collapse Tags in Multiple      |
| `separator`       | String                  | '/'     | -                 | Option Label Separator         |
| `filterable`      | Boolean                 | -       | -                 | Searchable Options             |
| `filter-method`   | Function(node, keyword) | -       | -                 | Custom Function                |
| `debounce`        | Number                  | 300     | -                 | Debounce delay                 |
| `before-filter`   | Function(value)         | -       | -                 | Hook Function before Filtering |
| `popper-class`    | String                  | -       | -                 | Custom Dropdown Class Name     |

### Cascader Events

| Event Name       | Parameters                   | Description                          |
| ---------------- | ---------------------------- | ------------------------------------ |
| `change`         | Value                        | Triggers when Binding value changes  |
| `expand-change`  | Array of Parent Nodes        | Triggers when Expand option changes  |
| `blur`           | (event: Event)               | Triggers when Cascader blurs         |
| `focus`          | (event: Event)               | Triggers when Cascader focuses       |
| `visible-change` | appear: true - hidden: false | Triggers when Dropdown Appears       |
| `remove-tag`     | Value of removed Tag         | Triggers when Remove Tag in Multiple |

### Cascader Slots

| Name    | Description                                |
| ------- | ------------------------------------------ |
| `-`     | Custom Content. Parameter `{ node, data }` |
| `empty` | Content when No Matching options           |

### Cascader Methods
| Method            | Parameters                | Description                |
| ----------------- | ------------------------- | -------------------------- |
| `getCheckedNodes` | (leafOnly) default: false | Get Array of Selected Node |

### CascaderPanel Attributes

| Attribute       | Type   | Default | Values | Description           |
| --------------- |:------:|:-------:| ------ | --------------------- |
| `value/v-model` | -      | -       | -      | Binding Value         |
| `options`       | Array  | -       | -      | Data of Options       |
| `props`         | Object | -       | -      | Configuration Options |

### CascaderPanel Events

| Event Name      | Parameters            | Description                         |
| --------------- | --------------------- | ----------------------------------- |
| `change`        | Value                 | Triggers when Binding value changes |
| `expand-change` | Array of Parent Nodes | Triggers when Expand option changes |

### CascaderPanel Slots

| Name | Description                                 |
| ---- | ------------------------------------------- |
| `-`  | Custom Content. Parameters `{ node, data }` |

### CascaderPanel Methods

| Method              | Parameters                | Description                     |
| ------------------- | ------------------------- | ------------------------------- |
| `getCheckedNodes`   | (leafOnly) default: false | Array of current selected nodes |
| `clearCheckedNodes` | -                         | Clear checked nodes             |

### Props

| Attribute       | Type                    | Default    | Values      | Description                                    |
| --------------- |:-----------------------:|:----------:| ----------- | ---------------------------------------------- |
| `expandTrigger` | String                  | `click`    | click/hover | Trigger Expanded Options                       |
| `multiple`      | Boolean                 | false      | -           | Multiple Select Enabled                        |
| `checkStrictly` | Boolean                 | false      | -           | Checked State does not affect Parents/Children |
| `emitPath`      | Boolean                 | true       | -           | Emit -> Array: true / Value: false             |
| `lazy`          | Boolean                 | false      | -           | Dynamic Load Child Nodes                       |
| `lazyLoad`      | Function(node, resolve) | -          | -           | Loading Child Nodes                            |
| `value`         | String                  | `value`    | -           | Specify Key Node Object as Value               |
| `label`         | String                  | `label`    | -           | Specify Key Node Object as Label               |
| `children`      | String                  | `children` | -           | Specify Key Node Object as Children            |
| `disabled`      | String                  | `disabled` | -           | Specify Key Node Object as Disabled            |
| `leaf`          | String                  | `leaf`     | -           | Specify Key Node Object as Leaf Field          |

---

## Switch

[Element UI - Switch](https://element.eleme.io/#/en-US/component/switch)

Usage: `<el-switch>`

```html
<template>
  <el-switch
    v-model="value1">
  </el-switch>

  <!-- Active : Inactive -->
  <el-switch
    v-model="value2"
    active-color="#12ce66"
    inactive-color="#ff4949">
  </el-switch>
</template>

<script>
export default {
  data () {
    return {
      value1: true,
      value2: true
    };
  }
}
</script>
```

### Switch Attributes

| Attribute             | Type                  | Default | Values | Description                 |
| --------------------- |:---------------------:|:-------:| ------ | --------------------------- |
| `value/v-model`       | Boolean/String/Number | -       | -      | Binding Value               |
| `disabled`            | Boolean               | false   | -      | Switch disabled             |
| `width`               | Number                | 40      | -      | Switch width                |
| `active-icon-class`   | String                | -       | -      | Icon Class when `on`        |
| `inactive-icon-class` | String                | -       | -      | Icon Class when `off`       |
| `active-text`         | String                | -       | -      | Text displayed when `on`    |
| `inactive-text`       | String                | -       | -      | Text displayed when `off`   |
| `active-value`        | Boolean/String/Number | true    | -      | Switch value when `on`      |
| `inactive-value`      | Boolean/String/Number | false   | -      | Switch value when `off`     |
| `active-color`        | String                | #409eff | -      | Background color when `on`  |
| `inactice-color`      | String                | #c0ccda | -      | Background color when `off` |
| `name`                | String                | -       | -      | Input name of Switch        |
| `validate-event`      | Boolean               | true    | -      | Trigger Form Validation     |

### Switch Events

| Event Name | Parameters           | Description                 |
| ---------- | -------------------- | --------------------------- |
| `change`   | Value after changing | Triggers when value changes |

### Switch Methods

| Method  | Parameters | Description            |
| ------- | ---------- | ---------------------- |
| `focus` | -          | Focus Switch Component |

---

## Slider

[Element UI - Slider](https://element.eleme.io/#/en-US/component/slider)

Usage: `<el-slider>`

```html
<template>
  <el-slider v-model="value1"></el-slider>

  <!-- Formatted Value -->
  <el-slider
    v-model="value2"
    :format-tooltip="formatTooltip">
  </el-slider>

  <!-- Step Increments -->
  <el-slider
    v-model="value3"
    :step="10"
    show-stops>
  </el-slider>

  <!-- Integrate Input -->
  <el-slider
    v-model="value4"
    show-input>
  </el-slider>

  <!-- Range -->
  <!-- Binding Value: Array(2) `[1,2]` -->
  <el-slider
    v-model="value5"
    range
    show-stops
    :max="10">
  </el-slider>

  <!-- Vertical -->
  <el-slider
    v-model="value6"
    vertical
    height="200px">
  </el-slider>
</template>

<script>
export default {
  data () {
    return {
      value1: 0,
      value2: 50,
      value3: 0,
      value4: 0,
      value5: [2, 8],
      value6: 0
    };
  },
  methods: {
    formatTooltip(val) {
      return val / 100;
    }
  }
}
</script>
```

### Slider Attributes

| Attribute             | Type            | Default | Values                  | Description                     |
| --------------------- |:---------------:|:-------:| ----------------------- | ------------------------------- |
| `value/v-model`       | Number          | 0       | -                       | Binding Value                   |
| `min`                 | Number          | 0       | -                       | Minimum Value                   |
| `max`                 | Number          | 100     | -                       | Maximum Value                   |
| `disabled`            | Boolean         | false   | -                       | Slider Disabled                 |
| `step`                | Number          | 1       | -                       | Step Size                       |
| `show-input`          | Boolean         | false   | -                       | Display Input Box               |
| `show-input-controls` | Boolean         | true    | -                       | Display Control Buttons         |
| `input-size`          | String          | -       | large/medium/small/mini | Input Box Size                  |
| `show-stops`          | Boolean         | false   | -                       | Display Breakpoints             |
| `show-tooltip`        | Boolean         | true    | -                       | Display Tooltip Value           |
| `format-tooltip`      | Function(value) | -       | -                       | Display Formatted Tooltip Value |
| `range`               | Boolean         | false   | -                       | Select Range                    |
| `vertical`            | Boolean         | false   | -                       | Vertical Slider                 |
| `height`              | String          | -       | -                       | Vertical Slider Height          |
| `label`               | String          | -       | -                       | Screen Reader Label             |
| `debounce`            | Number          | 300     | -                       | Debounce Delay                  |
| `tooltip-class`       | String          | -       | -                       | Custom Class Name               |
| `marks`               | Object          | -       | -                       | Type of Key must be Number      |

### Slider Events

| Event Name | Parameters         | Description                 |
| ---------- | ------------------ | --------------------------- |
| `change`   | Value after Change | Triggers when Value Changes |
| `input`    | Value after Change | Triggers when Data Changes  |

---

## TimePicker

[Element UI - TimePicker](https://element.eleme.io/#/en-US/component/time-picker)

Usage: `<el-time-select>`

```html
<template>
  <el-time-select
    v-model="value1"
    :picker-options="{
      start: '08:30',
      step: '00:15',
      end: '18:30'
    }"
    placeholder="Select Time...">
  </el-time-select>

  <!-- Fixed Time Range -->
  <!-- `endTime` updated after `startTime` changed -->
  <el-time-select
    placeholder="Start time..."
    v-model="startTime"
    :picker-options="{
      start: '08:30',
      step: '00:15',
      end: '18:30'
    }">
  </el-time-select>
  <el-time-select
    placeholder="End time..."
    v-model="endTime"
    :picker-options="{
      start: '08:30',
      step: '00:15',
      end: '18:30',
      minTime: startTime
    }">
  </el-time-select>
</template>

<script>
export default {
  data () {
    return {
      value1: '',
      startTime: '',
      endTime: ''
    };
  }
}
</script>
```

### TimePicker Attributes

| Attribute           | Type                                | Default                | Values            | Description                |
| ------------------- |:-----------------------------------:|:----------------------:| ----------------- | -------------------------- |
| `value/v-model`     | Date(TimePicker)/String(TimeSelect) | -                      | -                 | Binding Value              |
| `readonly`          | Boolean                             | false                  | -                 | Readonly TimePicker        |
| `disabled`          | Boolean                             | false                  | -                 | TimePicker Disabled        |
| `editable`          | Boolean                             | true                   | -                 | Input Editable             |
| `clearable`         | Boolean                             | true                   | -                 | Show Clear Button          |
| `size`              | String                              | -                      | medium/small/mini | Input Size                 |
| `placeholder`       | String                              | -                      | -                 | Placeholder (Non-range)    |
| `start-placeholder` | String                              | -                      | -                 | Start Placeholder (range)  |
| `end-placeholder`   | String                              | -                      | -                 | End Placeholder (range)    |
| `is-range`          | Boolean                             | false                  | -                 | Pick Time Range            |
| `arrow-control`     | Boolean                             | false                  | -                 | Pick Time using Arrow Keys |
| `align`             | left/center/right                   | -                      | left              | Alignment                  |
| `popper-class`      | String                              | -                      | -                 | Custom Class Name          |
| `picker-options`    | Object                              | `{}`                   | -                 | Additional Options         |
| `range-separator`   | String                              | `-`                    | -                 | Range Separator            |
| `default-value`     | Date(TimePicker)/String(TimeSelect) | -                      | -                 | Default Date               |
| `value-format`      | String                              | -                      | Date Formats      | TimePicker Formatting      |
| `name`              | String                              | -                      | -                 | Name Native                |
| `prefix-icon`       | String                              | `el-icon-time`         | -                 | Custom Prefix Icon         |
| `clear-icon`        | String                              | `el-icon-circle-close` | -                 | Custom Clear Icon          |

[TimePicker Date Formats](https://element.eleme.io/#/en-US/component/date-picker#date-formats)

### TimePicker Events

| Event Name | Parameters         | Description                 |
| ---------- | ------------------ | --------------------------- |
| `change`   | Binding Value      | Triggers when Confirmation  |
| `blur`     | Component Instance | Triggers when Input Blurs   |
| `focus`    | Component Instance | Triggers when Input Focuses |

### TimePicker Methods

| Method  | Parameters | Description           |
| ------- | ---------- | --------------------- |
| `focus` | -          | Focus Input Component |

### TimePicker Options

| Attribute | Type   | Default | Values | Description           |
| --------- |:------:|:-------:| ------ | --------------------- |
| `start`   | String | 09:00   | -      | Start Time            |
| `end`     | String | 18:00   | -      | End Time              |
| `step`    | String | 00:30   | -      | Time Step             |
| `minTime` | String | 00:00   | -      | Minimum Accepted Time |
| `maxTime` | String | -       | -      | Maximum Accepted Time |

### TimePicker Select Options

| Attribute         | Type         | Default  | Values                                         | Description           |
| ----------------- |:------------:|:--------:| ---------------------------------------------- | --------------------- |
| `selectableRange` | String/Array | -        | -                                              | Available Time Range  |
| `format`          | String       | HH:mm:ss | hour `HH`, minute `mm`, second `ss`, AM/PM `A` | Format for TimePicker |

---

## DatePicker

[Element UI - DatePicker](https://element.eleme.io/#/en-US/component/date-picker)

Usage: `<el-date-picker>`

```html
<template>
  <el-date-picker
    v-model="value1"
    type="date"
    placeholder="Pick a Date...">
  </el-date-picker>

  <!-- Picker w. Options -->
  <el-date-picker
    v-model="value2"
    type="date"
    placeholder="Pick a Date..."
    :picker-options="pickerOptions">
  </el-date-picker>
</template>

<script>
export default {
  data () {
    return {
      value1: '',
      value2: '',
      pickerOptions: {
        disabledDate(time) { return time.getTime() > Date.now(); },
        shortcuts: [
          {
            text: 'Today',
            onClick(picker) { picker.$emit('pick', new Date()); }
          },
          {
            text: 'Yesterday',
            onClick(picker) {
              const date = new Date();
              date.setTime(date.getTime() - 3600 * 1000 * 24);
              picker.$emit('pick', date);
            }
          },
          {
            text: 'A Week Ago',
            onClick(picker) {
              const date = new Date();
              date.setTime(date.getTime() - 3600 * 1000 * 24 * 7);
              picker.$emit('pick', date);
            }
          }
        ]
      }
    };
  }
}
</script>
```

### DatePicker Attributes

| Attribute           | Type                                    | Default                | Values                         | Description |
| ------------------- |:---------------------------------------:|:----------------------:| ------------------------------ | ----------- |
| `value/v-model`     | Date(DatePicker)/Array(DateRangePicker) | -                      | -                              |
| `readonly`          | Boolean                                 | false                  | -                              |
| `disabled`          | Boolean                                 | false                  | -                              |
| `size`              | String                                  | -                      | large/small/mini               |
| `editable`          | Boolean                                 | true                   | -                              |
| `clearable`         | Boolean                                 | true                   | -                              |
| `placeholder`       | String                                  | -                      | -                              |
| `start-placeholder` | String                                  | -                      | -                              |
| `end-placeholder`   | String                                  | -                      | -                              |
| `type`              | String                                  | Date                   | Date Types                     |
| `format`            | String                                  | yyyy-MM-dd             | Date Formats                   |
| `align`             | left/center/right                       | -                      | left                           |
| `popper-class`      | String                                  | -                      | -                              |
| `picker-options`    | Object                                  | `{}`                   | -                              |
| `range-separator`   | String                                  | `-`                    | -                              |
| `default-value`     | Date                                    | -                      | Any accepted by `new Date()`   |
| `default-time`      | String[]                                | -                      | Array ['hh-mm-ss', 'hh-mm-ss'] |
| `value-format`      | String                                  | -                      | Date Formats                   |
| `name`              | String                                  | -                      | -                              |
| `unlink-panels`     | Boolean                                 | false                  | -                              |
| `prefix-icon`       | String                                  | `el-icon-date`         | -                              |
| `clear-icon`        | String                                  | `el-icon-circle-close` | -                              |
| `validate-event`    | Boolean                                 | true                   | -                              |

### DatePicker Events

| Event Name | Parameters | Description |
| ---------- | ---------- | ----------- |
|

### DatePicker Slots

| Name | Description                                 |
| ---- | ------------------------------------------- |
| `-`  | Custom Content. Parameters `{ node, data }` |

### DatePicker Methods

| Method | Parameters | Description |
| ------ | ---------- | ----------- |
|

### DatePicker Options

| Attribute | Type | Default | Values | Description |
| --------- |:----:|:-------:| ------ | ----------- |
|

### DatePicker Shortcuts

| Attribute | Type | Default | Values | Description |
| --------- |:----:|:-------:| ------ | ----------- |
|


### Date Formats
| Format      | Label                | Example       | Description                                            |
|:-----------:|:--------------------:| ------------- | ------------------------------------------------------ |
| `yyyy`      | Year                 | 2017          | -                                                      |
| `M`         | Month                | 1             | No leading `0`                                         |
| `MM`        | Month                | 01            | -                                                      |
| `MMM`       | Month                | Jan           | -                                                      |
| `MMMM`      | Month                | January       | -                                                      |
| `W`         | Week                 | 1             | Week Picker - No leading `0`                           |
| `WW`        | Week                 | 01            | Week Picker                                            |
| `d`         | Day                  | 2             | No leading `0`                                         |
| `dd`        | Day                  | 02            | -                                                      |
| `H`         | Hour                 | 3             | 24-hr Clock - No leading `0`                           |
| `HH`        | Hour                 | 03            | 24-hr Clock                                            |
| `h`         | Hour                 | 3             | 12-hr Clock - No leading `0` - Must include `A` or `a` |
| `hh`        | Hour                 | 03            | 12-hr Clock - Must include `A` or `a`                  |
| `m`         | Minute               | 4             | No leading `0`                                         |
| `mm`        | Minute               | 04            | -                                                      |
| `s`         | Second               | 5             | No leading `0`                                         |
| `ss`        | Second               | 05            | -                                                      |
| `A`         | AM/PM                | AM            | Uppercase                                              |
| `a`         | am/pm                | am            | Lowercase                                              |
| `timestamp` | JS Timestamp         | 1483326245000 | `value-format`                                         |
| `[MM]`      | No escape characters | MM            | Escape Characters - Wrap in `[A]` Brackets             |

---

## DateTimePicker

[Element UI - DateTimePicker](https://element.eleme.io/#/en-US/component/datetime-picker)

Usage: `<el->`

```html
<template>
</template>

<script>
export default {
  data () {
    return {

    };
  }
}
</script>
```

### DateTimePicker Attributes

| Attribute | Type | Default | Values | Description |
| --------- |:----:|:-------:| ------ | ----------- |
|

### DateTimePicker Events

| Event Name | Parameters | Description |
| ---------- | ---------- | ----------- |
|

---

## Upload

[Element UI - Upload](https://element.eleme.io/#/en-US/component/upload)

Usage: `<el->`

```html
<template>
</template>

<script>
export default {
  data () {
    return {

    };
  }
}
</script>
```

### Upload Attributes

| Attribute | Type | Default | Values | Description |
| --------- |:----:|:-------:| ------ | ----------- |
|

### Upload Events

| Event Name | Parameters | Description |
| ---------- | ---------- | ----------- |
|

---

## Rate

[Element UI - Rate](https://element.eleme.io/#/en-US/component/rate)

Usage: `<el->`

```html
<template>
</template>

<script>
export default {
  data () {
    return {

    };
  }
}
</script>
```

### Rate Attributes

| Attribute | Type | Default | Values | Description |
| --------- |:----:|:-------:| ------ | ----------- |
|

### Rate Events

| Event Name | Parameters | Description |
| ---------- | ---------- | ----------- |
|

---

## ColorPicker

[Element UI - ColorPicker](https://element.eleme.io/#/en-US/component/color-picker)

Usage: `<el->`

```html
<template>
</template>

<script>
export default {
  data () {
    return {

    };
  }
}
</script>
```

### ColorPicker Attributes

| Attribute | Type | Default | Values | Description |
| --------- |:----:|:-------:| ------ | ----------- |
|

### ColorPicker Events

| Event Name | Parameters | Description |
| ---------- | ---------- | ----------- |
|

---

## Transfer

[Element UI - Transfer](https://element.eleme.io/#/en-US/component/transfer)

Usage: `<el->`

```html
<template>
</template>

<script>
export default {
  data () {
    return {

    };
  }
}
</script>
```

### Transfer Attributes

| Attribute | Type | Default | Values | Description |
| --------- |:----:|:-------:| ------ | ----------- |
|

### Transfer Events

| Event Name | Parameters | Description |
| ---------- | ---------- | ----------- |
|

---

## Form

[Element UI - Form](https://element.eleme.io/#/en-US/component/form)

Usage: `<el->`

```html
<template>
</template>

<script>
export default {
  data () {
    return {

    };
  }
}
</script>
```

### Form Attributes

| Attribute | Type | Default | Values | Description |
| --------- |:----:|:-------:| ------ | ----------- |
|

### Form Events

| Event Name | Parameters | Description |
| ---------- | ---------- | ----------- |
|
