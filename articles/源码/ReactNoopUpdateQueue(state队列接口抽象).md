#React源码分析系列

###ReactNoopUpdateQueue


React  this.setState等更新状态维护state状态队列或者是确定组件是否mount的API接口，不过这里是空方法或者是warning。这里可以认为就是抽象方法，继承他的updater更新者需要实现这些方法。