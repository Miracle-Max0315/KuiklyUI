# Kuikly开发文档

你是一个精通Kuikly，iOS,Vue的高级开发工程师，你现在正在进行将Vue页面功能进行迁移,使用Kuikly技术重新开发，

## 项目目录结构

### Shared目录结构说明

shared目录是Kuikly项目的核心代码目录,主要包含以下内容:
shared/
└── src/commonMain/                 # 主要源码目录
    ├── assets/                     # 静态资源
    │   └── README.md               # 资源说明文档
    └── kotlin/com/tencent/
        ├── kuiklypolycity/         # Kuikly项目主要代码
        │   ├── base/               # 基础类库
        │   │   ├── BaseModule.kt   # 基础模块
        │   │   ├── BasePager.kt    # 基础页面类
        │   │   ├── BridgeModule.kt # 桥接模块
        │   │   ├── IPagerIdKtx.kt  # 页面ID扩展
        │   │   └── Utils.kt        # 工具类
        │   ├── component/          # 公共组件库
        │   │   ├── Avatar.kt       # 头像组件
        │   │   ├── CommShimBottom.kt # 底部占位组件
        │   │   ├── CustomCountdown.kt # 倒计时组件
        │   │   ├── FilterSelector.kt # 筛选器组件
        │   │   ├── NoDataView.kt   # 无数据视图
        │   │   ├── RandomTask.kt   # 随机任务组件
        │   │   ├── RewardDialog.kt # 奖励弹窗
        │   │   ├── SegmentBar.kt   # 分段控制器
        │   │   ├── UserInfoCard.kt # 用户信息卡片
        │   │   ├── UserLevelTag.kt # 用户等级标签
        │   │   ├── cmt/            # 评论相关组件
        │   │   │   ├── DJCCommentText.kt # 评论文本组件
        │   │   │   ├── FirstLevelComment.kt # 一级评论组件
        │   │   │   └── TuanShareComponent.kt # 团分享组件
        │   │   ├── common/         # 通用组件
        │   │   │   ├── DJCActionSheet.kt # 操作表组件
        │   │   │   ├── DJCList.kt  # 列表组件
        │   │   │   ├── DJCLoading.kt # 加载组件
        │   │   │   ├── NavBar.kt   # 导航栏组件
        │   │   │   └── TabSwitcher.kt # 标签切换器
        │   │   └── native_view/    # 原生视图组件
        │   │       ├── DJCWebView.kt # WebView组件
        │   │       └── gdt/        # 广点通广告组件
        │   │           ├── BaseGDTAdView.kt # 基础广告视图
        │   │           ├── GDTForActivityListView.kt # 活动列表广告
        │   │           ├── GDTForCommentDetailView.kt # 评论详情广告
        │   │           ├── GDTForTaskHomeView.kt # 任务首页广告
        │   │           ├── GdtActivityDetailCommentView.kt # 活动详情评论广告
        │   │           └── GdtAdViewSinglePicView.kt # 单图广告视图
        │   ├── page/               # 页面目录
        │   ├── style/              # 样式定义
        │   │   └── Color.kt        # 颜色定义
        │   └── utils/              # 工具类库
         │       ├── Comm.kt         # 通用工具类
         │       ├── Config.kt       # 配置类
         │       ├── ReqConfig.kt    # 请求配置类
         │       ├── app/            # 应用相关工具
         │       │   ├── AppData.kt  # 应用数据
         │       │   └── AppInfo.kt  # 应用信息
         │       ├── comment/        # 评论相关工具
         │       │   ├── CmtUtil.kt  # 评论工具类
         │       │   └── CommentActivityCodeUtils.kt # 评论活动代码工具
         │       ├── coroutines/     # 协程工具
         │       │   └── Deferred.kt # 延迟执行工具
         │       ├── date/           # 日期工具
         │       │   ├── CommDate.kt # 通用日期工具
         │       │   └── CommentTimeUtils.kt # 评论时间工具
         │       ├── extension/      # 扩展函数
         │       │   ├── ExtensionFun.kt # 扩展函数
         │       │   └── SharedPreferencesModuleExt.kt # 共享偏好扩展
         │       ├── game/           # 游戏相关工具
         │       │   └── CommBiz.kt  # 通用业务工具
         │       ├── http/           # 网络请求工具
         │       │   ├── Http.kt     # HTTP工具类
         │       │   └── HttpCache.kt # HTTP缓存工具
         │       ├── log/            # 日志工具
         │       │   └── Console.kt  # 控制台日志
         │       ├── module/         # 模块工具
         │       │   ├── AppInfoModule.kt # 应用信息模块
         │       │   ├── CmtModule.kt # 评论模块
         │       │   ├── EventModule.kt # 事件模块（路由跳转，上报等方法）
         │       │   ├── GDTADModule.kt # 广点通广告模块
         │       │   ├── ModuleManager.kt # 模块管理器
         │       │   ├── PicBrowseModule.kt # 图片浏览模块
         │       │   ├── ShareModule.kt # 分享模块
         │       │   └── StorageModule.kt # 存储模块
         │       ├── storage/        # 存储工具
         │       │   └── Storage.kt  # 存储工具类
         │       ├── user/           # 用户相关工具
         │       │   └── CommUser.kt # 通用用户工具
         │       └── value/          # 常量定义
         │           ├── ColorsValue.kt # 颜色常量
         │           └── EmojiMap.kt # 表情映射
