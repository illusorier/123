UI-Router: State based routing for client-side web apps.

什么是客户端路由？

Client-side routing: A client-side router updates the browser URL as the user navigates through the single page app. 

在AngularJS的体系当中，`ui.router`是一个第三方module，其中包含了许多组件，如$stateProvider。

UI-Router的几个核心概念：

##### States

什么是state?

A state corresponds to a "place" in the application  in terms of the overall UI and navigation.

A state (via the controller / template / view properties) describes what the UI looks like and does at that place.

从设计的角度上来说，一个feature一个state。

Each feature of an application is defined as a state. 

state的继承体系

UI-Router states are hierarchical.

states can be nested inside other states, forming a tree.

Child states may inherit data and behavior from their parent state.

##### Views

A state defines a feature's UI (and UI behavior) using a view (or multiple views).

A view is a UI component, which is placed into a viewport (`<ui-view>`) when the state is activated.

Views can be **nested** inside other views.

每一个state都可以包含多个view。

Each state can have **multiple named views**, allowing complex layouts.

#### ui-view

The ui-view directive tells $state where to place your templates.

##### Where does the template get inserted?

When  a state is activated, its templates are automatically inserted into the `ui-view` of its parent state's template.

If it's a top-level state, then its parent template is index.html.

##### Activating a state

There are three main ways to activate a state:

1. Call `$state.go()`.
2. Click 
3. Navigate

在AngularJS中，当应用在不同路由间切换时，会存在这样的一个需求：我们希望某些参数能在路由之间进行传递。

Most states in your application will probably have a url associated with them.

## URL Parameters

Often, URLs have dynamic parts to them which are called parameters.

There are several options for specifying parameters.

##### Basic Parameters

A basic parameter looks like this:

        stateProvider
            .state('contacts.detail', {
                url: "/contacts/:contactId",
                templateUrl: 'contacts.detail.html',
                controller: function ($stateParams) {
                    // If we got here from a url of /contacts/42
                    expect($stateParams).toBe({contactId: "42"});
                }
            })
            
Alternatively you can also use curly brackets:

        // identical to previous example
        url: "/contacts/{contactId}" 
          
##### Using Parameters in Links  

#### Using Parameters without Specifying Them in State URLs

You still can specify what parameters to receive even though the parameters don't appear in the url.

### Route to Component

UI-Router v1.0 for AngularJS(1.x) introduced the ability to route directly to AngularJS 1.5+ components. 

In legacy UI-Router (version 0.x.x), views can only be defined using *a template* and *a controller*.

create a component => update the state definition

In the state definition, replace `template / controller` properties with a `component` property which refers to the name of the new component.

        .state('userlist', {
          url: '/users',
          component: 'users', // The component's name
          resolve: {
            users: function(UserService) {
              return UserService.list();
            }
          }
        });  

The process of changing application states is called a **Transition**.

Each Transition has a *from state* and a *to state*.
      
## Transition Hooks

UI-Route Transition Hooks, which allow a developer to tap into the lifecycle events of a Transition.

A transition has numerous lifecycle events.