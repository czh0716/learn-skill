# 会话示例

> 这是一次典型学习会话的完整对话流程，展示了各验收标准（费曼检验、POGIL探索、讲练同步、保护效应、30秒总结、L1-L4分级、主动回忆、交错学习等）的实际体现。被 [SKILL.md](../SKILL.md) 附录引用。

背景: 用户在学习 JavaScript Promise，当前是里程碑2的第3次会话。上次学了 Promise 基本用法。

---

**Step 1 — 回顾连接** (主动回忆)

> Skill: "欢迎回来！这是我们学 Promise 的第3次会话。上次我们学了 Promise 的基本链式调用 `.then()`。你还记得 `.then()` 的回调函数接收的是什么吗？先想想，不用查。"
>
> 用户: "嗯...接收的是上一个 Promise resolve 出来的值？"
>
> Skill: "对。那如果 `.then()` 里又 return 了一个 Promise 呢？这就是我们今天要深入的部分。上次的复习节点是+1天，你已经在综合练习里遇到过了——今天+3天，我们会在最后的综合练习里再见到它。"

**Step 2 — 学习循环** (POGIL 探索, 讲练同步)

> Skill: "先来看一段代码。你能运行一下吗？"
>
> （给出一段用了 `.then()` 链但没有 `.catch()` 的代码，故意让一个中间步骤失败）
>
> Skill: "运行后你看到了什么？"
>
> 用户: "报错了，但错误信息不太清楚..."
>
> Skill: "好，你观察到一个重要现象：Promise 链中如果中间出错但没有 `.catch()`，错误会被吞掉。这就是我们接下来要探索的——Promise 的错误处理。"
> *(POGIL: 先探索现象，再引入概念)*
>
> Skill: "Promise 的错误处理有3种方式：① `.catch()` ② `.then()` 的第二个参数 ③ `try/catch` + `async/await`。我们先看 `.catch()`。你试试在这段代码末尾加上 `.catch(err => console.error('捕获到:', err))`，再运行。"
> *(讲练同步: 讲完立即动手)*
>
> Skill: "现在用最简单的话总结一下 `.catch()` 在 Promise 链中的作用？不用术语。"
> *(费曼检验)*

之后用同样的微循环方式讲解另外两种错误处理方式。

**Step 2 末尾 — 交错综合** (交错学习)

> Skill: "好，现在你知道了3种 Promise 错误处理方式。它们有什么不同？什么场景用 `.catch()`，什么场景用 `try/catch`？"
>
> *(交错学习: 引导用户对比，而非分别练习)*

**Step 3 — 综合练习** (L1-L4 分级)

> Skill: "来做一个综合练习。这里有一个包含了文件读取和网络请求的异步流程，有些步骤可能失败。你需要：① 先用 `.catch()` 处理错误 (L2) ② 然后改写成 `async/await` + `try/catch` 版本 (L3)。"
>
> *(交错学习: 练习混合了本次的 Promise 错误处理 + 上次的异步流程)*

用户写代码。如果用户说"太简单了"...(太简单处理)

> Skill: "好，那你试试 L4 挑战：实现一个 `retry(fn, times)` 函数——Promise 失败后自动重试指定次数，每次重试间隔递增。给你5分钟？"

**Step 4 — 总结展望** (30秒总结, 保护效应)

> Skill: "时间差不多了。用30秒总结一下，今天关于Promise错误处理，你学到了什么？"
> *(30秒总结)*
>
> 用户: "三种错误处理方式..."
>
> Skill: "不错。最后，假设你的同事小明刚学了 Promise，想了解错误处理——你怎么教他？"
> *(保护效应)*
>
> Skill: "下次我们学 Promise 的静态方法——`Promise.all`、`Promise.race`，以及它们在真实项目中的应用。今天的掌握度你给自己打几分(1-5)？"
>
> *(记录掌握度，更新 plan.md + 写入 archive/)*

在整个会话中，Skill 在用户写代码时引导了一次 Copilot 功能 (Copilot 引导):
> "你现在可以右键这段代码，选 Copilot → Explain，看看 AI 怎么解释这个 `.catch()` 的位置。先自己解释，再对比。"

---

## 对应归档示例

> 以下是对应上述会话的归档文件。归档是详细学习笔记，不是摘要。写作标准：学员 2 周后翻开就能独立回顾，不需要翻聊天记录。

