# Element UI

[Element UI Documentation](https://element.eleme.io/#/en-US)

## Installation
NPM
```bash
$ npm i element-ui -S
```

CDN
```html
<!-- import CSS -->
<link rel="stylesheet" href="https://unpkg.com/element-ui/lib/theme-chalk/index.css">
<!-- import JavaScript -->
<script src="https://unpkg.com/element-ui/lib/index.js"></script>
```

## Import
```js
import Vue from 'vue';
import ElementUI from 'element-ui';
import 'element-ui/lib/theme-chalk/index.css';
import App from './App.vue';

Vue.use(ElementUI);

new Vue({
  el: '#app',
  render: h => h(App)
});
```

## Components
```js
import Vue from 'vue';
import {
  Pagination,
  Dialog,
  Autocomplete,
  Dropdown,
  DropdownMenu,
  DropdownItem,
  Menu,
  Submenu,
  MenuItem,
  MenuItemGroup,
  Input,
  InputNumber,
  Radio,
  RadioGroup,
  RadioButton,
  Checkbox,
  CheckboxButton,
  CheckboxGroup,
  Switch,
  Select,
  Option,
  OptionGroup,
  Button,
  ButtonGroup,
  Table,
  TableColumn,
  DatePicker,
  TimeSelect,
  TimePicker,
  Popover,
  Tooltip,
  Breadcrumb,
  BreadcrumbItem,
  Form,
  FormItem,
  Tabs,
  TabPane,
  Tag,
  Tree,
  Alert,
  Slider,
  Icon,
  Row,
  Col,
  Upload,
  Progress,
  Spinner,
  Badge,
  Card,
  Rate,
  Steps,
  Step,
  Carousel,
  CarouselItem,
  Collapse,
  CollapseItem,
  Cascader,
  ColorPicker,
  Transfer,
  Container,
  Header,
  Aside,
  Main,
  Footer,
  Timeline,
  TimelineItem,
  Link,
  Divider,
  Image,
  Calendar,
  Backtop,
  PageHeader,
  CascaderPanel,
  Loading,
  MessageBox,
  Message,
  Notification
} from 'element-ui';

Vue.use(Pagination);
Vue.use(Dialog);
Vue.use(Autocomplete);
Vue.use(Dropdown);
Vue.use(DropdownMenu);
Vue.use(DropdownItem);
Vue.use(Menu);
Vue.use(Submenu);
Vue.use(MenuItem);
Vue.use(MenuItemGroup);
Vue.use(Input);
Vue.use(InputNumber);
Vue.use(Radio);
Vue.use(RadioGroup);
Vue.use(RadioButton);
Vue.use(Checkbox);
Vue.use(CheckboxButton);
Vue.use(CheckboxGroup);
Vue.use(Switch);
Vue.use(Select);
Vue.use(Option);
Vue.use(OptionGroup);
Vue.use(Button);
Vue.use(ButtonGroup);
Vue.use(Table);
Vue.use(TableColumn);
Vue.use(DatePicker);
Vue.use(TimeSelect);
Vue.use(TimePicker);
Vue.use(Popover);
Vue.use(Tooltip);
Vue.use(Breadcrumb);
Vue.use(BreadcrumbItem);
Vue.use(Form);
Vue.use(FormItem);
Vue.use(Tabs);
Vue.use(TabPane);
Vue.use(Tag);
Vue.use(Tree);
Vue.use(Alert);
Vue.use(Slider);
Vue.use(Icon);
Vue.use(Row);
Vue.use(Col);
Vue.use(Upload);
Vue.use(Progress);
Vue.use(Spinner);
Vue.use(Badge);
Vue.use(Card);
Vue.use(Rate);
Vue.use(Steps);
Vue.use(Step);
Vue.use(Carousel);
Vue.use(CarouselItem);
Vue.use(Collapse);
Vue.use(CollapseItem);
Vue.use(Cascader);
Vue.use(ColorPicker);
Vue.use(Transfer);
Vue.use(Container);
Vue.use(Header);
Vue.use(Aside);
Vue.use(Main);
Vue.use(Footer);
Vue.use(Timeline);
Vue.use(TimelineItem);
Vue.use(Link);
Vue.use(Divider);
Vue.use(Image);
Vue.use(Calendar);
Vue.use(Backtop);
Vue.use(PageHeader);
Vue.use(CascaderPanel);

Vue.use(Loading.directive);

Vue.prototype.$loading = Loading.service;
Vue.prototype.$msgbox = MessageBox;
Vue.prototype.$alert = MessageBox.alert;
Vue.prototype.$confirm = MessageBox.confirm;
Vue.prototype.$prompt = MessageBox.prompt;
Vue.prototype.$notify = Notification;
Vue.prototype.$message = Message;
```

## Components: Basic

### Layout

Row Attributes: `<el-row>`

| Attribute | Type   | Default | Values                                      | Description        |
| --------- |:------:|:-------:| ------------------------------------------- | ------------------ |
| `gutter`  | Number | 0       | -                                           | Grid Spacing       |
| `type`    | String | -       | -                                           | Layout Mode        |
| `justify` | String | start   | start/end/center/space-around/space-between | Horizontal Align   |
| `align`   | String | top     | top/middle/bottom                           | Vertical Align     |
| `tag`     | String | div     | *                                           | Custom Element Tag |

Column Attributes: `<el-col>`

| Attribute | Type          | Default | Values | Description          |
| --------- |:-------------:|:-------:| ------ | -------------------- |
| `span`    | Number        | 24      | -      | Column Grid Span     |
| `offset`  | Number        | 0       | -      | Left Grid Spacing    |
| `push`    | Number        | 0       | -      | Right-side Grid Move |
| `pull`    | Number        | 0       | -      | Left-side Grid Move  |
| `xs`      | Number/Object | -       | -      | <768px Columns       |
| `sm`      | Number/Object | -       | -      | >=768px Columns      |
| `md`      | Number/Object | -       | -      | >=992px Columns      |
| `lg`      | Number/Object | -       | -      | >=1200px Columns     |
| `xl`      | Number/Object | -       | -      | >=1920px Columns     |
| `tag`     | Number/Object | div     | *      | Custom Element Tag   |

Hidden Utility Classes:

  * `hidden-xs-only` - Hide when on extra small viewports only
  * `hidden-sm-only` - Hide when on small viewports and down
  * `hidden-sm-and-down` - Hide when on small viewports and down
  * `hidden-sm-and-up` - Hide when on small viewports and up
  * `hidden-md-only` - Hide when on medium viewports only
  * `hidden-md-and-down` - Hide when on medium viewports and down
  * `hidden-md-and-up` - Hide when on medium viewports and up
  * `hidden-lg-only` - Hide when on large viewports only
  * `hidden-lg-and-down` - Hide when on large viewports and down
  * `hidden-lg-and-up` - Hide when on large viewports and up
  * `hidden-xl-only` - Hide when on extra large viewports only

---

### Layout Container

Container Components:
  * `<el-container>`
  * `<el-header>`
  * `<el-aside>`
  * `<el-main>`
  * `<el-footer`

Container Attributes

| Attribute   | Type   | Default                         | Values              | Description      |
| ----------- |:------:|:-------------------------------:| ------------------- | ---------------- |
| `direction` | String | Horizontal/Vertical when Nested | horizontal/vertical | Layout Direction |

Header Attributes

| Attribute | Type   | Default | Values | Description          |
| --------- |:------:|:-------:| ------ | -------------------- |
| `height`  | String | 60px    | -      | Height of the Header |

Aside Attributes

| Attribute | Type   | Default | Values | Description           |
| --------- |:------:|:-------:| ------ | --------------------- |
| `width`   | String | 300px   | -      | Width of Side Section |

Footer Attributes

| Attribute | Type   | Default | Values | Description          |
| --------- |:------:|:-------:| ------ | -------------------- |
| `height`  | String | 60px    | -      | Height of the Footer |

---

### Color

---

### Typography

---

### Border

---

### Icon

Usage: `el-icon-iconName`

---

### Button

Usage: `<el-button>`

| Attribute     | Type    | Default | Values                                   | Description        |
| ------------- |:-------:|:-------:| ---------------------------------------- | ------------------ |
| `size`        | String  | -       | medium/small/mini                        | Button Size        |
| `type`        | String  | -       | primary/success/warning/danger/info/text | Button Type        |
| `plain`       | Boolean | false   | -                                        | Plain Type         |
| `round`       | Boolean | false   | -                                        | Round Type         |
| `circle`      | Boolean | false   | -                                        | Circle Type        |
| `loading`     | Boolean | false   | -                                        | Loading Action     |
| `disabled`    | Boolean | false   | -                                        | Disabled Action    |
| `icon`        | String  | -       | -                                        | Icon ClassName     |
| `autofocus`   | Boolean | false   | -                                        | Autofocus Action   |
| `native-type` | String  | button  | button/submit/reset                      | Button Type Native |

---

### Link

Usage: `<el-link>`

| Attribute   | Type    | Default | Values                              | Description         |
| ----------- |:-------:|:-------:| ----------------------------------- | ------------------- |
| `type`      | String  | default | primary/success/warning/danger/info | Type                |
| `underline` | Boolean | true    | -                                   | Underline Style     |
| `disabled`  | Boolean | false   | -                                   | Disabled Action     |
| `href`      | String  | -       | -                                   | Hyperlink Reference |
| `icon`      | String  | -       | -                                   | Icon ClassName      |

---

## Components: Form

### Radio

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

Radio Attributes

| Attribute       | Type                  | Default | Values            | Description      |
| --------------- |:---------------------:|:-------:| ----------------- | ---------------- |
| `value/v-model` | String/Number/Boolean | -       | -                 | Binding Value    |
| `label`         | String/Number/Boolean | -       | -                 | Radio Value      |
| `disabled`      | Boolean               | false   | -                 | Radio Disabled   |
| `border`        | Boolean               | false   | -                 | Border for Radio |
| `size`          | String                | -       | medium/small/mini | Radio Size       |
| `name`          | String                | -       | -                 | Native `name`    |

Radio Button Attributes

| Attribute  | Type          | Default | Values | Description    |
| ---------- |:-------------:|:-------:| ------ | -------------- |
| `label`    | String/Number | -       | -      | Radio Value    |
| `disabled` | Boolean       | false   | -      | Radio Disabled |
| `name`     | String        | -       | -      | Native `name`  |

Radio Events

| Event Name | Parameters        | Description                       |
| ---------- | ----------------- | --------------------------------- |
| `change`   | Radio Label Value | Triggers when Bound value changes |

---

### RadioGroup

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

Radio Group Attributes

| Attribute       | Type                  | Default | Values            | Description               |
| --------------- |:---------------------:|:-------:| ----------------- | ------------------------- |
| `value/v-model` | String/Number/Boolean | -       | -                 | Binding Value             |
| `size`          | String                | -       | medium/small/mini | Radio Button Sizes        |
| `disabled`      | Boolean               | false   | -                 | Nested Radios Disabled    |
| `text-color`    | String                | #ffffff | -                 | Font Color when Active    |
| `fill`          | String                | #409eff | -                 | Border and Bg when Active |

Radio Group Events

| Event Name | Parameters        | Description                       |
| ---------- | ----------------- | --------------------------------- |
| `change`   | Radio Label Value | Triggers when Bound value changes |

---

### Checkbox

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

Checkbox Attributes

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

Checkbox Button Attributes

| Attribute       | Type                  | Default | Values            | Description                    |
| --------------- |:---------------------:|:-------:| ----------------- | ------------------------------ |
| `label`         | String/Number/Boolean | -       | -                 | Value of Checkbox in Group     |
| `true-label`    | String/Number/Boolean | -       | -                 | Value of Checkbox if Checked   |
| `false-label`   | String/Number/Boolean | -       | -                 | Value of Checkbox if Unchecked |
| `disabled`      | Boolean               | false   | -                 | Checkbox Disabled              |
| `name`          | String                | -       | -                 | Native `name`                  |
| `checked`       | Boolean               | false   | -                 | If Checkbox Checked            |

Checkbox Events

| Event Name | Parameters    | Description                         |
| ---------- | ------------- | ----------------------------------- |
| `change`   | Updated Value | Triggers when Binding value changes |

### CheckboxGroup

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

Checkbox Group Attributes

| Attribute       | Type    | Default | Values            | Description                |
| --------------- |:-------:|:-------:| ----------------- | -------------------------- |
| `value/v-model` | Array   | -       | -                 | Binding Value              |
| `size`          | String  | -       | medium/small/mini | Checkboxes Size or Border  |
| `disabled`      | Boolean | false   | -                 | Nested Checkboxes Disabled |
| `min`           | Number  | -       | -                 | Minimum Checkbox Checked   |
| `max`           | Number  | -       | -                 | Maximum Checkbox Checked   |
| `text-color`    | String  | #ffffff | -                 | Active Font Color          |
| `fill`          | String  | #409eff | -                 | Border and Bg when Active  |

Checkbox Group Events

| Event Name | Parameters    | Description                         |
| ---------- | ------------- | ----------------------------------- |
| `change`   | Updated Value | Triggers when Binding value changes |

### Input

Usage: `<el-input>`, `<el-autocomplete>`

```html
<template>
  <el-input placeholder="Please type..." v-model="input"></el-input>
  <el-input type="textarea" :rows="2" placeholder="Please type..." v-model="area"></el-input>

  <!-- Use `slot` to distibute & Append/Prepend to Input -->
  <el-input placeholder="Enter URL..." v-model="url">
    <template slot="prepend">https://</template>
  </el-input>

  <!-- Provide input suggestions -->
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

Input Attributes

| Attribute | Type | Default | Values | Description |
| --------- |:----:|:-------:| ------ | ----------- |
|

Input Slots

| Name | Description |
| ---- | ----------- |
|

Input Events

| Event Name | Parameters | Description |
| ---------- | ---------- | ----------- |
|

Input Methods

| Method | Parameters | Description |
| ------ | ---------- | ----------- |
|

Autocomplete Attributes

| Attribute | Type | Default | Values | Description |
| --------- |:----:|:-------:| ------ | ----------- |
|

Autocomplete Slots

| Name | Description |
| ---- | ----------- |
|

Autocomplete Scoped Slots

| Name | Description |
| ---- | ----------- |
|

Autocomplete Events

| Event Name | Parameters | Description |
| ---------- | ---------- | ----------- |
|

Autocomplete Methods

| Method | Parameters | Description |
| ------ | ---------- | ----------- |
|

### InputNumber

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

Attributes

| Attribute | Type | Default | Values | Description |
| --------- |:----:|:-------:| ------ | ----------- |
|

Events

| Event Name | Parameters | Description |
| ---------- | ---------- | ----------- |
|

### Select

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

Attributes

| Attribute | Type | Default | Values | Description |
| --------- |:----:|:-------:| ------ | ----------- |
|

Events

| Event Name | Parameters | Description |
| ---------- | ---------- | ----------- |
|

### Cascader

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

Attributes

| Attribute | Type | Default | Values | Description |
| --------- |:----:|:-------:| ------ | ----------- |
|

Events

| Event Name | Parameters | Description |
| ---------- | ---------- | ----------- |
|

### Switch

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

Attributes

| Attribute | Type | Default | Values | Description |
| --------- |:----:|:-------:| ------ | ----------- |
|

Events

| Event Name | Parameters | Description |
| ---------- | ---------- | ----------- |
|

### Slider

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

Attributes

| Attribute | Type | Default | Values | Description |
| --------- |:----:|:-------:| ------ | ----------- |
|

Events

| Event Name | Parameters | Description |
| ---------- | ---------- | ----------- |
|

### TimePicker

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

Attributes

| Attribute | Type | Default | Values | Description |
| --------- |:----:|:-------:| ------ | ----------- |
|

Events

| Event Name | Parameters | Description |
| ---------- | ---------- | ----------- |
|

### DatePicker

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

Attributes

| Attribute | Type | Default | Values | Description |
| --------- |:----:|:-------:| ------ | ----------- |
|

Events

| Event Name | Parameters | Description |
| ---------- | ---------- | ----------- |
|

### DateTimePicker

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

Attributes

| Attribute | Type | Default | Values | Description |
| --------- |:----:|:-------:| ------ | ----------- |
|

Events

| Event Name | Parameters | Description |
| ---------- | ---------- | ----------- |
|

### Upload

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

Attributes

| Attribute | Type | Default | Values | Description |
| --------- |:----:|:-------:| ------ | ----------- |
|

Events

| Event Name | Parameters | Description |
| ---------- | ---------- | ----------- |
|

### Rate

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

Attributes

| Attribute | Type | Default | Values | Description |
| --------- |:----:|:-------:| ------ | ----------- |
|

Events

| Event Name | Parameters | Description |
| ---------- | ---------- | ----------- |
|

### ColorPicker

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

Attributes

| Attribute | Type | Default | Values | Description |
| --------- |:----:|:-------:| ------ | ----------- |
|

Events

| Event Name | Parameters | Description |
| ---------- | ---------- | ----------- |
|

### Transfer

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

Attributes

| Attribute | Type | Default | Values | Description |
| --------- |:----:|:-------:| ------ | ----------- |
|

Events

| Event Name | Parameters | Description |
| ---------- | ---------- | ----------- |
|

### Form

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

Attributes

| Attribute | Type | Default | Values | Description |
| --------- |:----:|:-------:| ------ | ----------- |
|

Events

| Event Name | Parameters | Description |
| ---------- | ---------- | ----------- |
|
