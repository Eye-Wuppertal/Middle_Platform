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

  ![image-20200722110833924](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722110833924.png)

  ![image-20200722113554732](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722113554732.png)

  

- 启动

  ![image-20200722113631022](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722113631022.png)

  ![image-20200722113730624](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722113730624.png)

  





























## 三、Kettle使用

### 1、转换

- 功能：实现一个转换的程序
  - 输入：要读取什么数据进行转换
  - 转换：要对数据怎么进行处理【过滤、补全、转换】
  - 输出：要将处理好的数据保存到什么地方

![image-20200722114144063](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722114144063.png)



### 2、作业

- 功能：将多个转换根据需求构建任务流

  - 任务流：很多个任务【每一个转换程序】根据自动运行的条件来运行就是任务流
  - 实际工作中，一次要执行很多个转换任务，如何实现这些任务的自动化执行
  - 自动运行
    - 第一种：定时运行
      - 每天的00:01分开始自动运行
    - 第二种：依赖关系
      - A先运行，A运行成功，B就自动运行

- 举例

  - 转换1：实现对数据的过滤

  - 转换2：实现对数据的补全

  - 转换3：实现对数据的转换

  - 作业：一个任务流

    - 转换1：每天00:10分自动运行
    - 转换2：转换1运行成功，转换2就开始运行
    - 转换3：转换2运行成功，转换3就开始运行

    ![image-20200722114924436](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722114924436.png)

    





## 四、实战案例一

### 1、需求

- 将txt文件中的数据写入Excel表格中

### 2、分析

- 任务：一个转换程序
  - 输入：读取txt文件中内容
  - 转换：不需要
  - 输出：将内容加载到一个Excel文件中

### 3、实现

- step1：构建转换流程图

  - 新建一个转换任务

    ![image-20200722142250319](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722142250319.png)

    ![image-20200722142310820](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722142310820.png)

  - 将输入和输出拖入流程图的面板中

    ![image-20200722142458479](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722142458479.png)

    ![image-20200722142542150](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722142542150.png)

  - 连线

    ![image-20200722142722676](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722142722676.png)

    

- step2：配置输入

  - 关联文件

  ![image-20200722143501694](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722143501694.png)

  ![image-20200722143632745](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722143632745.png)

  ![image-20200722143734940](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722143734940.png)

  - 配置文件的格式

    ![image-20200722144128741](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722144128741.png)

    

  - 选择输出到下一步的数据

    ![image-20200722144224932](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722144224932.png)

    ![image-20200722144239822](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722144239822.png)

    ![image-20200722144446344](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722144446344.png)

    ![image-20200722144456628](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722144456628.png)

    ![image-20200722144531292](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722144531292.png)

    ![image-20200722144543660](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722144543660.png)

    

- step3：配置输出

  - 输出目标文件

    ![image-20200722144706570](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722144706570.png)

    ![image-20200722144814951](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722144814951.png)

    ![image-20200722144918502](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722144918502.png)

    

  - 预览输出信息

    ![image-20200722145005181](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722145005181.png)

    ![image-20200722145020311](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722145020311.png)

    

- step4：测试运行

  ![image-20200722145128899](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722145128899.png)

  ![image-20200722145136836](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722145136836.png)

  ![image-20200722145204498](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722145204498.png)

  ![image-20200722145234929](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722145234929.png)

  ![image-20200722145300553](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722145300553.png)

  ![image-20200722145342524](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722145342524.png)

  ![image-20200722145349915](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722145349915.png)

  





## 五、实战案例二

### 1、需求

- 读取Excel文件中的数据，存储MySQL中

### 2、分析

- 这是一个转换程序

- 输入：读取这个Excel文件

- 转换：不需要实现转换

- 输出：存储到MySQL中的表中

  - 数据库：kettle_demo

    ```
    create database kettle_demo;
    ```

    ![image-20200722155531955](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722155531955.png)

    

  - 表：t_user

    - 让Kettle根据上游的数据自行创建

### 3、实现

- step1：构建转换流程图

  - 新建保存

    ![image-20200722153632700](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722153632700.png)

  - 定义输入

    ![image-20200722153825528](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722153825528.png)

  - 定义输出

    ![image-20200722153849321](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722153849321.png)

    

- step2：配置输入

  - 定义输入的数据

    ![image-20200722154052274](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722154052274.png)

    ![image-20200722154130148](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722154130148.png)

    ![image-20200722154146185](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722154146185.png)

    ![image-20200722154157423](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722154157423.png)

    ![image-20200722154236283](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722154236283.png)

    ![image-20200722154317003](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722154317003.png)

    ![image-20200722154343906](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722154343906.png)、

  - 定义输出的字段

    ![image-20200722154439414](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722154439414.png)

    ![image-20200722154624225](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722154624225.png)

    ![image-20200722154639730](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722154639730.png)

    ![image-20200722154716523](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722154716523.png)

    ![image-20200722154730317](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722154730317.png)

    

- step3：配置输出

  - 将连接MySQL的工具放入Kettle的lib目录中

    ![image-20200722160018987](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722160018987.png)

    ![image-20200722160104092](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722160104092.png)

    

  - ==**重新启动Kettle**==

  - 构建MySQL连接：地址、用户名、密码、数据库

    ![image-20200722155803639](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722155803639.png)

    ![image-20200722160250214](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722160250214.png)

    ![image-20200722160310389](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722160310389.png)

    ![image-20200722160508104](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722160508104.png)

    ![image-20200722160529093](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722160529093.png)

    ![image-20200722160549087](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722160549087.png)

    ![image-20200722160559340](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722160559340.png)

    ![image-20200722160642263](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722160642263.png)

    ![image-20200722160657900](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722160657900.png)

    

