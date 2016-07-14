#React源码分析系列

###ReactComponent

更新组件state的基础帮助类，主要提供

setState(partialState, callback)

	partialState：待更新的状态，state会将其放到setState的队列里

	callback: 时间回掉


forceUpdate(callback)

执行forceUpdate不会执行`shouldComponentUpdate`， 但会执行`componentWillUpdate` 和`componentDidUpdate`



注：React.CreateClass创建组件内部方法不能包含isMounted\replaceState方法，否则会抛出异常。