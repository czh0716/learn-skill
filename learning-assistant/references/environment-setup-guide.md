# 阶段 0：环境准备指南

> 零基础学习者面对的第一个障碍往往不是编程概念，而是"怎么运行代码"。本指南帮助学习者在进入正式学习前完成环境搭建，消除"无从下手"的恐惧。

## 目录

1. [核心原则](#1-核心原则)
2. [路径 A：在线环境（推荐零基础起步）](#2-路径-a在线环境推荐零基础起步)
3. [路径 B：本地环境](#3-路径-b本地环境)
4. [常见问题安抚](#4-常见问题安抚)
5. [环境验证清单](#5-环境验证清单)

---

## 1. 核心原则

- **先跑起来，再理解** — 不需要理解每一行配置，Hello World 能跑就行
- **在线环境优先** — 零基础前 1-2 周建议用在线 playground，降低认知负荷
- **逐步迁移到本地** — 当用户能独立写简单程序（L2 水平）时，再引导安装本地环境
- **终端不是魔法** — 强调"它只是一个用文字操控电脑的工具，刚开始不需要理解所有命令"

---

## 2. 路径 A：在线环境（推荐零基础起步）

### 通用在线 Playground

| 平台 | 适合 | 特点 |
|------|------|------|
| [CodePen](https://codepen.io) | HTML/CSS/JS | 即时预览，前端入门首选 |
| [CodeSandbox](https://codesandbox.io) | React/Vue/全栈 | 完整 VS Code 体验，支持 npm |
| [StackBlitz](https://stackblitz.com) | 前端框架 | 自动热更新，Node.js 环境 |
| [Replit](https://replit.com) | 通用（多语言） | 支持 Python/Node/Java 等，一键运行 |
| [Python Tutor](https://pythontutor.com) | Python/Java/C/C++/JS | **执行过程可视化**，理解程序运行流程 |

### 引导话术

> "不用安装任何东西，打开浏览器就行。我们先在网页上写代码——等你熟悉了基本语法，我们再来搭本地环境。来，打开 [Replit](https://replit.com)，点 Create Repl，选 Python。"

---

## 3. 路径 B：本地环境

### 3.1 终端入门

**Windows 用户**:
- 按 `Win + R`，输入 `powershell`，回车
- 或者 VS Code 中按 `` Ctrl+` `` 打开内置终端
- 第一个命令：`pwd`（显示当前位置）+ `ls`（列出文件）

**macOS 用户**:
- `Cmd + Space` 搜索 `Terminal`
- 或 VS Code 中 `` Ctrl+` ``

**安抚话术**:
> "终端看起来吓人，但它只是一个文字版的文件管理器。你日常用鼠标点来点去做的事（打开文件夹、新建文件、删除文件），终端里都是敲一行字搞定。我们慢慢来，这节课只需要记住 3 个命令。"

### 3.2 VS Code 安装

1. 从 [code.visualstudio.com](https://code.visualstudio.com) 下载安装
2. 必装插件（学习用）：Prettier（格式化）、Live Preview（预览）、对应语言的官方插件
3. 用 `code .` 命令从终端打开当前目录

### 3.3 按语言的环境搭建

**Python**:
1. [python.org](https://python.org) 下载安装（安装时勾选"Add Python to PATH"）
2. 验证：终端输入 `python --version`
3. 第一个程序：创建 `hello.py`，写入 `print("Hello, World!")`，终端运行 `python hello.py`

**JavaScript/Node.js**:
1. [nodejs.org](https://nodejs.org) 下载 LTS 版本
2. 验证：终端输入 `node --version`
3. 第一个程序：终端输入 `node` 进入 REPL，输入 `console.log("Hello, World!")`

**Java**:
1. [adoptium.net](https://adoptium.net) 下载 JDK
2. 验证：终端输入 `java --version`
3. 第一个程序：创建 `Hello.java`，终端 `javac Hello.java && java Hello`

### 3.4 Git 安装（可选，建议在里程碑 2-3 时引入）

1. [git-scm.com](https://git-scm.com) 下载安装
2. 验证：`git --version`
3. 基本配置：`git config --global user.name "你的名字"` + `git config --global user.email "你的邮箱"`

---

## 4. 常见问题安抚

| 用户反馈 | 回应策略 |
|---------|---------|
| "我连终端是什么都不知道" | "没关系，它只是个用文字操控电脑的工具。你不需要一开始就理解所有东西——就像开车不需要先懂发动机原理。" |
| "安装好复杂，我怕搞坏电脑" | "编程环境的安装都是可逆的——装错了卸载重来就行，不会损坏你的系统。我们先从不需要安装的在线版本开始。" |
| "报错了怎么办？" | "报错是编程中最正常的事。每次报错都是学习机会，我们一起来看它说了什么。90% 的环境错误都是路径或版本问题，很容易搜到解决方案。" |
| "为什么要用命令行，不能用鼠标吗？" | "可以先用鼠标操作，但命令行在编程中有独特的效率优势。我们不急，等你写了几次代码后再慢慢引入。" |

---

## 5. 环境验证清单

学习者在进入第一个正式里程碑前，应能完成：

- [ ] 能打开终端/命令行（本地）或打开在线 playground
- [ ] 能创建并运行一个 Hello World 程序
- [ ] 能修改程序中的文字并重新运行，看到输出变化
- [ ] 知道如何查看报错信息（不求看懂，但要知道报错在哪显示）
- [ ] 知道遇到环境问题去哪里搜索（推荐关键词 + Stack Overflow/掘金）

**不要求**：理解 package manager、构建工具、版本管理、PATH 原理等。这些在后续学习中按需引入。
