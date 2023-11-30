# React初探

## React简介

### React 简介

React 是由 Facebook 开发并维护的一个用于构建用户界面的 JavaScript 库。它以组件化的方式来构建复杂的用户界面。React 最主要的特点包括：

- **声明式编程**：使代码更易读和维护，特别是在创建交互式 UI 时。
- **组件化结构**：允许开发者将 UI 拆分为独立可复用的部分，并独立管理每个部分的状态。
- **虚拟DOM**：提高应用的性能，通过虚拟DOM来最小化与真实DOM的交互。
- **单向数据流**：使得数据管理和状态变化更加可预测。
- **强大的社区支持**：由于其流行性，React 有着广泛的社区支持和丰富的生态系统。

### React 与 Vue 3 的比较

当比较 React 和 Vue 3 时，重要的是要注意，虽然两者都是用于构建用户界面的现代 JavaScript 框架，但它们在设计哲学、生态系统和特定用途方面有所不同。

**React 的优势**

1. **社区和生态系统**：React 拥有一个非常大和成熟的社区，提供了大量的资源、库和工具。这使得寻找问题的解决方案、学习资源和第三方库变得相对容易。
2. **更广泛的采用**：React 被许多大公司和成熟的项目采用，意味着更多的工业案例和最佳实践可供参考。
3. **灵活性**：React 本身更倾向于是一个库而不是一个全面的框架。这种灵活性使得它可以更容易地与其他库和框架集成。
4. **更丰富的职业机会**：由于 React 的流行，掌握 React 的开发者可能会发现更多的职业机会。

**相对于 Vue 3**

- **响应式系统**：Vue 3 引入了 Composition API，这使得它在组织和复用逻辑方面变得更灵活，特别是在更复杂的应用中。
- **易于上手**：Vue 通常被认为更容易上手，特别是对于那些熟悉 HTML 和 JavaScript 基础的开发者来说。
- **集成度**：Vue 提供了更多内置功能和官方支持的附加库，例如 Vue Router 和 Vuex。

在选择 React 或 Vue 3 时，最终的决策往往取决于项目的具体需求、开发团队的熟悉度以及个人偏好。每个框架都有其独特的优势，适合不同类型的项目和开发环境。

## 工程目录文件简介

React 的最新版本（截至我最后更新的时间，2023年4月）本身并不强制规定一个特定的工程目录结构。不过，当你使用 `create-react-app`（一个广泛使用的 React 应用程序引导工具）来初始化一个新项目时，会生成一个标准的目录结构。下面是这种结构的一个简要介绍：

### 标准的 `create-react-app` 目录结构