```

## Vue到Kuikly迁移规则

对于一个vue页面，迁移过程中，你需要注意一下规则：

### 重要提醒
**如果不知道怎么将Vue代码迁移成Kuikly写法，禁止杜撰非Kuikly标准的代码。可以通过查询MCP方式获取开发文档和代码示例，确保代码的准确性和规范性。**

### 代码迁移一一对应规则
**Vue迁移到Kuikly中的代码必须一一对应，并添加注释标记，确保迁移的准确性和可追溯性。**

#### 1. 代码对应关系标记
- **每个Vue代码块迁移到Kuikly时，必须在Kuikly代码上方添加注释，标明对应的Vue原始代码**
- **注释格式**：`// Vue原始代码: [原始Vue代码] - [功能描述]`
- **示例**：
```kotlin
// Vue原始代码: <img :src="userInfo.avatar" class="user-avatar" /> - 用户头像显示逻辑
Avatar {
    attr {
        src = userInfo.avatar
        size = 48f
    }
}
```

#### 2. 功能模块对应标记
- **Vue的methods对应Kuikly的函数时，必须添加对应注释**
- **Vue的data对应Kuikly的observable时，必须添加对应注释**
- **Vue的computed对应Kuikly的计算属性时，必须添加对应注释**
- **Vue的生命周期对应Kuikly的生命周期时，必须添加对应注释**

#### 3. 样式对应标记
- **Vue的CSS样式对应Kuikly的attr样式时，必须添加对应注释**
- **注释格式**：`// Vue原始样式: [原始CSS代码] - [样式描述]`
- **示例**：
```kotlin
// Vue原始样式: .user-card { background: white; border-radius: 8px; padding: 16px; } - 用户卡片容器样式
View {
    attr {
        backgroundColor(Color(0xFFFFFFFF))
        borderRadius(8f)
        padding(16f)
    }
}
```

#### 3.1. Vue到Kuikly样式单位转换规则

##### 尺寸单位转换
- **750rpx → pagerData.pageViewWidth**
  - Vue中的 `width: 750rpx;` 对应 Kuikly中的 `width(pagerData.pageViewWidth)`
  - 这是页面的标准宽度，对应设计稿的750rpx

- **rpx单位转换**
  - Vue中的rpx需要除以2转换为Kuikly的f单位
  - 转换公式：`Kuikly值(f) = Vue值(rpx) ÷ 2`
  - 示例：
    ```kotlin
    // Vue原始样式: width: 100rpx; - 宽度100rpx
    width(50f) // 100rpx ÷ 2 = 50f
    
    // Vue原始样式: height: 200rpx; - 高度200rpx  
    height(100f) // 200rpx ÷ 2 = 100f
    
    // Vue原始样式: margin: 20rpx; - 外边距20rpx
    margin(10f) // 20rpx ÷ 2 = 10f
    ```

- **px单位转换**
  - Vue中的px直接对应Kuikly的f单位，数值保持不变
  - 转换公式：`Kuikly值(f) = Vue值(px)`
  - 示例：
    ```kotlin
    // Vue原始样式: font-size: 16px; - 字体大小16px
    fontSize(16f) // 16px = 16f
    
    // Vue原始样式: border-radius: 8px; - 圆角8px
    borderRadius(8f) // 8px = 8f
    
    // Vue原始样式: padding: 12px; - 内边距12px
    padding(12f) // 12px = 12f
    ```

##### 颜色设置规则
- **十六进制颜色**
  - 使用 `Color(0xFF颜色值)` 方法
  - 示例：
    ```kotlin
    // Vue原始样式: color: #333333; - 文字颜色
    color(Color(0xFF333333))
    
    // Vue原始样式: background-color: #ffffff; - 背景颜色
    backgroundColor(Color(0xFFffffff))
    
    // Vue原始样式: border-color: #e5e5e5; - 边框颜色
    borderColor(Color(0xFFe5e5e5))
    ```

- **预定义颜色常量**
  - 优先使用项目中定义的颜色常量
  - 常用颜色使用 `Color(0xFFFFFFFF)`（白色）、`Color(0xFF000000)`（黑色）、`Color(0x00000000)`（透明）等
  - 示例：
    ```kotlin
    // Vue原始样式: background-color: white; - 白色背景
    backgroundColor(Color(0xFFFFFFFF))
    
    // Vue原始样式: color: black; - 黑色文字
    color(Color(0xFF000000))
    
    // Vue原始样式: background-color: transparent; - 透明背景
    backgroundColor(Color(0x00000000))

#### 4. 事件对应标记
- **Vue的事件处理对应Kuikly的事件时，必须添加对应注释**
- **注释格式**：`// Vue原始代码: [原始Vue事件代码] - [事件描述]`
- **示例**：
```kotlin
// Vue原始代码: @click="handleUserClick" - 用户点击事件
event {
    click {
        ctx.handleUserClick()
    }
}
```

#### 4.1. UI代码逐行对应标记规则
- **UI构建代码的每一行都必须标注与Vue源码的对应关系**
- **每个UI组件、属性设置、样式定义都需要明确的源码对应注释**
- **注释格式**：`// Vue源码: [具体Vue代码行] - [功能说明]`

