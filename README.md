# vuejs-components
vuejs custom components  
직접 만든 유용한 컴포넌트 모음

## Spec, Reference

* vuejs
* element-ui
* vue-element-admin

## Components

* [Date Picker](https://github.com/deepweller/vuejs-components/tree/master/components/DatePicker)

## Usage

- Install element-ui

```shell script
npm i element-ui -S
```

- main.js

```javascript
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