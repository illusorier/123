对比模板引擎？

Interpolation markup with embedded expressions is used by AngularJS to provide data-binding to text nodes and attribute values.

        <a ng-href="img/{{username}}.jpg">Hello {{username}}!</a>
        
### How text and attribute bindings work

During the compilation process the **compiler** uses the **$interpolate** service to see if text nodes and element attributes contain interpolation markup with embedded expressions.

If that is the case, the compiler adds an **interpolateDirective** to the node and registers watches on the computed interpolation function, which will update the corresponding text nodes or attribute values as part of the normal digest cycle. 