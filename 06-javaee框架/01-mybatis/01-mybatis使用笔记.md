 mybatis3.4支持日期 

## 1. mybatis-foreach的场景

### 1.1 insert（批量新增）

```
<insert id="insertBatch"  parameterType="java.util.List">
    INSERT INTO game_server (`server_name`,game_id,opening_time,create_time,update_time) values
    <foreach collection ="list" item="item" separator =",">
		( #{item.serverName},
        #{item.gameId},
        #{item.openingTime},
        #{item.createTime},
        #{item.updateTime} )
    </foreach>
</insert>
```

打印的sql是 INSERT INTO 表名 values (值1，值2), (), ()

```
这样处理会有问题
<insert id="insertBatch"  parameterType="java.util.List">
    INSERT INTO game_server (`server_name`,game_id,opening_time,create_time,update_time) values
    <foreach collection ="list" item="item" index= "index" open="(" close=")" separator =",">
		#{item.serverName},
        #{item.gameId},
        #{item.openingTime},
        #{item.createTime},
        #{item.updateTime}
    </foreach>
</insert>
打印的sql是 INSERT INTO 表名 values (值1，值2, 值1，值2)
```



### 1.2 update（批量修改）

第一种是不同记录，固定值的批量更新

```
<update id="updateBatch" parameterType="java.util.Map">
    UPDATE sdk_notice_game set enable = #{enable}, update_time = #{updateTime}
    where id in
    <foreach item="item" index="index" collection="idList" open="(" separator="," close=")">
        #{item}
    </foreach>
</update>
```

第二种是不同记录，不同值的批量更新 多条一起执行，类似于有缓存

```
    <update id="batchUpdate" parameterType="java.util.Map">
        <!-- 接收list参数，循环着组装sql语句，注意for循环的写法
             separator=";" 代表着每次循环完，在sql后面放一个分号
             item="cus" 循环List的每条的结果集
             collection="list" list 即为 map传过来的参数key -->
        <foreach collection="list" separator=";" item="cus">
            update t_customer set
            c_name = #{cus.name},
            c_age = #{cus.age},
            c_sex = #{cus.sex},
            c_ceroNo = #{cus.ceroNo},
            c_ceroType = #{cus.ceroType}
            where id = #{cus.id}
        </foreach>
    </update>
```




### 1.3 select（查询）

```
<if test="@Ognl@isNotEmpty(idList)" >
    and id in
    <foreach collection="idList" index="index" item="item" open="(" separator="," close=")">
        #{item}
    </foreach>
</if>
```

判断或者改为 <if test="idList != null" >



## 2. 返回值为Map（不推荐，推荐使用vo来接收）

<http://blog.csdn.net/yu491833661/article/details/49335899>

 返回map 有些点需要 注意，字段名称的大小写问题

