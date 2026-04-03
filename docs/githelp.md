# 文档维护教程

## 前言

欢迎来到UAVTrains项目！本教程将帮助你从零开始学习如何为GitHub上的docsify项目贡献内容。无论你是编程新手还是GitHub初学者，本教程都会一步步指导你完成整个流程。

## 目录

1. [准备工作](#准备工作)
2. [GitHub基础概念](#github基础概念)
3. [Fork项目](#fork项目)
4. [克隆项目到本地](#克隆项目到本地)
5. [编辑文档内容](#编辑文档内容)
6. [提交前的准备](#提交前的准备)
7. [提交更改](#提交更改)
8. [创建Pull Request](#创建pull-request)
9. [实例演示](#实例演示)
10. [常见问题](#常见问题)

## 准备工作

### 1. 注册GitHub账号

如果你还没有GitHub账号，请先访问 [GitHub官网](https://github.com) 注册一个账号。

### 2. 安装Git

Git是版本控制工具，我们需要用它来管理代码。

**Windows用户：**
- 下载并安装 [Git for Windows](https://gitforwindows.org/)
- 安装时保持默认设置即可

**Mac用户：**
- 打开终端，输入：`xcode-select --install`
- 或者下载 [Git for Mac](https://git-scm.com/download/mac)

**Linux用户：**
- Ubuntu/Debian: `sudo apt-get install git`
- CentOS/Fedora: `sudo yum install git`

### 3. 配置Git

安装完成后，打开终端（Windows用户打开Git Bash），配置你的用户名和邮箱：

```bash
git config --global user.name "你的GitHub用户名"
git config --global user.email "你的GitHub邮箱"
```

## GitHub基础概念

在开始之前，了解一些基本概念：

- **Repository（仓库）**：项目的存储空间，包含所有文件和历史记录
- **Fork（分叉）**：将别人的仓库复制到自己的GitHub账号下
- **Clone（克隆）**：将远程仓库下载到本地电脑
- **Branch（分支）**：项目的不同版本，用于独立开发
- **Commit（提交）**：保存更改到本地仓库
- **Pull Request（拉取请求）**：请求将你的更改合并到原项目中

## Fork项目

### 步骤1：访问项目页面

打开浏览器，访问项目地址：https://github.com/Hahngao/UAVTrains

### 步骤2：Fork项目

1. 点击页面右上角的 **Fork** 按钮
2. 选择你的GitHub账号作为目标位置
3. 等待Fork完成


Fork完成后，你会在自己的GitHub账号下看到一个完全相同的仓库副本。

## 克隆项目到本地

### 步骤1：获取仓库地址

1. 进入你Fork后的仓库页面
2. 点击绿色的 **Code** 按钮
3. 复制HTTPS链接

### 步骤2：克隆到本地

打开终端（或Git Bash），执行以下命令：

```bash
# 切换到你想存放项目的目录
cd Desktop

# 克隆项目
git clone https://github.com/你的用户名/UAVTrains.git

# 进入项目目录
cd UAVTrains
```


## 编辑文档内容

### 了解docsify项目结构

docsify项目通常包含以下重要文件：

```
UAVTrains/
├── README.md
├── update_docs.py
└── docs/
    ├── README.md
    ├── index.html
    ├── _sidebar.md
    ├── ...
    └── 入门实验步骤/
        ├── readme.md
        └── 实验xxx/
            └── step1.md
            ├── pics.jpg
            └── ...
        └── ...
```

### 编辑Markdown文件

docsify使用Markdown格式编写文档。以下是一些基本语法：

```markdown
# 一级标题
## 二级标题
### 三级标题

**粗体文本**
*斜体文本*

- 列表项1
- 列表项2

1. 有序列表1
2. 有序列表2

[链接文本](链接地址)
![图片描述](图片地址)

```代码块```
```

### 使用文本编辑器

推荐使用以下编辑器：
- **VS Code**（免费，功能强大）
- **Sublime Text**（轻量级）
- **Notepad++**（Windows用户）

### 使用文件夹保存文本项目文档

当一个文档需要配套保存图片、表格附件或其他素材时，建议不要只创建单独的 `.md` 文件，而是为该文档建立一个同名文件夹，统一管理内容。

#### 推荐目录结构
```text
docs/入门实验步骤/实验xxx/step1.md
docs/入门实验步骤/实验xxx/pics.jpg
...
```

#### 操作步骤

1. 在 `docs/` 目录下的 `入门实验步骤/` 文件夹中新建一个文件夹，文件夹名称建议与章节名称一致，例如 `实验01-无人机安全操作指南`。
2. 在该文件夹中创建 `实验01-无人机安全操作指南.md`，作为这个章节的首页内容。
3. 将本章节需要使用的图片、附件等素材也放在这个文件夹内；如果图片较多，可以再建立 `images/` 或 `素材/` 子文件夹分类保存。
4. 在 `实验01-无人机安全操作指南.md` 中使用相对路径引用图片，例如：

```markdown
![飞行前检查](./飞行前检查.png)
![示例图片](./素材/示例图片.jpg)
```

5. 如果这是一个新章节，需要同步更新侧边栏导航。可以手动修改 `_sidebar.md`，也可以运行 `python update_docs.py` 自动更新。下一小结将详细介绍方法。


## 提交前的准备（重点！必须执行，检查更改是否生效！）
### 步骤1：更新侧边栏导航（新增md文件需要）

方法一：在 `_sidebar.md` 文件中，添加新的章节到导航结构。例如：

```markdown
- [**比赛介绍**](intro.md)
- [**系统组成**](systemoverview.md)
- [**硬件选项**](hardware_options.md)
- [**快速启动**](quickstart.md)
- [**文档维护教程**](githelp.md)
- [**进度记录**](progress.md)
- [**入门实验步骤**](入门实验步骤/readme.md)
  - [实验01-无人机安全操作指南](入门实验步骤/实验xxx/step1.md)
- [**开发教程**](开发教程/readme.md)
```
方法二：自动更新侧边栏导航。在工程目录UAVtrans下运行 update_docs.py 程序。

```bash
# 运行update_docs.py命令
python update_docs.py
```

### 步骤2：在 `docs/` 目录下运行docsify serve 命令，点开网页，检查更改是否生效。必须认真核对。

```bash
# 运行docsify serve命令
docsify serve
```
#### 备注：如果没有安装docsify，需要先安装，详见 [本地使用docsify](#本地使用docsify)


## 提交更改

### 步骤1：查看更改状态

```bash
# 查看哪些文件被修改
git status
```

### 步骤2：添加更改到暂存区

```bash
# 添加所有更改
git add .

# 或者添加特定文件
git add README.md
```

### 步骤3：提交更改

```bash
# 提交更改并添加描述
git commit -m "描述你的更改内容"

# 提交信息示例：
# git commit -m "添加无人机基础操作章节"
# git commit -m "修复README中的拼写错误"
# git commit -m "更新侧边栏导航"
```


### 步骤4：推送到远程仓库-主分支

```bash
# 推送到你的GitHub仓库
git push origin main
```

## 创建 Pull Request

### 步骤1：访问 GitHub 页面

推送完成后，访问你的 GitHub 仓库页面，通常页面顶部会出现“Create pull request”或“Compare & pull request”等提示按钮。

### 步骤2：创建 Pull Request

1. 点击 **Create pull request**（可能显示为 **Compare & pull request**、**Open pull request** 或 **New pull request**，取决于你所在分支和仓库设置）
2. 选择目标分支（通常为 `main` 或 `master`）和你当前工作分支
3. 填写清晰的 Pull Request 标题和详细描述
4. 可以添加 reviewers、labels、projects、milestones 等（可选）
5. 点击 **Create pull request**

### 步骤3：等待审核

项目维护者会审核你的更改，可能会提出修改建议。根据反馈进行修改后，再次推送到同一个分支，PR 会自动更新。
项目维护者会审核你的更改，可能会提出修改建议。根据反馈进行修改后，再次提交即可。



## 实例演示

### 示例：添加新的章节

假设我们要为项目添加一个新的章节"无人机安全操作指南"。


#### 步骤1：创建新文档文件

在 `docs/` 目录下创建新文件 `safety-guide.md`：

```markdown
# 无人机安全操作指南

## 飞行前检查

1. 检查电池电量
2. 确认天气条件
3. 检查飞行区域是否允许飞行

## 飞行中注意事项

- 保持视线范围内飞行
- 避免在人群上空飞行
- 注意障碍物和电线

## 紧急情况处理

如果遇到紧急情况：
1. 立即启动返航功能
2. 寻找安全降落点
3. 关闭电机电源
```


#### 步骤2：提交更改至主分支

```bash
git add docs/safety-guide.md _sidebar.md
git commit -m "添加无人机安全操作指南章节"
git push origin main
```

#### 步骤3：创建Pull Request

在GitHub上创建Pull Request，等待项目维护者审核。

## 常见问题

### Q: 如何解决合并冲突？

A: 当多人修改同一文件时可能出现冲突。解决方法：
1. 拉取最新代码：`git pull origin main`
2. 手动解决冲突（编辑文件，保留需要的更改）
3. 重新提交：`git add .` 和 `git commit -m "解决冲突"`

### Q: 如何更新本地仓库？

A: 定期同步原项目的更新：

```bash
# 添加上游仓库
git remote add upstream https://github.com/Hahngao/UAVTrains.git

# 拉取上游更新
git fetch upstream

# 合并到本地分支
git merge upstream/main
```

### Q: 提交信息应该怎么写？

A: 提交信息应该清晰简洁，遵循以下格式：
- 类型：添加、修复、更新、删除等
- 范围：涉及的文件或功能
- 描述：具体做了什么

示例：
- "添加：无人机安全操作指南章节"
- "修复：README中的语法错误"
- "更新：侧边栏导航结构"

### Q: 如何撤销错误的提交？

A: 使用以下命令：

```bash
# 撤销最后一次提交，保留更改
git reset --soft HEAD~1

# 撤销最后一次提交，丢弃更改
git reset --hard HEAD~1
```

## 最佳实践

1. **频繁提交**：小步快跑，每次提交只完成一个小功能
2. **描述清晰**：提交信息要能清楚说明更改内容
3. **保持同步**：定期拉取原项目的更新
4. **测试更改**：在本地预览docsify网站效果
5. **遵守规范**：遵循项目的代码规范和文档格式

## 本地使用docsify

如果你想在本地预览修改后的效果：

1. 安装docsify-cli：
```bash
npm i docsify-cli -g
```

2. 在项目根目录启动服务：
```bash
docsify serve .
```

3. 打开浏览器访问：http://localhost:3000