```
# Session 3 — 2026-03-18

## 基本信息
- **学习时长**: 45 分钟（完整会话）
- **里程碑**: M2 JavaScript 异步编程
- **学习主题**: Promise 错误处理（.catch()、.then() 第二个参数、try/catch + async/await）

---

## 学习过程

### 1. Promise 错误处理的三种方式

**教练引入**: 给一段没有 .catch() 的 Promise 链代码，故意让中间步骤失败——让我先观察现象再引出概念。

**我的初始理解**: 之前只用过 .then()，以为 Promise 成功就继续，失败就不执行，没想过要处理错误。

**精讲内容**: Promise 错误处理有 3 种方式：① `.catch()` — 链式捕获 ② `.then(onFulfilled, onRejected)` — 分别处理成功/失败 ③ `try/catch` + `async/await` — 同步风格写法。

**跨技术概念映射**:

| 已知技术 | 目标技术 | 关键差异 |
|----------|---------|---------|
| Node.js 回调 `(err, result)` | `.catch(err)` | 回调错误参数分叉 vs Promise 链统一捕获 |
| Express 错误中间件 `next(err)` | `.catch(err)` | 都是"错误逐级传递"模式，但 Express 有 4 参数签名限制 |
| Vue `try/catch` 包裹 API 调用 | `async/await` + `try/catch` | 结构完全一致，但 Promise 的 reject 必须被 catch 否则 unhandled rejection |

**动手实验**:

```javascript
// 故意让中间步骤失败，看看会发生什么
fetch('/api/user')
  .then(res => res.json())
  .then(data => {
    throw new Error('数据库写入失败');  // 故意失败
  })
  .then(() => console.log('这行不会执行'))
  .catch(err => console.error('捕获到:', err.message));
```

**运行结果**:
```
捕获到: 数据库写入失败
```

**我的发现**: 加了 .catch() 之后，不管哪个环节出错都能捕获到。而且 .catch() 后面的 .then() 不会执行——这个以前理解错了，以为 catch 之后会继续。

**你知道吗**: Node.js 15+ 引入了 unhandledRejection 全局事件。如果没有 .catch()，Promise 的 reject 会触发这个事件，Node 默认行为是 warning，未来版本会直接 crash 进程。所以**生产代码所有 Promise 都该有 .catch()**。

---

### 2. 三种方式的选择场景

**精讲内容**:
- `.catch()`: 适合 Promise 链式调用，统一捕获链上所有错误
- `.then(onFulfilled, onRejected)`: 适合需要区分"当前这一步的成功/失败"的场景
- `try/catch` + `async/await`: 适合需要条件分支和多层 try 嵌套的场景

**动手实验**:

```javascript
// 对比三种写法
// 方式1: .catch()
fetchData().then(process).catch(handleError);

// 方式2: .then() 的两个参数
fetchData().then(process, handleError);  
// ⚠️ 这里 process 自己的错误不会被 handleError 捕获！

// 方式3: try/catch
async function main() {
  try {
    const data = await fetchData();
    const result = await process(data);
    return result;
  } catch (err) {
    handleError(err);
  }
}
```

**运行结果**: 方式2 的问题——process 函数内部的错误不会被 handleError 捕获（因为 onRejected 只处理 fetchData 的 reject）。

**我的发现**: 原来 `.then(onFulfilled, onRejected)` 不一定等于 `.then(onFulfilled).catch(onRejected)`！这个是细节中的细节。

---

## 费曼检验

**方式**: 方式①口头解释

**学员输出**: ".catch() 就像一个安全网，Promise 不管在哪一步摔了，都会被这个安全网接住。跟 Express 的错误处理中间件一样——只要在最后面挂一个，前面所有路由的错误都会被收集。"

**检验结果**: ✅ 通过——用自己的类比（Express 中间件）准确解释，且提到了"链上任何位置"这个关键点。

---

## 本节课学会的

- Promise 错误处理三种方式各自适用场景
- `.catch()` 统一捕获链上所有错误，推荐作为默认选择
- `.then(onFulfilled, onRejected)` 只捕获上一个 Promise 的 reject，不捕获 onFulfilled 里的错误——这是个陷阱
- `try/catch` + `async/await` 写起来跟同步代码一样，适合复杂条件分支

## 还不确定的

- Promise.all 里如果有一个 reject，其他 Promise 还在执行吗？
- 微任务队列和错误传播的关系？（感觉讲快了一点点）

## 踩到的坑

| 遇到的问题 | 怎么解决的 | 经验教训 |
|-----------|-----------|---------|
| .catch() 放在中间位置时，后面的 .then() 还会执行 | 写代码实测——.catch() 后面的 .then() 确实会执行（因为 .catch() 返回新 Promise 且默认 resolve） | .catch() 放在链末尾才能兜底所有错误 |

## 学习资料

- [MDN — Promise.prototype.catch()](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise/catch) — 官方文档，看 "Description" 部分就行
- [JavaScript.info — Promise 错误处理](https://javascript.info/promise-error-handling) — 有图解 .catch() 在链中的位置影响
- [Node.js — unhandledRejection 事件](https://nodejs.org/api/process.html#event-unhandledrejection) — 了解就行，实际项目用 lint 规则 enforce

## 下次想问的

- Promise.all 的错误处理——一个失败全失败？
- Promise.race 和 Promise.any 什么时候用？

## 掌握度

4/5 — 三种方式都会用，但方式2的陷阱在实际项目中容易踩——需要更多练习来内化选择直觉。

## 进度

M2 JavaScript 异步 [████████░░░░░░░░░░░░] 60%
```
