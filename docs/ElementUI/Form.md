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

## Cascader

[Element UI - Cascader](https://element.eleme.io/#/en-US/component/cascader)

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

### Cascader Attributes

| Attribute | Type | Default | Values | Description |
| --------- |:----:|:-------:| ------ | ----------- |
|

### Cascader Events

| Event Name | Parameters | Description |
| ---------- | ---------- | ----------- |
|

## Switch

[Element UI - Switch](https://element.eleme.io/#/en-US/component/switch)

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

### Switch Attributes

| Attribute | Type | Default | Values | Description |
| --------- |:----:|:-------:| ------ | ----------- |
|

### Switch Events

| Event Name | Parameters | Description |
| ---------- | ---------- | ----------- |
|

## Slider

[Element UI - Slider](https://element.eleme.io/#/en-US/component/slider)

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

### Slider Attributes

| Attribute | Type | Default | Values | Description |
| --------- |:----:|:-------:| ------ | ----------- |
|

### Slider Events

| Event Name | Parameters | Description |
| ---------- | ---------- | ----------- |
|

## TimePicker

[Element UI - TimePicker](https://element.eleme.io/#/en-US/component/time-picker)

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

### TimePicker Attributes

| Attribute | Type | Default | Values | Description |
| --------- |:----:|:-------:| ------ | ----------- |
|

### TimePicker Events

| Event Name | Parameters | Description |
| ---------- | ---------- | ----------- |
|

## DatePicker

[Element UI - DatePicker](https://element.eleme.io/#/en-US/component/date-picker)

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

### DatePicker Attributes

| Attribute | Type | Default | Values | Description |
| --------- |:----:|:-------:| ------ | ----------- |
|

### DatePicker Events

| Event Name | Parameters | Description |
| ---------- | ---------- | ----------- |
|

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
