# blazor-client-performance
This repository aims to investigate how certain features of the component model in blazor affect the performance in wasm scenarios

To test the performance of each Grid/Table, click on a row and observe the latency before it's marked as selected by the background-color style. Each component will calculate its latency and display the time elapsed in the console.

Ex:
```
WASM: Refresh Time 600
```

# Sample
These are some times we recorded with our tests:

### plain-table-component
Components use only basic HTML/Razor and no additional framework features.
```
WASM: Refresh Time 600
```
### cascadingvalue-table-component
Components use CascadingValue for parent > child support.
```
WASM: Refresh Time 1390
```
### parameters-table-component
Components use basic [parameter] attributes to share values.
```
WASM: Refresh Time 964
```
### attributes-table-component
Components use splat attributes to share values.
```
WASM: Refresh Time 908
```
### combined-table-component
Components use splat attributes and CascadingValues to share values. This combination seems to compound the latency problem.
```
WASM: Refresh Time 3219
```
### telerik-grid 2.7.x (optimized *not available to public / not included in demo*)
Note: Time below is not reproduceable in this demo.
```
WASM: Refresh Time 964
```
### telerik-grid 2.7.1 (non-optimized current public version)
Note: Time below is likely twice what is reported due to how calculations are performed in the demo.
```
WASM: Refresh Time 8500+
```
