本仓库面向不了解前端的技术人员，如何更改社区部署版的dify，以完成自己的需求
你可以达成的事项包括但不限于：
- 增加可供调用的工具数
- 增加agent迭代轮次
- 调整内置prompt等

已完成事项
[x] 增加可供调用的工具数（1000000）
[x] 增加阅读文章长度（1500）
等等


# 本机快速启动

```
cd web && docker build . -t dify-web
cd ..
cd docker
docker compose up -d
```
请注意，前端docker build之前可用内存需要大于等于4GB

如果前后端分离，需要更改 `web/.env.local`文件中的
- NEXT_PUBLIC_API_PREFIX
- NEXT_PUBLIC_PUBLIC_API_PREFIX
按需将`localhost:5001`改为后端所在ip地址或域名

# 本地开发调试
## 开发前环境安装
### nvm  
<img width="717" alt="image" src="https://github.com/ValeriaWong/dify/assets/63283616/461ce60c-0339-4317-b0e6-655b5fa89776">

安装成功后使用nvm安装v18.17.0或者v21.0.0版本的node.js

### yarn  
```
npm install yarn
```

## 后端启动
请参照官方文档[本地源码启动](https://docs.dify.ai/v/zh-hans/getting-started/install-self-hosted/local-source-code) 

⚠️flask需要这样运行`python flask db upgrade`

## 前端启动
```
yarn
yarn build
yarn start
```
## 主要更改文件

`web/config/index.ts`


# 此前的尝试及失败经验：

更改`docker-compose.yaml`将web注释,nginx的依赖中web注释掉，docker启动后端

然后再启动前端

发现nginx会不断重启，前端页面停留在`localhost:3000/apps`的等待页面



