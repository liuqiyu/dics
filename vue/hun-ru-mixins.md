# mixin

作用于将一些复用功能混合到对象中。

## example

> 局部混入

```js
// 定义一个混入对象
const myMixin = {
  created() {
    document.body.classList.add('whiteBg');
  },
  destroyed() {
    document.body.classList.remove('whiteBg');
  },
};
export default myMixin;

import background from './../../mixin/background';
export default {
   mixins: [background],
};
```