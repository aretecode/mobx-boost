# mobx-boost

[![NPM version][mobx-boost-npm-image]][mobx-boost-npm-url]

> mobx, mobs-state-tree, mobx-react, mobx-react-devtools, mobx-utils, as 1 pkg

# note

* `mobx-state-tree` & `mobx` both export `decorate` and `flow`
* `mobx-state-tree`'s variants are exported as `mstDecorate` & `mstFlow`

# imports

each package can be imported by using the main entry point

```ts
import {observer, observable, action, DevTools} from 'mobx-boost'

const state = observer({
  eh: undefined,
})
state.setEh = action(value => (state.eh = value))

@observer
class App {
  state = state
  componentWillMount() {
    this.state.setEh('eh')
  }
  render() {
    return <h1>{this.state.eh}</h1>
  }
}
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

# packages

* [https://github.com/mobxjs/mobx](mobx)
* [https://github.com/mobxjs/mobx-state-tree](mobx-state-tree)
* [https://github.com/mobxjs/mobx-state-tree/tree/master/packages/mst-middlewares](mst-middlewares)
* [https://github.com/mobxjs/mobx-react](mobx-react)
* [https://github.com/mobxjs/mobx-react-devtools](mobx-react-devtools)
* [https://github.com/mobxjs/mobx-utils](mobx-utils)

# related

* [https://dev-blog.apollodata.com/zero-config-graphql-state-management-27b1f1b3c2c3](apollo-boost)

[mobx-boost-npm-image]: https://img.shields.io/npm/v/mobx-boost.svg
[mobx-boost-npm-url]: https://npmjs.org/package/mobx-boost
