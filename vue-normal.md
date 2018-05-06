1、所有命名必须具有语义化，不允许直接后缀加上1,2,3，js代码使用驼峰命名法，css代码使用-或者_连接符，组件首字符大写。

2、关键代码需要注释说明，公用组件需要说明调用方式以及入参、响应参数。

3、代码必须格式化，console.log以及注释之类的代码在调试完成后全部删除。

4、组件书写顺序按照统一结构排版：`<template></template><script></script><style></style>`。

5、组件template最外层标签添加唯一className，组件的name属性名于此相同，书写样式时最外层加上统一加上改className。

6、生命周期书写顺序一般按照name、mixins、components、props、data、computed、watch、created、mounted、methods排序。

7、提取公共css样式库，解耦css代码，提高className复用性。可参考[css库](https://github.com/binglinzhang/my-css-style)

8、公用组件放置components文件夹下，且对于常用的公用组件，将其注册为全局组件使用，非公用组件放置views相关模块文件夹下，所有组件必须首字母大写。

9、一个组件逻辑代码部分总行数尽量不超过400行，如果超过考虑进行组件拆分，拆分有2种方式，一种是通过vue提供的mixins功能，一种是直接引入js文件方式，但需要注意作用域问题。同理methods里面尽量编写纯函数，函数解耦，函数功能单一化等。

10、所有api的url路径统一提取到一个文件进行维护，可写为常量的形式。

11、views文件目录按照功能模块的router层级设置，且最好每个功能模块有个index入口文件，方便快捷根据路由地址找到相关代码。

12、vue项目文件目录中不允许存在中文字符，否则热加载失败。

13、assets文件夹中尽量按照css、font、images、js文件夹进行区分，非静态资源尽量不要放置在static文件夹。