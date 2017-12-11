UI-Router v1.0 for AngularJS(1.x) introduced the 

In legacy UI-Router (version 0.x.x), views can only be defined using a template 

#### ui-view

The ui-view directive tells $state where to place your templates.

#### Where does the template get inserted?

When  a state is activated, its templates are automatically inserted into the `ui-view` of its parent state's template.

If it's a top-level state 

#### Activating a state

There are three main ways to activate a state:

1. Call `$state.go()`.

在AngularJS中，当应用在不同路由间切换时，会存在这样的一个需求：我们希望某些参数能在路由之间进行传递。

Often, URLs have dynamic parts to them which are called parameters.

There are several options for specifying parameters.

#### Using Parameters without Specifying Them in State URLs

You still can specify what parameters to receive even though the parameters don't appear in the url.