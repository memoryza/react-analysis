#React源码分析系列

###reactProdInvariant AND Invariant


这两个文件暴露出来的接口是React整体异常报错的系统，通过new Error的方式将错误信息输出到控制台。根据NODE_ENV来确认当前是生产环境还是开发环境，当时生产环境如果有异常抛出则直接引导到React Document的Error Decoder[地址](https://facebook.github.io/react/docs/error-decoder.html?invariant=2)，否则直接产出error