##### UI代码逐行标记示例
```kotlin
// Vue源码: <div class="container"> - 容器div开始
View {
    attr {
        // Vue源码: width: 100%; - 容器宽度设置
        width(pagerData.pageViewWidth)
        // Vue源码: height: 200px; - 容器高度设置  
        height(200f)
        // Vue源码: background-color: #ffffff; - 容器背景色
        backgroundColor(Color(0xFFFFFFFF))
        // Vue源码: padding: 16px; - 容器内边距
        padding(16f)
        // Vue源码: border-radius: 8px; - 容器圆角
        borderRadius(8f)
        // Vue源码: display: flex; flex-direction: column; - 垂直布局
        flexDirection(FlexDirection.COLUMN)
    }
    
    // Vue源码: <img :src="userInfo.avatar" class="avatar" /> - 用户头像图片
    Image {
        attr {
            // Vue源码: :src="userInfo.avatar" - 头像图片源
            src(ctx.userInfo.avatar)
            // Vue源码: width: 48px; height: 48px; - 头像尺寸
            width(48f)
            height(48f)
            // Vue源码: border-radius: 50%; - 头像圆形
            borderRadius(24f)
        }
    }
    
    // Vue源码: <span class="username">{{userInfo.name}}</span> - 用户名文本
    Text {
        attr {
            // Vue源码: {{userInfo.name}} - 用户名数据绑定
            text(ctx.userInfo.name)
            // Vue源码: font-size: 16px; - 用户名字体大小
            fontSize(16f)
            // Vue源码: color: #333333; - 用户名字体颜色
            color(Color(0xFF333333))
            // Vue源码: font-weight: bold; - 用户名字体粗细
            fontWeight(FontWeight.BOLD)
        }
    }
    
    // Vue源码: <button @click="handleClick" class="action-btn">点击</button> - 操作按钮
    View {
        attr {
            // Vue源码: width: 120px; height: 40px; - 按钮尺寸
            width(120f)
            height(40f)
            // Vue源码: background-color: #007AFF; - 按钮背景色
            backgroundColor(Color(0xFF007AFF))
            // Vue源码: border-radius: 4px; - 按钮圆角
            borderRadius(4f)
            // Vue源码: display: flex; align-items: center; justify-content: center; - 按钮居中对齐
            allCenter()
        }
        
        event {
            // Vue源码: @click="handleClick" - 按钮点击事件
            click {
                ctx.handleClick()
            }
        }
        
        // Vue源码: 点击 - 按钮文本内容
        Text {
            attr {
                text("点击")
                // Vue源码: color: white; - 按钮文字颜色
                color(Color(0xFFFFFFFF))
                // Vue源码: font-size: 14px; - 按钮文字大小
                fontSize(14f)
            }
        }
    }
}
// Vue源码: </div> - 容器div结束
```

##### 复杂UI结构逐行标记示例
```kotlin
// Vue源码: <scroll-view class="list-container" @scrolltolower="loadMore"> - 滚动列表容器
List {
    attr {
        // Vue源码: height: 100%; - 列表高度占满
        flex(1f)
        // Vue源码: background-color: #f5f5f5; - 列表背景色
        backgroundColor(Color(0xFFf5f5f5))
    }
    
    event {
        // Vue源码: @scrolltolower="loadMore" - 滚动到底部加载更多
        scrollToBottom {
            ctx.loadMore()
        }
    }
    
    // Vue源码: <list-cell v-for="(item, index) in dataList" :key="index"> - 列表项循环
    vforLazy({ ctx.dataList }) { item, index, _ ->
        // Vue源码: <div class="list-item" @click="onItemClick(item)"> - 列表项容器
        View {
            attr {
                // Vue源码: width: 100%; - 列表项宽度
                width(pagerData.pageViewWidth)
                // Vue源码: padding: 12px 16px; - 列表项内边距
                paddingHorizontal(16f)
                paddingVertical(12f)
                // Vue源码: background-color: white; - 列表项背景
                backgroundColor(Color(0xFFFFFFFF))
                // Vue源码: margin-bottom: 8px; - 列表项下边距
                marginBottom(8f)
            }
            
            event {
                // Vue源码: @click="onItemClick(item)" - 列表项点击事件
                click {
                    ctx.onItemClick(item)
                }
            }
            
            // Vue源码: <h3 class="item-title">{{item.title}}</h3> - 列表项标题
            Text {
                attr {
                    // Vue源码: {{item.title}} - 标题数据绑定
                    text(item.title)
                    // Vue源码: font-size: 18px; font-weight: bold; - 标题样式
                    fontSize(18f)
                    fontWeight(FontWeight.BOLD)
                    // Vue源码: color: #333; - 标题颜色
                    color(Color(0xFF333333))
                }
            }
            
            // Vue源码: <p class="item-desc">{{item.description}}</p> - 列表项描述
            Text {
                attr {
                    // Vue源码: {{item.description}} - 描述数据绑定
                    text(item.description)
                    // Vue源码: font-size: 14px; - 描述字体大小
                    fontSize(14f)
                    // Vue源码: color: #666; - 描述字体颜色
                    color(Color(0xFF666666))
                    // Vue源码: margin-top: 4px; - 描述上边距
                    marginTop(4f)
                }
            }
        }
        // Vue源码: </div> - 列表项容器结束
    }
    // Vue源码: </list-cell> - 列表项循环结束
}
// Vue源码: </scroll-view> - 滚动列表容器结束
```

