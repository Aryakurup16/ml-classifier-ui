
````markdown
# ML Classifier UI

ML Classifier is a React front end for a machine learning engine for quickly training image classification models in your browser. Models can be saved with a single command, and the resulting models reused to make image classification predictions.

This package is the UI front end for [`ml-classifier`](https://github.com/thekevinscott/ml-classifier).

## Walkthrough

A walkthrough of the code can be found in the article [Image Classification in the Browser with Javascript](https://thekevinscott.com/image-classification-with-javascript/).


## Getting Started

### Installation

`ml-classifier-ui` can be installed via `yarn` or `npm`:

```bash
yarn add ml-classifier-ui
````

or

```bash
npm install ml-classifier-ui
```

### Quick Start (Code Sandbox)

You can fork a live running version at [codesandbox.io](https://codesandbox.io/s/218po5mzxn).

### Quick Start (Running locally)

Start by instantiating a new MLClassifierUI:

```tsx
import React from 'react';
import ReactDOM from 'react-dom';
import MLClassifierUI from 'ml-classifier-ui';

ReactDOM.render(<MLClassifierUI />, document.getElementById('root'));
```

## API Documentation

`MLClassifierUI` accepts a number of parameters:

* **getMLClassifier** (`Function`) *Optional* - A callback that returns an instance of the underlying `ml-classifier` object. Call this if you want to programmatically call methods like `addData`, `train`, and `predict`. For more information on `ml-classifier`'s API methods, [refer to its documentation](https://github.com/thekevinscott/ml-classifier#api-documentation).
* **methodParams** (`Object`) *Optional* - A set of parameters that will be passed in calls to `ml-classifier`'s methods.
* **uploadFormat** (`string`) *Optional* - A string denoting what type of upload format to accept. Formats can be `flat` or `nested`.
* **imageFormats** (`string[]`) *Optional* - An array of file extensions to accept.
* **showDownload** (`boolean`) *Optional* - A flag denoting whether to show a download button or not. Defaults to true.

`MLClassifierUI` also accepts a number of callbacks that are called on the beginnings and ends of `ml-classifier` functions. [You can view a list of those here](https://github.com/thekevinscott/ml-classifier#parameters).

### `getMLClassifier`

`getMLClassifier` returns an instance of `ml-classifier` for programmatic access.

#### Example

```tsx
<MLClassifierUI
  getMLClassifier={(mlClassifier) => {
    mlClassifier.addData(...);
  }}
/>
```

### `methodParams`

Used to pass custom parameters to the underlying ML methods.

```tsx
<MLClassifierUI
  methodParams={{
    train: {
      epochs: 20,
    },
    evaluate: {
      batchSize: 32,
    },
    save: {},
  }}
/>
```

### `uploadFormat`

Describes the file upload structure:

#### `nested` (folder-based labels)

```
- images/
  - dogs/
    - dog1.jpg
  - cats/
    - cat1.jpg
```

#### `flat` (filename-based labels)

```
- images/
  - dog-1.jpg
  - cat-1.jpg
```

#### Example

```tsx
<MLClassifierUI uploadFormat="nested" />
```

### `imageFormats` (*optional*)

Filter accepted image types.

```tsx
<MLClassifierUI imageFormats={['png', 'jpg']} />
```

## Contributing

Contributions are welcome!

To run the local example:

```bash
yarn watch
```

Written in TypeScript and React.

### Tests

To run tests:

```bash
yarn test
```

## Maintainer

**Arya Kurup**

> This fork is maintained and customized by Arya Kurup.

## License

This project is licensed under the MIT License - see the LICENSE file for details.

```

