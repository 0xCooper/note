![WebAssembly logo](../../img/webassembly.png)



WebAssembly/*wasm* WebAssembly 或者 wasm 是一个可移植、体积小、加载快并且兼容 Web 的全新格式

WebAssembly 是由主流浏览器厂商组成的 [W3C 社区团体](https://www.w3.org/community/webassembly/) 制定的一个新的规范。

### 高效

WebAssembly 有一套完整的[语义](https://www.wasm.com.cn/docs/semantics/)，实际上 wasm 是体积小且加载快的[二进制格式](https://www.wasm.com.cn/docs/binary-encoding/)， 其目标就是充分发挥[硬件](https://www.wasm.com.cn/docs/portability/#assumptions-for-efficient-execution)能力以达到原生执行效率

### 安全

WebAssembly 运行在一个沙箱化的[执行环境](https://www.wasm.com.cn/docs/semantics/#linear-memory)中，甚至可以在现有的 JavaScript 虚拟机中实现。在[web环境中](https://www.wasm.com.cn/docs/web/)，WebAssembly将会严格遵守同源策略以及浏览器安全策略。

### 开放

WebAssembly 设计了一个非常规整的[文本格式](https://www.wasm.com.cn/docs/text-format/)用来、调试、测试、实验、优化、学习、教学或者编写程序。可以以这种文本格式在web页面上[查看wasm模块的源码](https://www.wasm.com.cn/docs/faq/#will-webassembly-support-view-source-on-the-web)。

### 标准

WebAssembly 在 [web](https://www.wasm.com.cn/docs/web/) 中被设计成无版本、特性可测试、向后兼容的。WebAssembly 可以被 JavaScript 调用，进入 JavaScript 上下文，也可以像 Web API 一样调用浏览器的功能。当然，WebAssembly 不仅可以运行在浏览器上，也可以运行在[非web](https://www.wasm.com.cn/docs/non-web/)环境下。

https://www.jianshu.com/p/6b774fb2a345