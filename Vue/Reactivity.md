One of the core features of Vue.js is it's *reactive data binding system*.

Vue是如何实现数据双向绑定的？

When a Vue instance is created, it adds all the properties found in its `data` object to Vue's **reactivity system**.

Every component instance has a corresponding **watcher** instance, which records any properties "touched" during the component's render as dependencies.

Later on when a dependency's setter is triggered, it notifies the watcher, which in turn causes the component to re-render.

通过getter实现dependency-tracking, setter实现change-notification。

![](../assets/vue-reactivity.png)

Due to the limitation of modern JavaScript (and the abandonment of `Object.observe`), Vue **cannot detect property addition or deletion**.

### Async Update Queue

下一个问题就是，Vue在什么时候更新DOM？

当任何一个dependency的值发生变化，就更新DOM可能会造成严重的性能问题。

例如一个component中，两个dependency存在依赖关系，没有必要再一个dependency的值发生变化时就更新DOM。

Vue performs DOM updates **asynchronously**.