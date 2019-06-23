## redis 操作命令


### 数据类型
- [x] string (字符串)
- [x] hash （哈希 key:value 键值对集合，适合存储对象）
- [x] list （列表 简单的字符串列表 可以添加元素到列表的头部和尾部）
- [x] set (集合 string 类型的无序集合 集合是通过哈希表实现的)
- [x] zset (有序集合 zset和set一样也是string类型的元素集合，且不允许重复成员 不同的是每个元素都会关联一个double类型的分数。通过分数对集合成员从大到小排序 zset的成员是唯一的但score可以重复)

用于记录一些redis 的基础常用命令

### key 操作
#### set key_name value (设置指定的key值 如果key值已经存储其他的值 set会覆盖旧值,且无视类型) 
* set name zhucong

#### get key_name (获取指定key值 如果key存在返回nil 如果key存储值不是字符串 返回一个错误)

* get name //输出:zhucong

#### dump key_name (序列号name 输出序列号后的值)

* dump name //"\x00\azhucong\b\x00\af\xf9\x05\x84\xa5\xc2\x91"

#### exists key_name (判断key是否存在)

* exists name //1

#### expire key_name time_in_seconds (设置有效时间过期后则删除 时间是S 对已经存在的key进行操作)

* expire name 10 //1

#### expireat key_name time_in_unix_timestamp (指定过期时间戳)
* set name tnb
* expireat name 1551341040 //1

#### keys pattern (查找所有符合给定模式 pattern 的 key)
* keys * //(返回所有键名) 输出 name
* set naes test
* keys na* //输出 name test

#### select index (切换到指定的数据库 index为索引号 0作为起始索引值)
* select 6

#### move key_name destination_database (将当前数据库的key值移动到指定的db库中)
* move name 1 //(移动name到1数据库中)
* exists name //0
* select 1
* exists name //1
* expire name 10

#### ttl key_name (以秒为单位返回key的剩余过期时间)
* ttl name //8

#### persist key_name (移除指定的key的过期时间 使key永不过期)
* persist name //1
* ttl name //-1 (表示不过期)

#### del key_name (删除已存在的键 不存在的会被忽略)
* del name //1

* set name zhucoong
* set age 25

#### randomkey (从当前数据库中随机返回一个key)
* randomkey //name

#### rename old_key_name new_key_name
* rename name newname
* get name //nli
* rename newname namecopy
* get namecopy //zhucong

* set name zhucong

#### renamex old_key_name new_key_name 
* rename namecopy name //0 (修改key名不成功)

#### type key_name (返回key的存储值的类型)
* type name //string