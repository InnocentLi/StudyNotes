# JavaScript高级程序设计

# HTML的JavaScript

## \<scirpt>元素

#### 8个元素 

| 属性           | 选择性                                                       |
| :------------- | ------------------------------------------------------------ |
| async          | 是否立即下载脚本，但不能阻止其他页面动作                     |
| charset        | 使用src属性指定的代码字符集                                  |
| crossorigin    | 配置相关请求的CORS。默认不实用                               |
| defer          | 是否延迟到文档执行完被解析后再进行执行                       |
| integrity      | 验证子资源完整性。如果签名和这个签名不一致会报错处理，确保CDN不会提供恶意内容 |
| language(废弃) | -                                                            |
| src            | 表示要执行的代码或者外部文件                                 |
| type           | 代替language                                                 |

#### 标签位置

1.放在head中间

```html
<!DOCTYPE html>
<head>
    <title>Document</title>
    <script src="a1.js"></script>   例子
    <script src="a1.js"></script>   例子
</head>
</html>
```

把所有的JS文件都放在\<head>里也就意味着，必须把所有js文件下载，解析，解释完成后，才能开始页面。

2.放在body中













































# 语言基础

# 变量内存作用域

# 基本引用类型

# 集合引用类型

# 迭代器和生成器

# 对象类与面向对象编程

# 代理与反射

# 函数

# 契约与异步函数

# BOM

# 客户端检测

# DOM

# DOM扩展

# DOM2和DOM3

# 事件

# 动画和canvas模型

# JavascriptAPI

# 错误处理和调试

# 处理XML

# 网络请求与远程资源

# 客户端存储

# 模块

# 工作者线程

# 最佳实践