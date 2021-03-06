# rule-matrix-js
The front end module for rule matrix

## Install

```
npm install --save rule-matrix-js
```

## Usage

```tsx
import { RuleMatrixApp, RuleList, Streams, ConditionalStreams } from 'rule-matrix-js';

const input = null;
const styles: RuleMatrixStyles = {
  flowWidth: 30,
  // mode: 'matrix',
  rectWidth: 45,
  rectHeight: 27,
  color: labelColor,
  displayEvidence: true,
  // displayFidelity: false,
  // displayFlow: false,
  zoomable: true,
};
const model: RuleList = new RuleList(require('./test_data/model.json'));
const streams: Streams = createStreams(require('./test_data/stream.json'));
// const streams: ConditionalStreams = createConditionalStreams(require('./test_data/stream_cond.json'));
// const support: Support | SupportMat = require('./test_data/support.json');
const support: Support | SupportMat = require('./test_data/support_mat.json');
model.support(support);

ReactDOM.render(
  <div>
    <RuleMatrixApp model={model} streams={streams} support={support} styles={styles} input={input} widgets={true}/>
  </div>,
  document.getElementById('root') as HTMLElement
);
```

## Customization

RuleMatrixApp support the following styling (the `styles` prop) options:

  * `transform`: (`string`) The transform css applied to the group element containing the visualization (not affecting the svg);
  * `flowWidth`: (`number`) The width of the data flow on the left of the matrix;
  * `evidenceWidth`: (`number`) The width of the evidence on the right of the matrix;
  * `rectWidth`: (`number`) The width of each rect cell in the matrix;
  * `rectHeight`: (`number`) The height of each rect cell in the matrix;
  * `displayFlow`: (`boolean`) Whether to display the data flow;
  * `displayEvidence`: (`boolean`) Whether to display the evidence;
  * `zoomable`: (`boolean`) Whether the visualization is zoomable or not;
  * `color`: (`ColorType`) A color function, used for color the class labels, the type of the function should be (i: number) => string;
  * `minSupport`: (`number`) The minimum support (in proportion) of a rule (if a rule does not have a enough support, it will be collapsed) default to 0.01;
  * `width`: (`number`) The width of the svg;
  * `height`: (`number`) The height of the svg;

## Development

1. Clone the project to your machine.

2. Run `npm install` to install dependencies. This might take a while

3. Run `npm run start` to start a development server which would watch the changes in code.

4. After changes are made, run `gulp test` to build a test distribution (in `build` dir). 
   Then run `serve build` to check the vis is rendered properly.

5. Run `gulp` or `npm build` to build the distribution. 
   The development distribution (a module) suitable for a npm package will locate in `dist`.
   The production distribution (a standard alone js module) suitable to include in a `<script>` tag in browser will locate in `build`.

## Known Issues

1. Firefox has trouble using getBBox, which results in the error display of tooltip
