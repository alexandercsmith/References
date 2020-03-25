# Element UI

[Element UI Documentation](https://element.eleme.io/#/en-US)

* [General Components](../General.md)
  * [Layout](../General.md#layout)
  * [Layout Container](../General.md#layout-container)
  * [Color](../General.md#color)
  * [Typography](../General.md#typography)
  * [Border](../General.md#border)
  * [Icon](../General.md#icon)
  * [Button](../General.md#button)
  * [Link](../General.md#link)
* [Form Components](../Form.md)
  * [Radio](../Form.md#radio)
  * [RadioGroup](../Form.md#radiogroup)
  * [Checkbox](../Form.md#checkbox)
  * [CheckboxGroup](../Form.md#checkboxgroup)
  * [Input](../Form.md#input)
  * [InputNumber](../Form.md#inputnumber)
  * [Select](../Form.md#select)
  * [Cascader](../Form.md#cascader)
  * [Switch](../Form.md#switch)
  * [Slider](../Form.md#slider)
  * [TimePicker](../Form.md#timepicker)
  * [DatePicker](../Form.md#datepicker)
  * [DateTimePicker](../Form.md#datetimepicker)
  * [Upload](../Form.md#upload)
  * [Rate](../Form.md#rate)
  * [ColorPicker](../Form.md#colorpicker)
  * [Transfer](../Form.md#transfer)
  * [Form](../Form.md#form)
* [Data Components](../Data.md)
  * [Table](../Data.md#table)
  * [Tag](../Data.md#tag)
  * [Progress](../Data.md#progress)
  * [Tree](../Data.md#tree)
  * [Pagination](../Data.md#pagination)
  * [Badge](../Data.md#badge)
* [Navigation Components](../Navigation.md)
  * [NavMenu](../Navigation.md#navmenu)
  * [Tabs](../Navigation.md#tabs)
  * [Breadcrumb](../Navigation.md#breadcrumb)
  * [PageHeader](../Navigation.md#pageheader)
  * [Dropdown](../Navigation.md#dropdown)
  * [Steps](../Navigation.md#steps)
* [Notice Components](../Notice.md)
  * [Alert](../Notice.md#alert)
  * [Loading](../Notice.md#loading)
  * [Message](../Notice.md#message)
  * [MessageBox](../Notice.md#messagebox)
  * [Notification](../Notice.md#notification)
* [Misc Components](../Misc.md)
  * [Dialog](../Misc.md#dialog)
  * [Tooltip](../Misc.md#tooltip)
  * [Popover](../Misc.md#popover)
  * [Popconfirm](../Misc.md#popconfirm)
  * [Card](../Misc.md#card)
  * [Carousel](../Misc.md#carousel)
  * [Collapse](../Misc.md#collapse)
  * [Timeline](../Misc.md#timeline)
  * [Divider](../Misc.md#divider)
  * [Calendar](../Misc.md#calendar)
  * [Image](../Misc.md#image)
  * [Backtop](../Misc.md#backtop)
  * [InfiniteScroll](../Misc.md#infinitescroll)
  * [Avatar](../Misc.md#avatar)
  * [Drawer](../Misc.md#drawer)

---

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

---

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

---

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
