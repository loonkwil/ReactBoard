# React Board

[React](https://facebook.github.io/react) components for rendering the board
for typical board games (like chess, reversi, etc.).

Example usage: https://github.com/loonkwil/reversi

It is written in ES2015 (previously called ES6), so you should use
[Babel](https://babeljs.io) to transpile it (and probably
[webpack](http://webpack.github.io) to load it).

# Install

```bash
npm install https://github.com/loonkwil/ReactBoard.git --save
```

# Usage

```javascript
import React from 'React';
import ReactBoard from 'ReactBoard';

export default class ChessApp extends React.Component {
    constructor(props) {
        super(props);

        // The this.board[0][0] will be in the bottom left corner and
        // the this.board[7][0] in the bottom right
        this.board = [
            [ '♖', '♙', ' ', ' ', ' ', ' ', '♟', '♜' ],
            [ '♘', '♙', ' ', ' ', ' ', ' ', '♟', '♞' ],
            [ '♗', '♙', ' ', ' ', ' ', ' ', '♟', '♝' ],
            [ '♕', '♙', ' ', ' ', ' ', ' ', '♟', '♛' ],
            [ '♔', ' ', ' ', '♙', ' ', ' ', '♟', '♚' ],
            [ '♗', '♙', ' ', ' ', ' ', ' ', '♟', '♝' ],
            [ '♘', '♙', ' ', ' ', ' ', ' ', '♟', '♞' ],
            [ '♖', '♙', ' ', ' ', ' ', ' ', '♟', '♜' ],
        ];

        // https://facebook.github.io/react/blog/2015/01/27/react-v0.13.0-beta-1.html#autobinding
        this.clickHandler = this.clickHandler.bind(this);
    }

    clickHandler({ col, row, cellName, cellValue }) {
        // ...
    }

    render() {
        return React.createElement(ReactBoard, {
            size: [ 8 /* width */, 8 /* height */ ], // or just `size: 8`
            values: this.board,
            highlight: [ [ 4 /* col index */, 3 /* row index */, ] ],
            clickHandler: this.clickHandler,
        });
    }
}
```

# Contribute

## Gulp tasks

List all gulp task: `gulp --tasks`

### Test

Run the linting (jshint, jsonlint) scripts: `gulp lint`, `gulp test` or
`npm test`

### Compile

The `gulp build` (or just `gulp`).

### Release

For compiling the source code, bumping the version number and creating a
release commit, use the `gulp release [--version <version>|-v <version>]` task.

Version could be: major (1.0.0), minor (0.1.0), patch (0.0.2) (this one is the
default), or a specific version number like: 1.2.3 or 1.0.0-alpha

More about the Semantic Versioning: http://semver.org
