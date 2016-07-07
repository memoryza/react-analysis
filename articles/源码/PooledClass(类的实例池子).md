#React源码分析系列

###PooledClass

向给定对象的上初始化方法、属性；

PooledClass形的类包含destructor析构函数[必须]、实例个数[默认10个]、添加实例对应调用参数个数的函数[默认oneArgumentPooler]

其中包含[one|two|three|four|five]ArgumentPooler、addPoolingTo、standardReleaser

其中[one|two|three|four|five]ArgumentPooler通过类.call(实例,n个参数)的方式，之前有在微博看过关于call 传递多少（我忘记了，貌似是7、8个）参数的情况下比apply快，这个没有看过webkit中的源代码确实不敢确认，不过现阶段测试同样的函数调用方式不同感觉性能差距没有那么大，既然React里面的代码也这么写了看来是确有其事并且这个pooler调用量估计不小吧.

instancePool 维护实例的数组

release 添加实例的方法

poolSize 实例个数限制

getPooled 实例默认的调用参数个数的方法



addPoolingTo:构造一个满足pooledClass类型的实例
   	
   	<code>
   	
   	   	var addPoolingTo = function (CopyConstructor, pooler) {
  			var NewKlass = CopyConstructor;
  			NewKlass.instancePool = [];
 			NewKlass.getPooled = pooler || DEFAULT_POOLER;
  			if (!NewKlass.poolSize) {
    			NewKlass.poolSize = DEFAULT_POOL_SIZE;
  			}
  			NewKlass.release = standardReleaser;
  			return NewKlass;
		};
	</code>