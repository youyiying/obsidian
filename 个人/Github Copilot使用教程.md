# 介绍

GitHub Copilot 是全球首个大规模 AI 开发人员工具，可帮助你更快地编写代码，减少工作量。 GitHub Copilot 从注释和代码中提取上下文，以立即为单个行和整个函数提供建议。

研究发现，GitHub Copilot 可帮助开发人员更快地编码，专注于解决更大的问题，长时间地保持良好状态，以及对工作更加满意。

GitHub Copilot 的生成预训练语言模型由 OpenAI 创建，由 OpenAI 提供支持。 扩展可用于 Visual Studio Code、Visual Studio、Neovim 和 JetBrains 集成开发环境 (IDE) 套件。

# 权限申请

要使用GitHub Copilot,需要加入Teams申请权限。

# 安装插件

GitHub Copilot 目前只支持 Visual Studio Code 编辑器。要使用 GitHub Copilot，你需要先安装 Visual Studio Code，并且登录你的 GitHub 账号。然后，你可以在 Visual Studio Code 的扩展商店中搜索 "GitHub Copilot" ，下载并安装 GitHub Copilot 插件。

# 快捷键及配置

| 快捷键         | 说明                              |
| -------------- | --------------------------------- |
| Tab            | 接受建议                          |
| Esc            | 拒绝建议                          |
| Ctrl + Enter   | 会打开一个单独的面板,展示10个建议 |
| Alt/Option + ] | 下一条建议                        |
| Alt/Option + \[ | 上一条建议                        |
| Alt/Option + \ | 触发行内建议                      | 
| cmd + ->       | 逐个单词提示确认                  |

| 配置项                              | 说明             |
| ----------------------------------- | ---------------- |
| github.copilot.inlineSuggest.enable | 是否开启内联提示 |
| editor.suggest.preview              | 编辑器提示预览   |
| editor.inlineSuggest.enabled        | 编辑器内联提示   |
| editor.inlineSuggest.showToolbar    | 显示提示工具栏   |
| github.copilot.enable               | 语言开关         |
| github.copilot.advanced             | 高级设置         |



## Visual Studio Code命令

\- `@workspace`
​	\- 询问关于当前工作空间中的文件的问题
\- `/explain` - 解释所选代码的工作原理
\- `/tests` - 为所选代码生成单元测试
\- `/fix` - 为所选代码中的问题提出修复建议
\- `/new` - 构建新的工作空间脚手架代码
\- `/newNotebook` - 创建新的Jupyter Notebook
\- `/terminal` - 询问如何在终端执行某项操作
\- `@vscode`
​	\- 询问关于VS Code的问题
​	\- `/api` - 询问关于VS Code扩展开发的问题
## Visual Studio命令
- /help - 获取Copilot聊天帮助
- /explain - 解释代码
- /doc - 为该符号添加文档注释
- /fix - 为所选代码中的问题提出修复建议
- /optimize - 分析和优化所选代码的运行时间

# 使用技巧

## 让Copilot学习你的代码

> 将自己编写的代码示例提供给Copilot,有助它更好地模仿你的编码风格。

## 编写具体的需求参数和返回参数

> 例如,如果您输入函数名称、参数和返回值类型,Copilot可以为您生成函数实现。

## 先写好上下文

> 例如类/函数开头注释或示例调用,有助于Copilot生成符合预期的代码。

## 写算法函数

> 输入算法描述、示例输入输出,Copilot可以生成算法实现。

## 写测试用例

> 使用 /// 生成测试用例代码。

```csharp
/// 生成Calculate方法的单元测试
int Calculate(int a, int b)
{
    return a + b;
}
```

## 写注释

> 写上///符号后换行,Copilot会自动提示补全。

```csharp
/// 生成用户管理API控制器
/// GET /api/users
/// POST /api/users
/// GET /api/users/{id}
/// PUT /api/users/{id}
/// DELETE /api/users/{id}
```

## 自动填词

> Copilot可以帮助续写前面未完成的词语。

## 写数组

> 输入数组声明后直接Enter,Copilot会生成数组初始化代码。

## 写文档

> 输入文字后///,Copilot会提供翻译版本。