##### 条件渲染逐行标记示例
```kotlin
// Vue源码: <div v-if="isLoading" class="loading-container"> - 加载状态条件渲染
vif({ ctx.isLoading }) {
    View {
        attr {
            // Vue源码: width: 100%; height: 100%; - 加载容器占满
            width(pagerData.pageViewWidth)
            height(pagerData.pageViewHeight)
            // Vue源码: display: flex; align-items: center; justify-content: center; - 加载容器居中
            allCenter()
            // Vue源码: background-color: rgba(0,0,0,0.1); - 加载遮罩背景
            backgroundColor(Color(0x1A000000))
        }
        
        // Vue源码: <div class="loading-spinner"></div> - 加载动画
        DJCLoading {
            attr {
                // Vue源码: width: 40px; height: 40px; - 加载动画尺寸
                size(40f)
            }
        }
    }
}
// Vue源码: </div> - 加载状态条件渲染结束

// Vue源码: <div v-else class="content-container"> - 内容容器条件渲染
velse {
    View {
        attr {
            // Vue源码: flex: 1; - 内容容器占满剩余空间
            flex(1f)
        }
        
        // 内容组件...
    }
}
// Vue源码: </div> - 内容容器条件渲染结束
```

##### 逐行标记规则要求

1. **每个UI组件必须标记对应的Vue元素**
   - 标记Vue标签名称和主要属性
   - 说明组件的功能用途

2. **每个样式属性必须标记对应的CSS属性**
   - 标记具体的CSS属性名和值
   - 说明样式的视觉效果

3. **每个事件绑定必须标记对应的Vue事件**
   - 标记Vue事件名称和处理函数
   - 说明事件的触发条件和处理逻辑

4. **每个数据绑定必须标记对应的Vue数据**
   - 标记Vue数据绑定语法
   - 说明数据的来源和用途

5. **复杂结构必须标记开始和结束**
   - 标记Vue标签的开始和结束
   - 保持代码结构的清晰对应关系

6. **条件和循环渲染必须标记Vue指令**
   - 标记v-if、v-for等Vue指令
   - 说明渲染条件和数据源

#### 5. 组件对应标记
- **Vue组件对应Kuikly组件时，必须在组件文件开头添加对应注释**
- **注释格式**：
```kotlin
/**
 * Vue组件对应: [Vue组件文件名]
 * 功能描述: [组件功能说明]
 * 迁移日期: [YYYY-MM-DD]
 * 迁移人员: [开发人员]
 */
```

#### 6. API接口对应标记
- **Vue的API调用对应Kuikly的网络请求时，必须添加对应注释**
- **注释格式**：`// Vue原始代码: [原始Vue API代码] - [接口描述]`
- **示例**：
```kotlin
// Vue原始代码: this.$api.getUserInfo().then(res => { this.userInfo = res.data }) - 获取用户信息接口
suspend fun fetchUserInfo() {
    val response = http.smartFetchAndCheckRes(
        urlKey = "/api/user/info",
        isPost = false
    )
}
```

#### 7. 数据结构对应标记
- **Vue的数据结构对应Kuikly的数据类型时，必须添加对应注释**
- **对于复杂的数据转换，需要详细说明转换逻辑**

#### 8. 迁移完整性检查
- **每个Vue文件迁移完成后，必须在Kuikly文件开头添加迁移完整性声明**
- **格式**：
```kotlin
/**
 * 迁移完整性声明:
 * Vue源文件: [Vue文件路径]
 * 迁移状态: 完整迁移/部分迁移
 * 未迁移功能: [如有未迁移功能，请列出]
 * 迁移验证: 已验证/待验证
 */
```

### 1. 目录结构建立
- 先熟悉vue页面目录结构，建立项目的kuikly目录结构
- 在 `shared/src/commonMain/kotlin/com/tencent/kuiklypolycity/page/` 下创建对应页面目录

### 2. 文件命名规范
- Vue页面的文件名称，需要保持和Kuikly页面的文件名称一致
- **Kuikly文件名称首字母大写，不包含下划线(_)**
- 例如：`user_profile.vue` → `UserProfile.kt`

### 3. 迁移顺序
- **先将Vue组件进行迁移，迁移完成后，再迁移Vue页面**
- 组件必须符合Kuikly的组件规范

### 4. 页面文件拆分规则
- **UI拆分，放在文件 `PageUI.kt` 中**
- **其他代码（逻辑、数据处理等），放在文件 `xxxx.kt` 中**

### 5. 组件文件拆分规则
- **组件不需要拆分**

## Kuikly文件夹创建规范

### 1. 页面文件夹创建

#### 创建位置
```
shared/src/commonMain/kotlin/com/tencent/kuiklypolycity/page/[页面名称]/
```

#### 文件夹命名规则
- 使用小写字母和下划线
- 与Vue页面目录名保持一致
- 例如：`activity_home`、`user_profile`、`task_center`

#### 标准页面目录结构
```
page/[页面名称]/
├── [页面名称].kt          # 主文件，包含页面逻辑、数据处理、生命周期
├── PageUI.kt              # UI构建文件，包含所有UI组件和布局
├── component/             # 页面专用组件目录（可选）
│   ├── [组件名].kt        # 页面内部组件
```

### 2. 组件文件夹创建

#### 公共组件位置
```
shared/src/commonMain/kotlin/com/tencent/kuiklypolycity/component/
```

#### 页面专用组件位置
```
shared/src/commonMain/kotlin/com/tencent/kuiklypolycity/page/[页面名称]/component/
```

## PageUI.kt与主文件对应关系

### 1. 主文件（如ActivityHome.kt）职责

