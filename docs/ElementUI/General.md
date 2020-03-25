# Element UI - General Components

[Element UI Documentation](https://element.eleme.io/#/en-US)

* Layout
* Layout Container
* Color
* Typography
* Border
* Icon
* Button
* Link

---

## Layout

[Element UI - Layout](https://element.eleme.io/#/en-US/component/layout)

### Row Attributes

Usage: `<el-row>`

| Attribute | Type   | Default | Values                                      | Description        |
| --------- |:------:|:-------:| ------------------------------------------- | ------------------ |
| `gutter`  | Number | 0       | -                                           | Grid Spacing       |
| `type`    | String | -       | -                                           | Layout Mode        |
| `justify` | String | start   | start/end/center/space-around/space-between | Horizontal Align   |
| `align`   | String | top     | top/middle/bottom                           | Vertical Align     |
| `tag`     | String | div     | *                                           | Custom Element Tag |

### Column Attributes

Usage: `<el-col>`

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

### Hidden Utility Classes

| Class Name           | Description                             |
| -------------------- | --------------------------------------- |
| `hidden-xs-only`     | Hide when on extra small viewports only |
| `hidden-sm-only`     | Hide when on small viewports and down   |
| `hidden-sm-and-down` | Hide when on small viewports and down   |
| `hidden-sm-and-up`   | Hide when on small viewports and up     |
| `hidden-md-only`     | Hide when on medium viewports only      |
| `hidden-md-and-down` | Hide when on medium viewports and down  |
| `hidden-md-and-up`   | Hide when on medium viewports and up    |
| `hidden-lg-only`     | Hide when on large viewports only       |
| `hidden-lg-and-down` | Hide when on large viewports and down   |
| `hidden-lg-and-up`   | Hide when on large viewports and up     |
| `hidden-xl-only`     | Hide when on extra large viewports only |

## Layout Container

[Element UI - Layout Container](https://element.eleme.io/#/en-US/component/container)

### Container Components

  * `<el-container>`
  * `<el-header>`
  * `<el-aside>`
  * `<el-main>`
  * `<el-footer`

### Container Attributes

| Attribute   | Type   | Default                         | Values              | Description      |
| ----------- |:------:|:-------------------------------:| ------------------- | ---------------- |
| `direction` | String | Horizontal/Vertical when Nested | horizontal/vertical | Layout Direction |

### Header Attributes

| Attribute | Type   | Default | Values | Description          |
| --------- |:------:|:-------:| ------ | -------------------- |
| `height`  | String | 60px    | -      | Height of the Header |

### Aside Attributes

| Attribute | Type   | Default | Values | Description           |
| --------- |:------:|:-------:| ------ | --------------------- |
| `width`   | String | 300px   | -      | Width of Side Section |

### Footer Attributes

| Attribute | Type   | Default | Values | Description          |
| --------- |:------:|:-------:| ------ | -------------------- |
| `height`  | String | 60px    | -      | Height of the Footer |

## Color

[Element UI - Color](https://element.eleme.io/#/en-US/component/color)

## Typography

[Element UI - Typography](https://element.eleme.io/#/en-US/component/typography)

## Border

[Element UI - Border](https://element.eleme.io/#/en-US/component/border)

## Icon

[Element UI - Icon](https://element.eleme.io/#/en-US/component/icon)

Usage: `el-icon-iconName`

## Button

[Element UI - Button](https://element.eleme.io/#/en-US/component/button)

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

## Link

[Element UI - Link](https://element.eleme.io/#/en-US/component/link)

Usage: `<el-link>`

| Attribute   | Type    | Default | Values                              | Description         |
| ----------- |:-------:|:-------:| ----------------------------------- | ------------------- |
| `type`      | String  | default | primary/success/warning/danger/info | Type                |
| `underline` | Boolean | true    | -                                   | Underline Style     |
| `disabled`  | Boolean | false   | -                                   | Disabled Action     |
| `href`      | String  | -       | -                                   | Hyperlink Reference |
| `icon`      | String  | -       | -                                   | Icon ClassName      |
