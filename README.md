# vue-top

> A simple Vue.js component to scroll your webpage to the top

# Installation

```bash
npm install --save vue-top
```

## Use with Single File Component

### Globally

```js
import VueTop from 'vue-top';

Vue.component('vue-top', VueTop);
```

### Locally

```js
import VueTop from 'vue-top';

export default {
  components: {
    ... ,
    VueTop,
  },
};
```

## Use in Browser

### Include js file in page

```html
<script type="text/javascript" src="unpkg.com/vue-top@1.0.0/dist/vue-top.min.js"></script>
```

### Install as plugin

```js
Vue.use(VueTop);
```

# Usage

```html
<vue-top>
  <!-- Your HTML CODE -->
</vue-top>
```

## Example

```html
<vue-top>
  <i class="fa fa-arrow-up" aria-hidden="true"></i>
</vue-top>
```

```html
<vue-top>
  <img src="path/yourIcon.png"></img>
</vue-top>
```

## Properties

| Option      | Type   | Default | Description                                                                                        |
| ----------- | ------ | ------- | -------------------------------------------------------------------------------------------------- |
| bottom      | String | 30px    | This property will convert to CSS style property which is the distance from bottom of browser edge |
| right       | String | 30px    | This property will convert to CSS style property which is the distance from right of browser edge  |
| speed       | Number | 500     | Scolling speed , the smaller the faster                                                            |
| customStyle | Object | Null    | Define your own style to the component                                                             |