#### 文件结构
```kotlin
@Page("页面路由名称")
internal class ActivityHome : BasePager() {
    // 1. 模块依赖声明
    private lateinit var eventModule: EventModule
    private lateinit var http: Http
    
    // 2. 响应式数据定义
    var isLoading by observable(ObservableThreadSafetyMode.NONE, false)
    var dataList by observableList<JSONObject>(ObservableThreadSafetyMode.NONE)
    
    // 3. 视图引用
    lateinit var refreshRef: ViewRef<RefreshView>
    
    // 4. 生命周期方法
    override fun created() { }
    override fun pageDidAppear() { }
    
    // 5. 业务逻辑方法
    private fun loadData() { }
    private fun handleUserAction() { }
    
    // 6. 事件处理方法
    fun onRefresh() { }
    fun onItemClick(item: JSONObject) { }
    
    // 7. UI构建入口（必须实现）
    override fun body(): ViewBuilder {
        return buildUI(this)
    }
}
```

#### 主要职责
- **页面注解**：使用 `@Page("路由名称")` 注解
- **继承基类**：继承 `BasePager()` 基础页面类
- **模块管理**：声明和初始化所需的模块依赖
- **数据管理**：定义响应式数据（observable、observableList）
- **生命周期**：实现页面生命周期方法
- **业务逻辑**：处理数据请求、状态管理、业务流程
- **事件处理**：处理用户交互事件
- **UI入口**：通过 `body()` 方法调用 `PageUI.kt` 中的 `buildUI()` 函数

### 2. PageUI.kt文件职责

#### 文件结构
```kotlin
/**
 * [页面名称]UI构建函数
 * 
 * 主要包含：
 * 1. 页面布局结构
 * 2. UI组件定义
 * 3. 样式设置
 * 4. 事件绑定
 */
fun buildUI(page: Pager): ViewBuilder {
    val ctx: ActivityHome = page as ActivityHome
    return {
        // UI组件构建
        View {
            attr {
                flex(1f)
                backgroundColor(Color(0xFFFFFFFF))
            }
            
            // 子组件
            NavBar { }
            List { }
            // ...
        }
    }
}
```

#### 主要职责
- **UI构建**：定义页面的完整UI结构
- **布局管理**：设置组件的布局属性（flex、padding、margin等）
- **样式定义**：设置颜色、字体、尺寸等视觉样式
- **事件绑定**：将UI事件绑定到主文件的处理方法
- **数据绑定**：将主文件的响应式数据绑定到UI组件
- **条件渲染**：使用 `vif`、`velseif` 等指令控制组件显示
- **列表渲染**：使用 `vforLazy` 等指令渲染动态列表

### 3. 数据流向关系

```
主文件 ←→ PageUI.kt
  ↑           ↓
数据/状态   UI组件
  ↑           ↓
业务逻辑 ←→ 用户交互
```

- **主文件 → PageUI.kt**：通过参数传递页面实例，提供数据和状态
- **PageUI.kt → 主文件**：通过事件回调，将用户操作传递给业务逻辑
- **响应式更新**：主文件数据变化自动触发UI重新渲染

## Kuikly组件开发规范

### 1. 组件文件结构

#### 标准组件文件模板
```kotlin
package com.tencent.kuiklypolycity.component

import com.tencent.kuikly.core.base.*
import com.tencent.kuikly.core.views.*

/**
 * [组件名称]组件
 * [组件功能描述]
 */
internal class Avatar : ComposeView<AvatarAttr, AvatarEvent>() {
    
    override fun createEvent(): AvatarEvent {
        return AvatarEvent()
    }

    override fun createAttr(): AvatarAttr {
        return AvatarAttr()
    }

    override fun body(): ViewBuilder {
        val ctx = this
        return {
            // UI构建逻辑
        }
    }
}

/**
 * 组件属性定义
 */
internal class AvatarAttr : ComposeAttr() {
    var src: String = ""              // 属性说明
    var size: Float = 36f             // 属性说明
}

/**
 * 组件事件定义
 */
internal class AvatarEvent : ComposeEvent() {
    var onClick: (() -> Unit)? = null // 事件说明
}

/**
 * 组件使用扩展函数
 */
internal fun ViewContainer<*, *>.Avatar(init: Avatar.() -> Unit) {
    addView(Avatar().apply(init))
}
```

### 2. 组件命名规范

#### 文件命名
- 使用 PascalCase（首字母大写的驼峰命名）
- 文件名与组件类名保持一致
- 例如：`Avatar.kt`、`UserInfoCard.kt`、`CustomCountdown.kt`

#### 类命名
- **组件类**：与文件名相同，如 `Avatar`
- **属性类**：组件名 + `Attr`，如 `AvatarAttr`
- **事件类**：组件名 + `Event`，如 `AvatarEvent`

### 3. 组件分类和存放位置

#### 公共组件（通用性强）
```
component/
├── Avatar.kt                    # 头像组件
├── UserInfoCard.kt             # 用户信息卡片
├── CustomCountdown.kt          # 倒计时组件
├── common/                     # 基础通用组件
│   ├── DJCActionSheet.kt       # 操作表单
│   ├── DJCList.kt             # 列表组件
│   ├── DJCLoading.kt          # 加载组件
│   ├── NavBar.kt              # 导航栏
│   └── TabSwitcher.kt         # 标签切换器
├── cmt/                        # 评论相关组件
│   ├── DJCCommentText.kt      # 评论文本
│   ├── FirstLevelComment.kt   # 一级评论
│   └── TuanShareComponent.kt  # 团购分享组件
└── native_view/                # 原生视图组件
    ├── DJCWebView.kt          # WebView组件
    └── gdt/                   # 广告相关组件
```

