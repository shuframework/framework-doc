## es的用途





## es的基本概念

### index 索引

一个索引就是含有某些相似特性的文档的集合。例如，你可以有一个用户数据的索引，一个产品目录的索引。

命名 必须都是小写字母，还可以用 _ （类似数据库的表名）



### type 类型 【7.x已被移除，6.x中过时不推荐使用】

一个类型是你的索引中的一个分类或者说是一个分区，它可以让你在同一索引中存储不同类型的文档，例如，为用户建一个类型，为博客文章建另一个类型。现在已不可能在同一个索引中创建多个类型，并且整个类型的概念将会在未 来的版本中移除。

### document 文档

描述 index的文档结构，每个属性（字段）都有对应的类型，可以理解为类里面的属性，有数据类型，名称等



### 分片

它可以将你的索引细分成多个部分。当你创建一个索引的时候，你可以简单的定义你想要的分片的数量。每个分片本身是一个全功能的完全独立的“索引”，它可以部署在集群中的任何节点上。



## REST API 操作

检查集群，节点和索引的健康状况，状态和统计数据 

管理集群，节点和索引的数据和原数据 

执行CRUD(增删改查)操作，依靠索引进行搜索 

执行高级搜索操作，比如分页，排序，过滤，脚本化，聚集等等 



### kibana执行CRUD(增删改查)操作

#### 集群健康监控

GET  /_cat/health?v

#### 新增index



#### 查询index



#### 查询index下的数据

**语法**  GET /index值/type值/_search

	GET shq_game_configs/item/_search
	{
	  "query": {
	    "match": {
	      "gameNo": "13wh8vn2jsi8f"
	    }
	  }
	}



#### 修改index下的数据



#### 删除index

**语法**  DELETE  index值

	DELETE test_index



#### 清空index下的记录

**语法**  POST  index值/item/_delete_by_query

	POST shq_errorcode/item/_delete_by_query?refresh&slices=5&pretty 
	{
	  	"query": {
			"match_all": {}
	  	}
	}
删除单条记录