- step4：测试运行

  ![image-20200722160730805](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722160730805.png)

  ![image-20200722160739216](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722160739216.png)

  ![image-20200722160759504](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722160759504.png)

  ![image-20200722160844136](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722160844136.png)

  



## 六、常用组件

### 1、共享数据库连接

- 新建的数据库连接都只属于某一个转换程序
- 如果你想让所有的转换程序都能使用这个连接，需要开启共享

![image-20200722165840910](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722165840910.png)

![image-20200722165859797](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722165859797.png)

![image-20200722165919365](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722165919365.png)



### 2、表输入组件

- 需求：将t_user中的数据，同步到t_user1这张表中

- 分析

  - 这是一个转换任务
  - 输入：读取t_user表的数据
  - 转换：没有转换过程
  - 输出：将结果写入t_user1表中

- 实现

  - 开发程序

    ![image-20200722164702600](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722164702600.png)

    

  - 配置输入

    - 先配置数据库连接共享

    ![image-20200722165958428](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722165958428.png)

    ![image-20200722170047492](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722170047492.png)

    ![image-20200722170105618](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722170105618.png)

    ![image-20200722170215354](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722170215354.png)

    ![image-20200722170330357](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722170330357.png)

    

  - 配置输出

    ![image-20200722170419413](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722170419413.png)

    ![image-20200722170438223](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722170438223.png)

    ![image-20200722170452804](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722170452804.png)

    

  - 测试运行

    ![image-20200722170536458](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722170536458.png)

    ![image-20200722170549399](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722170549399.png)

    ![image-20200722170622208](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722170622208.png)

    ![image-20200722170632510](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722170632510.png)

    

### 3、插入更新组件

- 工作需求：将 A表的数据同步到B表中，保证B表的数据与A表的数据一致，实现是不断更新的操作

  - A表发生了更新，更新的数据也会同步到B表中
  - A表没有发生更新，即使程序运行，B表也不发生改变
  - 数据同步的过程
    - 每次只同步更新的数据
    - 已经同步过的数据，就不会再进行同步
  - 工作中一般一天会同步一次，程序就每天执行一次

- 解决：插入更新的输出组件

- 功能：只会同步发生更新的数据，已经同步过的数据不会再次同步

  - 数据更新
    - 插入一条新的数据
    - 更改一条老的数据

- 实现：将t_user表的数据同步到t_user2中【任何的时刻，这两张表 数据同步时是一致的】

  - 开发转化 任务流程图

    ![image-20200722172727176](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722172727176.png)

    

  - 定义输入

    ![image-20200722172804528](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722172804528.png)

    ![image-20200722172825165](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722172825165.png)

    

  - 定义输出

    ![image-20200722173646566](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722173646566.png)

    ![image-20200722173715767](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722173715767.png)

    ![image-20200722173750781](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722173750781.png)

    ![image-20200722173859869](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722173859869.png)

    ![image-20200722173918025](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722173918025.png)

    ![image-20200722173939760](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722173939760.png)

    

  - 测试运行

    ![image-20200722173956739](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722173956739.png)

    ![image-20200722174010199](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722174010199.png)

    ![image-20200722174019228](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722174019228.png)

    ![image-20200722174035354](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722174035354.png)

  - 如果修改了t_user的数据，重新执行程序，观察t_user2中的数据是否与t_user是一致的

    - 修改t_user的数据

      ![image-20200722174237259](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722174237259.png)

      ![image-20200722174257213](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722174257213.png)

    - 重新运行程序

      ![image-20200722174325258](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722174325258.png)

    - 观察t_user2的数据

      ![image-20200722174412978](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722174412978.png)

  - 同步业务

    - 全量：每次将所有的数据都同步一份
      - 保证A和B是一致的
        - 每次先删除B所有内容，然后，再同步
      - 程序的性能比较差，数据量大了以后，非常慢，不建议使用
      - 表输出：全量的组件
    - 增量：每次将发生更新的数据同步，没有发生更新就是已经同步过的数据不再同步
      - 保证A和B是一致的
      - 工作中都使用增量的方式
      - 插入更新：增量的组件



## 七、Kettle Job

### 1、Job的功能

- 转换：实现一种数据的转换处理，是一个转换任务
- 作业：实现多个转换任务按照一定的规则运行，就是一个任务流
  - 时间规则：从00:10分开始，每5种运行一次
  - 依赖规则：A成功了，就执行B
- 功能：将多个转换根据彼此之间的 关系实现任务流运行

### 2、Job的开发

- 需求：每5s就运行一个Kettle的转换任务

- 实现

  - 构建一个作业

    ![image-20200722184809959](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722184809959.png)

    

  - 配置转换任务

    ![image-20200722185018655](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722185018655.png)

    ![image-20200722184844483](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722184844483.png)

    ![image-20200722184904596](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722184904596.png)

    ![image-20200722184929577](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722184929577.png)

    

  - 配置作业运行的规则

    ![image-20200722185004590](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722185004590.png)

    ![image-20200722185211573](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722185211573.png)

    

  - 运行

    ![image-20200722185247683](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722185247683.png)

    ![image-20200722185310911](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722185310911.png)



![image-20200722185421352](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722185421352.png)

![image-20200722185439558](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722185439558.png)



- 扩展：多个转换任务，按照时间以及顺序运行

  ![image-20200722185634596](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722185634596.png)

  ![image-20200722185754113](F:\Middle_PlatformLearningFiles\资料-3天从零快速搭建BI商业大数据分析平台\Day02：可视化ETL工具Kettle资料\随堂笔记\Day02：可视化ETL工具Kettle.assets\image-20200722185754113.png)

  















