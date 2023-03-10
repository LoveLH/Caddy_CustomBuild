# Redpill_CustomBuild
[![](https://img.shields.io/github/issues-search?label=%E5%AE%9A%E5%88%B6%E6%AC%A1%E6%95%B0&query=repo%3ALoveLH%2FCaddy_CustomBuild%20label%3Acustom)](https://github.com/LoveLH/Caddy_CustomBuild/issues?q=label%3Acustom)
[![](https://img.shields.io/github/issues-search?label=%E6%AF%8F%E6%97%A5%E6%9E%84%E5%BB%BA&query=repo%3ALoveLH%2FCaddy_CustomBuild%20label%3schedule)](https://github.com/LoveLH/Caddy_CustomBuild/issues?q=label%3Aschedule)  

## 介绍  
[Caddy_CustomBuild](https://github.com/LoveLH/Caddy_CustomBuild)  
一个自定义配置通过 Github Action 编译 Caddy 的平台. 

主要是通过环境变量设置并使用xcaddy来进行交叉编译的，所以主要参数都是go交叉编译用的环境变量。

> 😎 为什么用 GitHub Action？  
> 托管于 GitHub 服务器, 只要 GitHub 不宕机, 它就不受影响(Private 项目每月有 2000 次的限制, Public 项目无限制).

## 使用  
在本项目 Issues 中创建问题(符合下述规范), 按需填写即可发起定制构建.

### Issue title:
标题请以 custom 开头(不区分大小写), 且不要包含'(单引号),"(双引号) 等转义字符.
### Issue body:
内容 以json格式编写(切记符号为英文符号, [【👉JSON检测】](https://json-online.com/check/)
[【👉Go编译时的环境变量】](https://go.dev/doc/install/source#environment))


参数             | 必选 |     默认值     | 说明  
-----------------|------|----------------|---------  
GOOS             | X    |linux           | 系统，请参照表上提到的环境变量。  
GOARCH           | X    |amd64           | 指令集，请参照表上提到的环境变量。  
version          | X    |latest          | 如果不指定，则脚本会自动获取caddy最终版本。
GOARM            | ×    |-               | GOARCH为arm时，指定arm架构版本.  
addons           | ×    |-               | 请输入需要集成的插件, 多个请以','间隔. 


## 说明
1. 构建成功 Issues 会自动 closed.  
2. 构建失败 后请调整参数重新创建Issues发起重新构建, 或者修改body后 Close Issue + Reopen 重新触发.（触发编译：open, reopen）. 
3. 再次构建, 直接 reopen 会再次触发构建. 
4. 每日构建, 打上'schedule'标签 将会每日构建(通过Reopen的方式, 因此如果构建失败Issues没有Closed 将终止).     
5. 根据github官方说明所有的编译结果保留90天，周知.
6. 如果没有魔法, 参考 https://github.com/wjz304/hosts 设置 hosts.
7. 在Issues下评论 "transfer" 附件转快传 🚲->🏍. (请勿重复发, 转换操作时间 ≈ 该Issue编译成功次数 X 3分钟).
8. 在Issues下评论 "delete builds" 即可删该Issues的所有历史编译记录.

## 举例
* 示例: 
  - {"GOOS":"linux","GOARCH":"arm","GOARM":"6","addons":"github.com/imgk/caddy-trojan"}  

## 鸣谢
https://github.com/wjz304/Redpill_CustomBuild