1. **node_modules/**
   - 存放项目依赖的文件夹。所有通过 npm 或 yarn 安装的包都会放在这里。

2. **public/**
   - 包含静态资源文件。
   - `index.html`：应用的主 HTML 文件。React 组件将挂载到这里定义的 `<div id="root"></div>`。
   - `favicon.ico`：网站的图标。
   - `manifest.json`：用于定义 Progressive Web App (PWA) 行为的文件。
   - 注意`manifest.json` 是一个重要的配置文件，用于定义 Progressive Web App（PWA）的行为和外观。PWA 是一种可以提供类似于原生应用体验的网页应用。这个文件允许开发者控制用户添加网站到他们的主屏幕时的一些设置和外观。下面是 `manifest.json` 文件中一些关键的字段及其作用：
   
     1. **`name`**：应用的名称。这是当用户安装 PWA 到他们的设备时显示的名称。
   
     2. **`short_name`**：应用的简短名称，用于设备主屏幕上的图标下方。
   
     3. **`icons`**：定义一组图标，这些图标用于设备的主屏幕、启动画面等。你可以指定不同尺寸的图标，以适应不同的设备和分辨率。
   
     4. **`start_url`**：指定当用户从主屏幕图标启动应用时应用打开的 URL。
   
     5. **`display`**：控制应用的显示模式。例如，`fullscreen`、`standalone`、`minimal-ui` 或 `browser`。`standalone` 模式使得 PWA 看起来更像一个原生应用，因为它会隐藏浏览器的 UI 元素。
   
     6. **`background_color`**：指定应用启动时的背景颜色。
   
     7. **`description`**：应用的描述。
   
     8. **`orientation`**：指定应用的首选屏幕方向，如 `portrait` 或 `landscape`。
   
     9. **`theme_color`**：指定应用的主题颜色，这影响到浏览器界面的颜色，包括地址栏和任务栏。
   
     通过适当配置这些（以及其他）字段，你可以提供更丰富的用户体验，并使你的网页应用在安装到用户设备时表现得更像一个原生应用。这对于提高用户的参与度和满意度非常有帮助。PWA 的一个关键优势是它能够在离线时继续提供功能，这通过 Service Workers 实现。
   
3. **src/**
   
   - 源代码文件夹，包含所有的 React 组件、JS 文件和 CSS 文件。
   - `App.js`：主要的 React 组件，通常是应用程序的起点。
   - `index.js`：应用程序的入口文件，用于渲染 App 组件。
   - `reportWebVitals.js`（可能包含）：用于测量应用性能的脚本。
   - `setupTests.js`（可能包含）：用于设置测试环境的文件。
   
4. **.gitignore**
   - 指定 git 版本控制要忽略的文件和文件夹。

5. **package.json**
   - 定义项目的元数据和依赖关系，以及可用的脚本和其他配置选项。

6. **README.md**
   - 项目的 README 文件，通常包含关于项目的说明、如何安装和运行项目等信息。

7. **yarn.lock** 或 **package-lock.json**（取决于使用 yarn 还是 npm）
   - 自动生成的文件，用于确保安装准确版本的 npm 包。

### 可选的目录和文件

- **.env 文件**
  
  - 用于存储环境变量。
  
  - 对env文件的解释`.env` 文件在软件开发中用于存储环境变量，它在多种场景下都非常有用：
  
    1. **配置敏感信息**：最常见的用途之一是存储敏感信息，比如数据库密码、API 密钥、秘密令牌等。这些信息不应该直接硬编码在代码中，以避免泄露或不安全的发布。
  
    2. **区分开发和生产环境**：开发、测试和生产环境通常需要不同的配置。例如，数据库URL、日志级别或第三方服务的API密钥在不同环境中可能会有所不同。通过环境变量，可以在不修改代码的情况下切换这些配置。
  
    3. **提高安全性**：将敏感信息存储在环境变量中可以提高应用程序的安全性。这些信息不会被提交到版本控制系统（如 Git），因此降低了信息泄露的风险。
  
    4. **易于配置更改**：通过 `.env` 文件，开发者可以轻松更改应用的配置而无需重新编译或重启应用。这在云服务和容器化部署中尤其有用。
  
    5. **平台独立性**：不同的部署平台（如 Heroku、AWS、Azure）可能有自己的方式来设置环境变量。`.env` 文件提供了一种统一的方式来处理这些环境变量，使得从一个平台迁移到另一个平台变得更加容易。
  
    在 React 应用程序中，`.env` 文件通常与 `create-react-app` 或其他类似的构建工具一起使用，这些工具会自动将 `.env` 文件中的变量加载到 `process.env` 中，使得它们可以在应用程序的 JavaScript 代码中被访问。这种方法使得管理配置变得更加简单和安全。
  
- **.eslintrc.js / .prettierrc**
  
  - 代码质量和格式化工具的配置文件。
  
  - `eslintrc.js` 和 `prettierrc` 是两个重要的配置文件，用于维护代码质量和格式的一致性。它们分别属于 ESLint 和 Prettier 这两个工具。下面是关于如何配置和学习这些工具的一些指导：
  
  - #### **ESLint（.eslintrc.js）**
  
    ESLint 是一个静态代码分析工具，用于识别 JavaScript 代码中的问题。它不仅可以捕获错误，还可以强制执行代码风格规则。
  
    1. **安装 ESLint**：首先，你需要在项目中安装 ESLint。可以通过 npm 或 yarn 完成：
       
       ```bash
       npm install eslint --save-dev
       # 或
       yarn add eslint --dev
       ```
       
    2. **初始化配置文件**：使用 ESLint 的初始化命令来创建一个 `.eslintrc.js` 配置文件：
       ```bash
       npx eslint --init
       ```
       这个命令会引导你完成一系列问题，以生成适合你项目的配置。
    
    3. **配置规则**：在 `.eslintrc.js` 文件中，你可以定义规则。例如：
       ```javascript
       module.exports = {
         env: {
           browser: true,
           es2021: true,
         },
         extends: [
           'plugin:react/recommended',
           'airbnb',
         ],
         rules: {
           'no-console': 'warn',
           'react/react-in-jsx-scope': 'off',
           // 更多规则...
         },
       };
       ```
    
    4. **学习和研究**：你可以访问 [ESLint 官方文档](https://eslint.org/docs/user-guide/configuring) 来了解更多关于规则和配置的信息。也可以在 GitHub 或其他项目中查看 `.eslintrc.js` 文件的例子，以获得灵感。
    
   -  #### **Prettier（.prettierrc）**
  
    Prettier 是一个代码格式化工具，它支持多种语言并且提供一致的代码风格。
  
    1. **安装 Prettier**：与 ESLint 类似，你可以通过 npm 或 yarn 安装 Prettier：
       
       ```bash
       npm install --save-dev prettier
       # 或
       yarn add --dev prettier
       ```
       
    2. **创建配置文件**：创建一个 `.prettierrc` 文件，在其中定义你的格式化规则。例如：
       ```json
       {
         "semi": false,
         "singleQuote": true
       }
       ```
    
    3. **集成 ESLint 和 Prettier**：为了确保 ESLint 和 Prettier 之间不会有冲突，你可以安装 `eslint-config-prettier` 和 `eslint-plugin-prettier`。
       ```bash
       npm install --save-dev eslint-config-prettier eslint-plugin-prettier
       ```
    
    4. **学习和研究**：参考 [Prettier 官方文档](https://prettier.io/docs/en/configuration.html) 来学习更多关于配置选项。同样，你也可以参考其他开源项目中的 `.prettierrc` 文件。
  
    结合实践学习
  
    - **实践项目中应用**：在实际项目中应用 ESLint 和 Prettier，对遇到的问题进行调试和解决。
    - **社区资源**：参考社区最佳实践和推荐配置，如 Airbnb 的 JavaScript 风格指南。
    - **不断迭代**：随着项目的发展，你可能需要不断调整和完善你的配置文件，以适应项目的变化。
  
- **tests/ 或 __tests__/**
  
  - 存放测试文件。
  
- **components/**
  - 存放 React 组件的目录，通常按功能或页面划分子目录。

- **assets/**
  
  - 存放图像、字体等资源的目录。
  
- **services/**
  - 存放与外部 API 交互的服务函数。

- **utils/**
  - 存放实用程序和帮助函数。

这个结构可以根据项目的规模和需求进行调整。大型项目可能需要更详细的目录结构，以保持代码的可管理性和可扩展性。

## React中的组件

### react 引入tips

```react
import {Component} from 'React';
//等价于
import React from 'react';
const Component = React.Component;
```

###  React.DOM.render

```react
import React from 'react';
import ReactDOM from 'react-dom';

ReactDOM.render(<App/>,document.getElementByID('root'));
```

`ReactDOM.render` 函数是 React 库中的一个核心函数，它的主要作用是将 React 组件渲染到真实的 DOM 节点中。这个函数是 React 应用与浏览器 DOM 交互的桥梁，它使得 React 能够控制页面上的内容。下面是对这个函数及其组成部分的详细解释：

### ReactDOM.render 函数

- **函数定义**：`ReactDOM.render(whatToRender, whereToRender)`。
- **参数**：
  - `whatToRender`：这是你希望渲染的 React 元素或组件。它通常是 JSX 表达式，它告诉 React 你想在页面上显示什么。
  - `whereToRender`：这是一个 DOM 元素，表示你想在哪里渲染这个 React 元素。React 将在这个 DOM 元素内部管理所有的内容和更新。

#### 示例解释

在示例中 `ReactDOM.render(<App/>, document.getElementById('root'));`：

1. **`<App/>`**：这是 React 组件（在这个示例中是 `App` 组件）。它可以是一个简单的组件，也可以是复杂的组件树的根。在 JSX 中，组件被写作标签（如 HTML 标签），并且可以包含其他组件和 HTML 元素。

2. **`document.getElementById('root')`**：这个 JavaScript 函数调用是在查询 HTML 文档，寻找一个 ID 为 `root` 的元素。这个元素是 React 应用的挂载点，即 React 组件将在这个元素内部渲染其内容。在 HTML 文件中，通常有一个 `<div id="root"></div>` 用作这个目的。

#### 渲染过程

- 当 `ReactDOM.render` 被调用时，React 会在页面上查找 ID 为 `root` 的 DOM 元素。
- 接着，React 会将 `App` 组件（或者是其他任何传递给 `ReactDOM.render` 的组件）渲染到找到的 DOM 元素中。
- 如果 `App` 组件有状态更新或者重新渲染的需求，React 会智能地只更新必要的部分，而不是整个 DOM 树。

#### 重要性

- **应用的入口点**：`ReactDOM.render` 是 React 应用开始的地方。它是连接 React 组件和浏览器 DOM 的关键函数。
- **虚拟 DOM**：React 使用虚拟 DOM 来提高性能。虽然 `ReactDOM.render` 操作真实的 DOM，但它是基于 React 的虚拟 DOM 来决定什么时候以及如何更新真实的 DOM。
- **组件的挂载**：这个函数负责“挂载”组件到 DOM 上。当组件第一次渲染时，它执行“挂载”操作，而当组件的状态发生变化时，React 将重新渲染这些组件并提供高效的更新。

### 函数组件

您的示例中的 `function App()` 是一个函数组件的例子。函数组件的特点包括：

- **简洁性**：函数组件通常更简洁，易于理解和编写。
- **无状态**：在引入 Hooks 之前，函数组件通常用于无状态组件（即不需要管理 state）。
- **Hooks**：React 16.8 引入了 Hooks，使得函数组件可以使用状态（`useState`）和其他 React 特性（如 `useEffect`）。
- **返回 JSX**：函数组件直接返回 JSX 元素。

示例代码：
```javascript
function App() {
  return (
    <div className="App">
       <div>hello world</div>
    </div>
  );
}
```

### 类组件

类组件通过扩展 `React.Component` 来创建。它们的特点包括：

- **状态管理**：类组件可以通过 `this.state` 和 `this.setState` 管理内部状态。
- **生命周期方法**：类组件提供了完整的生命周期方法，如 `componentDidMount`、`componentDidUpdate` 等。
- **更复杂的逻辑**：对于包含复杂状态逻辑和侧效（side effects）的组件，类组件可能是更好的选择（尽管 Hooks 的引入已部分改变这一点）。

示例代码：
```javascript
class App extends React.Component {
  render() {
    return (
      <div className="App">
        <div>hello world</div>
      </div>
    );
  }
}
```

### 对比

- **语法和结构**：函数组件使用函数语法，**更简洁**；类组件使用类语法，可能**更易于组织复杂的逻辑**。
- **Hooks**：函数组件可以使用 Hooks，这是类组件所不具备的。Hooks 使得在函数组件中使用状态和其他 React 特性成为可能。
- **生命周期方法**：类组件可以利用多种生命周期方法来管理组件的创建、更新和销毁过程，而函数组件则通过 Hooks（如 `useEffect`）实现类似的功能。
- **this 关键字**：在类组件中，你需要使用 `this` 来访问 props、state 和方法。而在函数组件中，你直接使用这些值和函数。

总体而言，随着 React Hooks 的引入，函数组件变得更加强大和灵活，许多开发者和项目开始更多地使用函数组件。但是，类组件依然在许多现存项目中广泛使用，并且在某些情况下可能更适合某些特定的用例。

## React中最基础的JSX语法



# React基础精讲
## 使用React编写TodoList功能

## React中的响应式设计思想和事件绑定

## 实现TodoList新增删除功能

## JSX语法细节补充

## 拆分组件与组件之间的传值

## TodoList代码优化

## 围绕React衍生出的思考

# React高级内容
## React developer tools安装及使用

## PropTypes与DefaultProps的应用

## props，state与render函数的关系

## React中的虚拟DOM

## 深入了解虚拟DOM

## 虚拟DOM中的Diff算法

## React中ref的使用

## React的生命周期函数

## React生命周期函数的使用场景

## 使用Charles实现本地数据mock

## React中实现CSS过渡动画

## React中使用CSS动画效果

## 使用react-transition-group实现动画（1）

## 使用react-transition-group的使用（2）

# Redux入门
## Redux概念简述

## Redux的工作流程

## 使用Antd实现TodoList页面布局

## 创建redux中的store

## Action和Reducer的编写

## 使用Redux完成TodoList删除功能

## ActionTypes的拆分

## 使用actionCreator统一创建action

## Redux知识点复习补充

# Redux进阶
## UI组件和容器组件

## 无状态组件

## Redux中发送异步请求获取数据

## 使用Redux-thunk中间件实现ajax数据请求

## 什么是Redux的中间件

## Redux-saga中间件入门（1）

## Redux-saga中间件入门（2）

## 如何使用React-redux（1）

## 如何使用React-redux（2）

## 使用React-redux完成TodoList功能

# 项目实战：Header组件开发
## 项目目录搭建，Styled-Components与Reset.css的结合使用

## 使用styled-components完成Header组件布局（1）

## 使用styled-components完成Header组件布局（2）

## 使用iconfont嵌入头部图标

## 搜索框动画效果实现

## 使用React-Redux进行应用数据的管理

## 使用combineReducers完成对数据的拆分管理

## actionCreators与constants的拆分

## 使用Immutable.js来管理store中的数据

## 使用redux-immutable统一数据格式

## 热门搜索样式布局

## Ajax获取推荐数据

## 代码优化微调

## 热门搜索换页功能实现

## 换页旋转动画效果的实现

## 避免无意义的请求发送，提升组件性能

# 项目实战：首页开发
- 什么是路由，如何在React中使用路由功能
- 首页组件的拆分
- 首页专题区域布局及reducer的设计
- 首页文章列表制作
- 首页推荐部分代码编写
- 首页异步数据获取
- 异步操作代码拆分优化
- 实现加载更多功能
- 返回顶部功能实现
- 首页性能优化及路由跳转

# 项目实战：详情页面和登录功能开发
- 详情页面布局
- 使用redux管理详情页面数据
- 异步获取数据
- 页面路由参数的传递
- 登陆页面布局
- 登陆功能实现
- 登陆鉴权及代码优化
- 异步组件及withRouter路由方法的