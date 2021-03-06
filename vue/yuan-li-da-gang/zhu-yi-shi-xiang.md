# vue需要注意的事项

### 1、组件里面，data必须是一个函数

类比引用数据类型Object是引用数据类型, 每个组件的data 都是内存的同一个地址,一个数据改变了其他也改变了;

那么用什么方法可以使每个组件的data相互独立,不受影响呢?

当一个组件被定义，data 必须声明为返回一个初始数据对象的函数，因为组件可能被用来创建多个实例。如果 data 仍然是一个纯粹的对象，则所有的实例将共享引用同一个数据对象！通过提供 data 函数，每次创建一个新实例后，我们能够调用 data 函数，从而返回初始数据的一个全新副本数据对象。

* 方式一： 在Vue实例中的data

`data: { a: 1,b: 2 }`

* 方式二： 方式二，在组件中的data

```
data: function(){
    return { a: 1,b: 2 }
}
```
我们知道，函数返回值返回一个对象时，每次执行函数都会创建一个新的对象。

方式一的data始终指向固定的对象，所以组件在调用时候**公用一个数据a和数据b**；

而方式二，组件执行时候data每次都创建新的对象，这个对象里面有数据a和数据b。**假如组件被复用了十次，则data里面的对象就被创建了十次，我们更新一个组件的a或b的值，并不会影响其他组件的a和b。**

### 2、使用`$set`

* `this.$set(this.userProfile, 'age', '12');`

* `this.someObject = Object.assign({}, this.someObject, { a: 1, b: 2 });`

### 3、什么周期详解

* beforeCreate: 实例刚刚创建，组件属性还未出现

* created: 组件实例创建完成，属性被绑定，但是DOM还未完成。`#el`为`Undefined`.

* beforeMount: 模板编译/挂载之前

* mounted: 模板编译/挂载之后

* beforeUpdate: 组件更新之前

* updated: 组件更新之后

* activated: for `keep-alive`,组件被激活时调用

* deactivated: for `keep-alive`,组件被移除时调用

* beforeDestroy: 组件销毁前被调用

* destoryed: 组件销毁后调用

### 4、vue组件通信

* 1、父组件 => 子组件

```js
// parent
<Parent :name="name"></Parent>


// child 
props:['name'],
```

* 2、子组件 => 父组件

子组件通过触发父组件事件传输参数。

```js
// parent
<Parent @changeName="change"></Parent>

// child
this.$emit('changeName', this.name);
```

* 3、子组件向子组件传输数据

vuex


