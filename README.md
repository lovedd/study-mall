# study-mall

##1. 简介
这是一个学习性质的项目，旨在贯穿前后端知识点，基于慕课网的一个视频，但是最后我们将做出来的并不限于该视屏所给的简单demo，而是一个功能丰富的购物网站。

###1.1 网站准备实现如下功能：
1. 注册/录录模块。
2. 商品展示页面，数据从网上进行爬取，支持分页和关键字搜索。
3. 订单模块，可以点击加入购物车并支持付款购买。

###1.2 技术栈：
构建工具：webpack
前端：vue + vuex + vuerouter + axios
后端：node + mongodb + mongoose + express

###1.3 拟贯穿的知识点：
1. webpack的使用，开发环境，测试环境和生产环境的配置搭建
2. vue单页应用的构建，熟练使用vue + vuex + vuerouter + axios
3. 掌握网络知识，熟悉前后端的通信以及缓存机制
4. 掌握后端开发知识，学会使用node + mongodb + mongoose + express搭建服务器
5. 掌握线上部署知识

### 1.4 环境简介
1. 使用mac进行开发（windows请参考package.json自行加载依赖）
2. 前端代码在https://github.com/lovedd/study-mall.git，后端代码在https://github.com/lovedd/study-mall-server.git。
注：这两个仓库在开发中，如果大家等不及，可以看完整版https://github.com/lovedd/whole-mall.git，该仓库前后端未做分离。
注：该项目不依赖后端，前端已做mock服务，如果不想学习后端，只需要clone前端代码即可
3. 需要下载node，monodb，其余依赖可以使用npm
4. 建议大家下载一款mongodb的可视化管理工具，方便导入数据，本人目前使用adminMongo

## 2. 操作步骤

step1：clone前后端仓库代码，准备环境配置

step2：下载依赖
```
npm install
```

step3：打开数据库
```
mongod

```
step4：运行代码(开发环境)
```
npm start
或者
npm run dev

```

step5：浏览器输入地址
```
http://localhost:8080/#/
```


代码在逐步完善中。。。