#### 页面专用组件
```
page/[页面名称]/component/
├── [组件名].kt                 # 页面专用组件
└── UI/                        # 复杂组件的UI分离（可选）
    └── [组件名]UI.kt          # 组件UI构建文件
```

### 4. 组件开发最佳实践

#### 属性设计原则
- **必需属性**：无默认值，使用时必须设置
- **可选属性**：提供合理的默认值
- **类型安全**：使用强类型，避免 `Any` 类型
- **命名清晰**：属性名要能清楚表达用途

#### 事件设计原则
- **回调函数**：使用 `(() -> Unit)?` 形式
- **参数传递**：需要参数时使用 `((参数类型) -> Unit)?`
- **命名规范**：使用 `on` 前缀，如 `onClick`、`onValueChange`

#### UI构建原则
- **性能优化**：避免不必要的重新渲染
- **样式一致性**：遵循设计规范

## 开发流程指南

### 1. Vue到Kuikly迁移完整流程

#### 步骤1：分析Vue页面
```
1. 分析Vue页面的功能需求
2. 识别页面中使用的组件
3. 梳理数据流和状态管理
4. 确定API接口和数据结构
5. 分析页面路由和参数传递
```

#### 步骤2：创建Kuikly目录结构
```bash
# 在page目录下创建页面文件夹
mkdir shared/src/commonMain/kotlin/com/tencent/kuiklypolycity/page/[页面名称]

# 创建必要的文件
touch [页面名称].kt
touch PageUI.kt

# 如果需要页面专用组件
mkdir component
mkdir data
```

#### 步骤3：迁移组件（优先）
```
1. 识别Vue组件中的props → 转换为Kuikly组件的Attr，如果熟悉是需要更新UI，请用observer定义属性
2. 识别Vue组件中的events → 转换为Kuikly组件的Event
3. 迁移Vue组件的template → 转换为Kuikly组件的body()
4. 迁移Vue组件的style → 转换为Kuikly的样式设置
```

#### 步骤4：迁移页面主文件
```
1. 创建页面类，继承BasePager
2. 添加@Page注解，设置路由
3. 迁移Vue的data → 转换为observable响应式数据
4. 迁移Vue的methods → 转换为页面方法
5. 迁移Vue的生命周期 → 转换为Kuikly生命周期
6. 处理模块依赖和API调用
```

#### 步骤5：构建PageUI
```
1. 分析Vue的template结构
2. 转换为Kuikly的ViewBuilder结构
3. 设置布局属性和样式
4. 绑定数据和事件
5. 处理条件渲染和列表渲染
```

#### 步骤6：测试和优化
```
1. 只能执行脚本./gradlew :shared:packLocalJSBundleRelease验证编译是否出错
2. 查看是否有报错
3. 修复报错，重复以上步骤
```

### 2. 常用工具类和模块

#### 网络请求
```kotlin
// 使用Http模块进行网络请求
private val http = Http()

// 方法一：使用smartFetch配合succRes（推荐用于需要自定义错误处理的场景）
suspend fun fetchDataWithCustomHandling() {
    val response = http.smartFetch(
        urlKey = your_api_url, // 直接将vue页面中的api地址，复制到这里
        isPost = false,
        param = JSONObject().apply {
            put("key", "value")
        },
        useCache = false
    )
    
    // 使用succRes进行数据解析，会自动解析data字段
    val processedData = http.succRes(response, "请求描述", noNeedPop = true)
    if (processedData != null) {
        // 处理成功的数据
        val actualData = processedData.opt("data") // 获取解析后的data数据
        console.info("请求成功: $actualData")
    } else {
        // 处理失败情况
        console.error("请求失败")
    }
}

// 方法二：使用smartFetchAndCheckRes（推荐用于简单场景）
suspend fun fetchDataSimple() {
    val processedData = http.smartFetchAndCheckRes(
        urlKey = your_api_url, // 直接将vue页面中的api地址，复制到这里
        isPost = false,
        param = JSONObject().apply {
            put("key", "value")
        },
        useCache = false
    )
    
    if (processedData != null) {
        // smartFetchAndCheckRes已经自动解析了data字段
        val actualData = processedData.opt("data") // 获取解析后的data数据
        console.info("请求成功: $actualData")
    } else {
        console.error("请求失败")
    }
}
```

#### 路由跳转
```kotlin
// 使用EventModule进行页面跳转
private lateinit var eventModule: EventModule

// 跳转到其他页面
eventModule.openURL("your_url_here")

// 示例：跳转到具体URL
eventModule.openURL("https://example.com/page?param1=value1&param2=value2")
```

#### 数据存储
```kotlin
// 使用Storage进行本地存储
Storage.setItem("key", "value")
val value = Storage.getItem("key")
```

#### 日志输出
```kotlin
// 使用console进行日志输出
console.log("debug message")
console.error("error message")
```

### 3. 样式和布局最佳实践

#### 响应式布局
```kotlin
View {
    attr {
        flex(1f)                    // 弹性布局
        flexDirection(FlexDirection.COLUMN) // 垂直排列
        justifyContentCenter()      // 主轴居中
        alignItemsCenter()          // 交叉轴居中
        padding(16f)                // 内边距
        margin(8f)                  // 外边距
    }
}
```

