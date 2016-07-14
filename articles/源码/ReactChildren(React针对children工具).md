#React源码分析系列

###ReactChildren

该类主要是输出
forEach、map、mapIntoWithKeyPrefixInternal、count、toArray 方法，挂载React.Children下，方便操作React实例对象的this.props.children对应内部的子元素。
官网的[描述](https://facebook.github.io/react/docs/top-level-api.html#react.children)：

    React.Children provides utilities for dealing with the this.props.children opaque data structure.