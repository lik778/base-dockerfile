### 基础镜像
#### 一、web 应用基础镜像
**使用现有的？**
##### 要求？
+ 1、node版本要求18.15.0
+ 2、通过pnpm run build构建
**使用:**
`docker pull copymanager/base-node-app`
**适合哪些项目？**
+ node 项目
**对项目的package.json的scripts要求？**
```sh
  "build": "构建项目指令",
```