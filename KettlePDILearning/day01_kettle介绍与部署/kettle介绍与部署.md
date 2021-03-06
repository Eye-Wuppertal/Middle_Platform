# 可视化ETL工具Kettle

## 一、数据仓库与ETL（Extract-Transform-Load）

### 1、数据仓库

- 本质：专门针对于数据存储模型
- 实现：MySQL、Oracle、Hive……
- 应用：专门用于实现将各种各样数据进行统一化规范化的数据存储，为所有数据应用提供数据
  - 数据分析
  - 数据挖掘
  - 用户画像
  - 推荐系统
  - 风控系统
- 特点
  - 本身不产生数据
  - 本身也不使用数据
  - 用于实现复杂数据的存储
- 与数据库区别
  - 数据库：一般用于支撑业务数据的存储
    - 网站后台：用户数据、商品数据、订单数据
  - 数据仓库：专门为数据处理提供数据的
    - 业务数据
    - 用户行为
    - 爬虫数据
    - 第三方数据
    - 日志数据
- 问题
  - 数据种类非常的多，每一种数据的内容或者格式都不一样
    - 有结构化、有非结构化
    - 有合法的，有非法的
    - 有需要的，有不需要的
  - MySQL是一个专门用于存储结构化数据的数据存储工具
    - 结构化
    - 需要
    - 合法
  - 如何将各种各样的数据存储在MYSQL中？
- 解决
  - 数据产生以后，不能直接放入数据仓库【MySQL】中存储
  - 对原始数据进行一步预处理，将需要的、合法的数据放入数据仓库中
  - 这一步预处理：ETL【数据清洗】

### 2、ETL（Extract-Transform-Load）

- 功能：实现数据的预处理，数据清洗过程，将原始数据经过ETL处理变成想要的数据，进行下一步的应用
- 实现
  - 抽取：读取需要处理的原始数据
  - 转换：将原始数据转换为目标数据
    - 过滤：将不需要的数据过滤掉
      - 原始数据中有100列
      - 实际需要30列
      - 过滤掉70列
    - 补全：将需要用到的数据补全
      - 每一个访问网站或者APP时，会有一个IP地址
      - 后台通过IP能获取到我们当前所在的国家、省份、城市
    - 转换：原始数据的格式不是我们想要的格式，转换为想要的格式
      - 原始数据：22/Aug/2020:12:20:35
      - |
      - |  转换
      - |
      - 目标格式：2020-08-22  12:20:35
  - 加载：将处理好的目标数据放入数据仓库中

### 3、Kettle

- 功能：实现可视化ETL
  - 可视化：不用写复杂的代码程序，可以通过图形化的界面来实现数据的处理
- 特点
  - 学习以及使用的成本比较低
  - 功能非常强大



## 二、Windows版本部署

### 1、JDK安装配置

- 安装JDK 略

  


### 2、Kettle安装启动

- 解压安装

  - 解压到一个不包含中文的路径中即可

  ![image-20200722110833924](img/image-20200722110833924-16468850427391.png)

  ![image-20200722113554732](img/image-20200722113554732-16468850445382.png)

  

- 启动

  ![image-20200722113631022](img/image-20200722113631022-16468850467933.png)

  ![image-20200722113730624](img/image-20200722113730624-16468850480304.png)

  





























