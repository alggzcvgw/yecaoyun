# AI 编程工具深度评测：ChatGPT、Copilot、Cursor、New Bing 谁更适合开发者？

## 引言

人工智能技术正在深刻地改变着软件开发行业。作为一名开发者，我既为 AI 带来的效率提升感到兴奋，也担忧它是否会颠覆传统的工作流程。但无论如何，我们需要积极拥抱 AI 时代，做“未来世界的幸存者”。

在深度体验了 GitHub Copilot、ChatGPT 等工具后，我对这些 AI 辅助开发工具进行了横向评测。本文旨在帮助开发者快速筛选出适合自己的 AI 工具。相信我，这些工具绝对能提升你的开发效率。

**评测工具：**
- GitHub Copilot
- ChatGPT (GPT-3.5)
- New Bing
- Cursor.so

这些工具可以结合使用，以最大化提升开发效率。文章最后将给出总结和建议。

## GitHub Copilot

GitHub Copilot 是由 GitHub 和 OpenAI 联合开发的人工智能代码辅助工具，基于 OpenAI 的 GPT 技术。它能为开发者提供实时代码提示和生成功能，类似于一个 AI 助手，帮助开发者更高效地编写代码。

目前 GitHub Copilot 基于 GPT-3 模型，能够分析上下文并根据现有代码和注释推断出应编写的代码。它支持多种编程语言（如 Python、JavaScript、TypeScript、Ruby 等），并能与主流 IDE 和文本编辑器无缝集成。

### 使用体验

我深度使用 Copilot 近一个月，总结出以下几点体验：
- **熟悉语言：** 帮助减少重复模板代码的编写。
- **不熟悉语言：** 能够准确推断意图，生成代码，省去查询 API 的时间。
- **生成片段：** 擅长根据当前代码生成片段，但很难从零开始生成整段代码，且生成的代码通常需要手动修改。

#### 常用功能
1. **根据上下文生成代码**  
   根据函数名、类名、注释推断代码意图，自动填充代码。

   ![上下文生成代码](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/15b0f7b411f74c7583be6ee0b2ec955a~tplv-k3u1fbpfcp-zoom-1.image)

2. **根据代码生成注释**  
   自动理解代码并生成注释，只需输入 `//` 前缀。

   ![生成注释](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/90bb6ec753c44bf0ac85b1ad97896743~tplv-k3u1fbpfcp-zoom-1.image)

3. **帮助命名变量**  
   为变量提供合适的命名，节省开发时间。

   ![命名变量](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/665fe141dc9f4c14b025747386723f42~tplv-k3u1fbpfcp-zoom-1.image)

4. **代码讨论**  
   支持在代码中与 Copilot 讨论代码逻辑，总结上下文并提供合理建议。

   ![代码讨论](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/749ba89594f34bc5954377811e0faf71~tplv-k3u1fbpfcp-zoom-1.image)

### 编码能力

#### 单例模式实现
Copilot 自动生成私有变量、构造方法和获取单例的方法。通过提示，它补全了双重检查锁。

   ![单例模式](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/5313952c98f04c00bf641add8169ad98~tplv-k3u1fbpfcp-zoom-1.image)

#### 项目代码补全
Copilot 根据现有代码补全方法，使用上下文信息推断代码逻辑，生成的代码质量较高。

### 不足之处
- **隐私问题：** 代码通过 HTTPS 传输到云端，国内开发环境可能受限。
- **复杂逻辑：** 对复杂代码的理解能力有限，擅长处理公开资料多的代码段落。

## ChatGPT

ChatGPT 是一款基于 GPT 模型的聊天机器人，能够进行自然语言对话并理解代码。它通过大量代码相关文本的训练，具备一定的代码理解和生成能力。

### 编码能力

#### 单例模式实现
ChatGPT 生成了双重检查锁的单例代码，并解释了其原理。继续追问后，它优化了代码并加入了 `volatile` 关键字。

java
public class Singleton {
    private static volatile Singleton instance;
    private Singleton() {}
    public static Singleton getInstance() {
        if (instance == null) {
            synchronized (Singleton.class) {
                if (instance == null) {
                    instance = new Singleton();
                }
            }
        }
        return instance;
    }
}


#### Kotlin + Reactor 并发接口设计
ChatGPT 用 Reactor 框架实现了并发处理，但初始代码未保证顺序，后续通过 `flatMapSequential` 解决了问题。

kotlin
fun processStrings(strings: List<String>): List<String> {
    return Flux.fromIterable(strings)
        .flatMapSequential { str ->
            Mono.fromCallable {
                str + str
            }.subscribeOn(Schedulers.parallel())
        }
        .collectList().block() ?: emptyList()
}


### 不足之处
- 对复杂代码设计的处理能力有限。
- 无法全程辅助编码，缺乏项目上下文支持。

## New Bing

New Bing 是 ChatGPT 与 Bing 搜索引擎结合的产物，能够基于网络信息提供更全面的回答。

### 编码能力
New Bing 在单例模式和 Kotlin 并发接口设计中的表现与 ChatGPT 类似。但由于依赖搜索引擎，容易出现错误结果。

### 不足之处
- 与 ChatGPT 相比，错误率更高，尤其在复杂代码设计中。
- 同样缺乏项目上下文支持。

## Cursor.so

Cursor.so 是 OpenAI 推出的一款 IDE，内置了类似 GitHub Copilot 的功能，并且免费使用。

### 编码能力
Cursor.so 在单例模式和代码补全测试中表现良好，但服务不稳定，且基础功能缺失。

### 不足之处
- **服务不稳定：** 经常出现长时间等待或错误。
- **功能缺失：** 不支持插件和版本控制，开发大型项目体验较差。

## 总结

**GitHub Copilot：**
- **优点：** 自动生成代码，支持多种语言，获取项目上下文能力强。
- **缺点：** 隐私问题。

**ChatGPT 和 New Bing：**
- **优点：** 随时随地可用，是谷歌搜索的替代品。
- **缺点：** 缺乏项目上下文支持，复杂代码理解能力有限。

**Cursor.so：**
- **优点：** 免费体验 AI 辅助编程。
- **缺点：** 功能缺失，服务不稳定。

👉 [WildCard | 一分钟注册，轻松订阅海外线上服务](https://bbtdd.com/WildCard)

**一句话总结：** 结合 GitHub Copilot 和 ChatGPT，是提升开发效率的最佳选择。如果暂时不想支付 Copilot 的费用，可以先使用 ChatGPT。Cursor.so 目前体验欠佳，建议等待后续版本优化。