#### 颜色使用
```kotlin
// 使用十六进制颜色值
Text {
    attr {
        color(Color(0xFF333333))           // 黑色文字
        backgroundColor(Color(0xFFf5f5f5)) // 浅灰背景
    }
}

// 使用项目中定义的颜色扩展属性
import com.tencent.kuiklypolycity.utils.value.C33  // 文字颜色
import com.tencent.kuiklypolycity.utils.value.F5   // 背景颜色

Text {
    attr {
        color(C33)                  // 使用预定义颜色
        backgroundColor(F5)
    }
}
```

#### 字体和尺寸
```kotlin
Text {
    attr {
        fontSize(16f)               // 字体大小
        fontWeight(FontWeight.BOLD)    // 字体粗细
        lineHeight(24f)             // 行高
        textAlign(TextAlign.CENTER)   // 文字对齐
    }
}
```

### 4. 性能优化建议

#### 列表渲染优化
```kotlin
// 使用vforLazy进行懒加载列表渲染
List {
    vforLazy(dataList) { item, index ->
        ItemView {
            attr {
                // 设置固定高度，提升性能
                height(80f)
            }
            // 组件内容
        }
    }
}
```

#### 图片加载优化
```kotlin
Image {
    attr {
        src(imageUrl)
        resizeCover()               // 图片缩放模式
    }
}
```

#### 状态管理优化
```kotlin
// 合理使用observable，避免不必要的重新渲染
var isLoading by observable(ObservableThreadSafetyMode.NONE, false)

```

### 5. 调试和错误处理

#### 调试技巧
```kotlin
// 使用console.log进行调试
console.log("Current state: isLoading=$isLoading, dataSize=${dataList.size}")

// 在关键位置添加日志
override fun pageDidAppear() {
    super.pageDidAppear()
    console.log("Page appeared: ${this::class.simpleName}")
}
```

### 6. 代码规范和注释

#### 文件头注释
```kotlin
/**
 * [页面/组件名称]
 * 源代码文件：[文件名.vue tempate] 或者 [文件名.vue script]
 * 功能描述：
 * 1. 主要功能1
 * 2. 主要功能2
 * 
 * 作者：[开发者姓名]
 */
```

#### 方法注释
```kotlin
/**
 * 加载页面数据
 * 源代码文件：[文件名.vue] + 源代码方法名
 * 
 * @param refresh 是否为刷新操作
 * @param page 页码，默认为1
 */
private fun loadData(refresh: Boolean = false, page: Int = 1) {
    // 方法实现
}
```

## Vue组件到Kuikly组件对应规则

### 1. isiPhoneX转换对应规则

#### Vue中的isiPhoneX使用方式
```javascript
// Vue原始代码: data中定义
data: function () {
    return {
        isiPhoneX: false
    }
},

// Vue原始代码: created生命周期中初始化
created: function () {
    let self = this;
    self.isiPhoneX = !!comm.isIphoneX();
},

// Vue原始代码: 模板中使用
<div v-if="isiPhoneX" style="width: 750rpx; height: 68rpx; background-color: white"></div>
```

#### Kuikly中的isiPhoneX对应实现

##### 1. 数据定义
```kotlin
// Vue原始代码: isiPhoneX: false - iPhone X设备判断标识
var isiPhoneX by observable(ObservableThreadSafetyMode.NONE, false)
```

##### 2. 初始化方式
```kotlin
// Vue原始代码: self.isiPhoneX = !!comm.isIphoneX() - 获取设备类型
override fun created() {
    super.created()
    // 方式1: 通过AppInfo模块获取
    val appInfo = acquireModule<AppInfoModule>(AppInfoModule.MODULE_NAME)
    isiPhoneX = appInfo.isIphoneX()
    
    // 方式2: 通过pageData直接获取
    isiPhoneX = pageData.isIphoneX
    
    // 方式3: 通过AppInfo工具类获取
    val app = AppInfo()
    isiPhoneX = app.isIphoneX()
}
```

##### 3. UI中使用
```kotlin
// Vue原始代码: <div v-if="isiPhoneX" style="width: 750rpx; height: 68rpx; background-color: white"></div> - iPhone X底部适配
vif({ ctx.isiPhoneX }) {
    View {
        attr {
            width(pagerData.pageViewWidth) // 对应750rpx
            height(34f) // 对应68rpx减半
            backgroundColor(Color(0xFFFFFFFF))
        }
    }
}
```

##### 4. 组件中使用
```kotlin
// 在CommShimBottom组件中的使用示例
internal class CommShimBottomAttr : ComposeAttr() {
    var needIpx: Boolean = true // 是否需要iPhone X适配
}

// 组件内部实现
val ipxHeight = if (attr.needIpx && pagerData.isIphoneX) 54f else 0f
View {
    attr {
        height(ipxHeight)
        backgroundColor(Color(0xFFFFFFFF))
    }
}
```

#### isiPhoneX转换规则总结

| Vue写法 | Kuikly写法 | 说明 |
|---------|------------|------|
| `isiPhoneX: false` | `var isiPhoneX by observable(ObservableThreadSafetyMode.NONE, false)` | 响应式数据定义 |
| `comm.isIphoneX()` | `pageData.isIphoneX` 或 `AppInfo().isIphoneX()` | 获取设备类型 |
| `v-if="isiPhoneX"` | `vif({ ctx.isiPhoneX })` | 条件渲染 |
| `height: 68rpx` | `height(34f)` | 高度单位转换（rpx除以2） |
| `width: 750rpx` | `width(pagerData.pageViewWidth)` | 全屏宽度 |

