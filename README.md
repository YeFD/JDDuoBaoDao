# 京东夺宝岛自动加价抢购程序

## 2022-02-22更新
* 优化登录策略，启动浏览器后只需登录一次
* 增加“自动加价/出最高价”选项
* 优化刷新频率

##  2021-08-29更新
出价策略改为在最后时刻，以最高价出价

## 2021-06-27更新

由于京东更新了出价的接口调用频率，2秒只能调用一次接口，该工具无法依靠暴力请求来达到出价的目的了。只能在最后时刻进行出价。

##  注意：由于京东出价的接口保护，目前该工具成功率较低，请谨慎使用

##  目前只能对单个商品进行抢购

##  使用方法
1. ```clone```整个下项目
2. 安装```nodejs```，
3. 进入项目目录，执行```npm install```，安装依赖环境
4. 修改```server/index.js```中的```OfferPriceDelay```，调整最后出价的时间，单位毫秒，默认100
5. ```npm start```运行软件
6. ```npm run dist```生成对应安装包

##  基本原理

使用puppeteer加载拍卖页面，先模拟一次正常操作的出价，获取出价请求中需要的各个参数，

然后轮询当前出价价格和剩余出价时间，在距离出价截止时间```OfferPriceDelay```毫秒时，开始请求出价接口。

##  注意事项
*   本程序仅供本人研究学习使用
*   需要安装chrome浏览器
*   如果网络环境不好，可以把```OfferPriceDelay```值设置高一点
*   在登录成功后跳转，有几率需要进行手动点击验证