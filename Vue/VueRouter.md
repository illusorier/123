Use router-link component for navigation.

1. Define route components.

        // These can be imported from other files
        const Foo = { template: '<div>foo</div>' };

2. Define some routes.

Each route should map to a component.

The "component" can either be an actual component

每个路由都对应一个相应的组件，这个组件的template会代替元素`router-view`。 

By injecting the router, we get access to it as `this.$router` as well as the current route as `this.$route` inside of any component:

Real app UIs are usually composed of components 

        <div id="app">
          <router-view></router-view>
        </div>
        
The `<router-view>` here is a top-level outlet.

It renders the component matched by a top level route.

Similarly, a rendered component can also contains its own, nested <router-view>.

To render components 



