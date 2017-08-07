招行法律知识库与智能交互研发
===================================
项目描述
-----------------------------------
   - **介绍**:本项目用于奇点创智数据科技有限公司操作neo4j数据库，elasticSearch以及与前端交互的服务器app。
   - **用途**：对3.2.0版本的neo4j数据库进行增删改查外加索引的操作
   - **特性**：
   	1.neo4j自带的服务端对中文建立的内置索引分词粒度以字为单位，不太符合实际需求，而且cypher语法没有对分词器的选择操作语句,修改采用elastic做中间业务处理索引内容对接图数据。
    2.本代码选用hanlp分词器做索引分词底层，可扩展词典修改分词粒度。

编译、运行环境说明：
-----------------------------------
    使用JDK1.8.0版本，具体依赖都在pom中，本地nexus没有所需依赖。

总体目录
-----------------------------------
+ main
    + java
        + com
            + qdcz
                * chat
                * common
                * graph
                * index
                * mongo
            + APP
    + resources
+ test

-------------------
**chat**包含智能问答接口与逻辑处理<br>
**common**中包含一些公用静态方法<br>
**graph**neo4j图操作及接口<br>
**index**为elasticSearch建立索引的接口与方法<br>
**sdn**为图边节点的实例化(entity)以及对应所需要的知识库cypher(epository)。<br>
**service**为结合实际所需的服务逻辑编写,分为低中高三层，上层依赖下层。<br>
**Tools**为定义的工具类。<br>
**APP为**  `SpringbootSdnEmbeddedApplication`，启动服务主入口。<br>
**resources**为配置文件<br>
	其中`IKAnalyzer.cfg.xml`为IK分词的扩展配置，加载了2个扩展词典`sougou`、 `stopword`、`银团指引词典`<br>
	`neo4j.properties`设置了app启动的驱动，访问的数据库的位置，对外端口<br>
	`mongo.properties`设置了mongo-driver所需的信息<br>
	`hanlp.properties`设置了han分词器加载词典位置<br>
**test**下为各类单元测试时使用的测试。<br>