### 2. Vue scroll-view对应Kuikly List组件规则

#### Vue scroll-view的使用方式
```vue
<!-- Vue原始代码: 基础滚动视图 -->
<scroll-view class="activity-list" :style="{'height':'600px'}">
    <list-cell v-for="(item, index) in activityItems" :key="index">
        <div class="activity-item" @click="goToDetail(item)">
            <!-- 活动内容 -->
        </div>
    </list-cell>
</scroll-view>

<!-- Vue原始代码: 带下拉刷新的滚动视图 -->
<scroll-view 
    class="scroll-container" 
    @scrolltolower="loadMore"
    @scroll="onScroll">
    <!-- 列表内容 -->
</scroll-view>
```

#### Kuikly List组件对应实现

##### 1. 基础List组件使用
```kotlin
// Vue原始代码: <scroll-view class="activity-list"> - 基础滚动列表
List {
    attr {
        height(300f) // 对应600px减半
        flex(1f)
        showScrollerIndicator(false) // 隐藏滚动指示器
        backgroundColor(Color(0xFFFFFFFF))
    }
    
    // Vue原始代码: v-for="(item, index) in activityItems" - 列表项循环渲染
    vforLazy({ ctx.activityItems }) { item, index, _ ->
        View {
            attr {
                width(pagerData.pageViewWidth)
                padding(16f)
            }
            
            event {
                // Vue原始代码: @click="goToDetail(item)" - 点击事件
                click {
                    ctx.goToDetail(item)
                }
            }
            
            // 活动内容组件
        }
    }
}
```

##### 2. 带下拉刷新的DJCList组件
```kotlin
// Vue原始代码: scroll-view with refresh functionality - 带刷新功能的滚动视图
DJCList<ActivityModel>(
    attr = {
        data.addAll(ctx.activityList) // 数据源
        hasNext = ctx.hasMoreData // 是否有更多数据
        noDataText = "暂无活动数据"
        noDataImage = "no_data_image_url"
    },
    event = {
        // Vue原始代码: 下拉刷新逻辑
        onRefresh {
            ctx.refreshData()
        }
        // Vue原始代码: @scrolltolower="loadMore" - 上拉加载更多
        loadMore {
            ctx.loadMoreData()
        }
    }
) { item, index, _ ->
    // Vue原始代码: list-cell内容 - 列表项内容
    View {
        attr {
            width(pagerData.pageViewWidth)
            padding(16f)
        }
        
        event {
            click {
                ctx.onItemClick(item)
            }
        }
        
        // 列表项UI内容
    }
}
```

##### 3. 带RefreshView的List组件
```kotlin
// Vue原始代码: scroll-view with manual refresh control - 手动刷新控制
List {
    attr {
        flex(1f)
        showScrollerIndicator(false)
    }
    
    // 下拉刷新组件
    Refresh {
        ref {
            ctx.refreshRef = it
        }
        attr {
            height(70f)
            allCenter()
        }
        
        event {
            // Vue原始代码: 刷新状态变化处理
            refreshStateDidChange {
                when (it) {
                    RefreshViewState.IDLE -> {
                        ctx.refreshState = 0
                    }
                    RefreshViewState.PULLING -> {
                        ctx.refreshState = 1
                    }
                    RefreshViewState.REFRESHING -> {
                        ctx.refreshState = 2
                        ctx.onRefresh()
                    }
                }
            }
        }
        
        // 刷新UI内容
    }
    
    // Vue原始代码: v-for列表项
    vforLazy({ ctx.dataList }) { item, index, _ ->
        // 列表项内容
    }
}
```

#### scroll-view到List组件转换规则总结

| Vue scroll-view特性 | Kuikly List对应实现 | 说明 |
|-------------------|-------------------|------|
| `<scroll-view>` | `List { }` | 基础滚动容器 |
| `v-for="item in list"` | `vforLazy({ ctx.list }) { item, index, _ -> }` | 列表项循环渲染 |
| `@scrolltolower` | `loadMore { }` 在DJCList中 | 滚动到底部加载更多 |
| `@scroll` | List的滚动事件 | 滚动事件监听 |
| `height: 600px` | `height(300f)` | 高度设置（px除以2） |
| 下拉刷新 | `Refresh { }` 或 DJCList的 `onRefresh` | 下拉刷新功能 |
| `list-cell` | `vforLazy`中的View容器 | 列表项容器 |
| 无数据状态 | DJCList的 `noDataText`、`noDataImage` | 空数据展示 |

##### 组件选择指南

1. **简单列表展示**：使用基础 `List` 组件
2. **需要下拉刷新和上拉加载**：使用 `DJCList` 组件
3. **自定义刷新样式**：使用 `List` + `Refresh` 组合
4. **复杂交互需求**：基于 `List` 自定义实现

## 总结

本文档详细说明了Vue到Kuikly的迁移规范，包括：

1. **项目结构**：清晰的目录组织和文件命名规范
2. **文件职责**：PageUI.kt与主文件的明确分工
3. **组件开发**：标准的组件开发模式和最佳实践
4. **开发流程**：完整的迁移步骤和开发指南
5. **isiPhoneX适配**：设备类型判断和UI适配规则
6. **scroll-view转换**：Vue滚动视图到Kuikly List组件的对应规则
7. **性能优化**：提升应用性能的建议和技巧
8. **代码规范**：保持代码质量的规范和标准

遵循这些规范可以确保迁移过程的一致性和代码质量，提高开发效率和维护性。

