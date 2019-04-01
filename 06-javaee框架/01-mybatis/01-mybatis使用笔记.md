 mybatis3.4支持日期 

## 1. mybatis-foreach的场景

### 1.1 insert（批量新增）

```
<insert id="insertBatch"  parameterType="java.util.List">
    INSERT INTO game_server (`server_name`,game_id,opening_time,create_time,update_time) values
    <foreach collection ="list" item="item" index= "index" separator =",">
        (   #{item.serverName,jdbcType=BIGINT},
        #{item.gameId,jdbcType=BIGINT},
        #{item.openingTime,jdbcType=TIMESTAMP},
        #{item.createTime,jdbcType=TIMESTAMP},
        #{item.updateTime,jdbcType=TIMESTAMP})
    </foreach >
</insert>
```



### 1.2 update（批量修改）

```
<update id="updateBatch" parameterType="java.util.Map">
    UPDATE sdk_notice_game set enable = #{enable}, update_time = #{updateTime}
    where id in
    <foreach item="item" index="index" collection="idList" open="(" separator="," close=")">
        #{item}
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

