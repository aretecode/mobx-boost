# mobx-boost

[![NPM version][mobx-boost-npm-image]][mobx-boost-npm-url]
[![codesandbox][mobx-boost-codesandbox-image]][mobx-boost-codesandbox-url]

> mobx, mobs-state-tree, mobx-react, mobx-react-devtools, mobx-utils, as 1 pkg

# note

* `mobx-state-tree` & `mobx` both export `decorate` and `flow`
* `mobx-state-tree`'s variants are exported as `mstDecorate` & `mstFlow`
* `mobx-react-devtools` exports `DevTools` as default, here it is exported as `DevTools`

# imports

each package can be imported by using the main entry point

```ts
import React from 'react'
import {render} from 'react-dom'
import {observer, observable, action, DevTools} from 'mobx-boost'

const state = observer({
  eh: 'default',
})
state.setEh = action(value => (state.eh = value))

@observer
class Eh extends React.Component {
  state = state
  componentWillMount() {
    this.state.setEh('eh')
  }
  render() {
    return <h1>{String(this.state.eh)}</h1>
  }
}
const App = () => (
  <React.Fragment>
    <DevTools />
    <Eh />
  </React.Fragment>
)

render(<App />, document.getElementById('root'))
```

or by importing the package from the path

```ts
import {observer} from 'mobx-boost/mobx-react'
import {observable} from 'mobx-boost/mobx'
```

or by importing using the dependency _(the packages are dependencies, but use caution if you have them in your project's dependencies so that the versions match)_

```ts
import {observer} from 'mobx-react'
import {observable} from 'mobx'
```

# exports

* there is no default export, all exports are re-exported, so tree shaking will work the same way

# packages

* [mobx](https://github.com/mobxjs/mobx)
* [mobx-state-tree](https://github.com/mobxjs/mobx-state-tree)
* [mst-middlewares](https://github.com/mobxjs/mobx-state-tree/tree/master/packages/mst-middlewares)
* [mobx-react](https://github.com/mobxjs/mobx-react)
* [mobx-react-devtools](https://github.com/mobxjs/mobx-react-devtools)
* [mobx-utils](https://github.com/mobxjs/mobx-utils)

# related

* [medium article on apollo-boost](https://dev-blog.apollodata.com/zero-config-graphql-state-management-27b1f1b3c2c3)

[mobx-boost-codesandbox-image]: https://img.shields.io/badge/mobx_boost-codesandbox-ff69b4.svg?longCache=true
[mobx-boost-codesandbox-url]: https://codesandbox.io/s/ww4y82z6kk
[mobx-boost-npm-image]: https://img.shields.io/npm/v/mobx-boost.svg
[mobx-boost-npm-url]: https://npmjs.org/package/mobx-boost
