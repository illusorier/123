The key step in server side rendering is to render the initial HTML of our component **before** we send it to the client side.

## ReactDOMServer

> The `ReactDOMServer` object enables you to render components to static markup. Typically, it's used on a Node server.

The following methods can be used in both server and browser environments:

- `renderToString`

- `renderToStaticMarkup`

These additional methods depend on 

- `renderToNodeStream`

#### renderToString()

        ReactDOMServer.renderToString(element)
        
Render a React element to its initial HTML.

React will return an HTML string.

#### renderToNodeStream()

### ReactDOM.hydrate

Same as `render()`, but is used to hydrate a container whose HTML contents were rendered by `ReactDOMServer`.

React will attempt to attach event listeners to the existing markup.