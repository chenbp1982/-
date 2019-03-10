# 项目部署
> 项目使用gradle构建，请先安装gradle。数据库会在启动项目时自动创建，用户数据可自行添加，其中密码要对明文进行sha1摘要。为了方便，在仓库sql目录下提供了默认的初始化脚本，可自行使用
- 从git导入项目
- 在IDE配置java运行环境
- 运行WarehouseApplication.java
- 访问:http://127.0.0.1:8880/user-login

# 用户手册



## 管理员

## 客服人员

## 仓库人员


# 2018/06/20需求更改
## 库存管理：
### 增加：
- 报税商改为入库编号：规则2018RXXXXX号
- 仓位
- 库别
- 添加供货商

### 批量操作
- 箱号去掉
- 时间段查询
- 入库：DateCode,Lotno可以不显示
- 一个出入库编号对应多个料号

### 入库加客户名称


## 供提关系
- [ ] 手动输入编号


# 2018/06/21需求更改
## 入库
- 增加“生产日期”
## 出库
- 增加“生产日期”
- 出库增加“入库编号” 
- 增加“出库料号”，出库料号

## 库存
- 增加库存物品状态：
  - 刚入库时为“未校验”，后面会根据校验结果将状态改为“良品”，“不良品“
- 增加生产日期

# 2018/06/25需求更改
## 库存
- 修改状态修改：增加良品和不良品的数量
- 出库时分情况：
  - 当提货商和供货商相同时：退回不良品
  - 当提货上和供货商不同时：良品正常出库
  
  
# 2018/06/25需求更改
## 库存
- 修改状态修改：修改状态后，拆分成两条记录。良品和不良品各一条记录

# 2018/06/28需求更改
## 库存
- 报表生成

# 2018/07/02需求更改
## 出库
  - 增加”订单号（PO）“
  
# 2018/08/06
- 增加日志模块
  - 系统运行日志
  - 用户操作日志
  
# 2016/08/07
- 自定义业务异常
- 对于自定义的业务异常，使用专门的异常处理类来记录，返回友好的页面

# 2016/08/26
- 增加权限控制
  - 管理员：所有页面
  - 客服
    - 首页
    - 入库申请
    - 入库历史
    - 出库申请
    - 出库历史
  - 仓库
    - 首页
    - 入库审核
    - 出库审核
    - 库存
# 20180909 BUGFIX
  - 困扰已久的阿里云发送邮件问题解决了，是由于阿里云默认封禁了25端口导致的，解决如下
  ```
   #邮箱配置
    mail:
      host: smtp.exmail.qq.com
      username: 邮箱名
      password: 邮箱登录密码
      properties:
        mail:
          smtp:
            auth: true
            timeout: 25000
            ssl.enable: true
            socketFactory.class: javax.net.ssl.SSLSocketFactory
            starttls.enable: true
            socketFactory.port: 465　
            port: 465
      default-encoding: UTF-8
  ```