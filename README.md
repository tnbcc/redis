## redis 操作命令


### 数据类型
- [x] string (字符串)
- [x] hash （哈希 key:value 键值对集合，适合存储对象）
- [x] list （列表 简单的字符串列表 可以添加元素到列表的头部和尾部）
- [x] set (集合 string 类型的无序集合 集合是通过哈希表实现的) 
- [x] zset (有序集合 zset和set一样也是string类型的元素集合，且不允许重复成员 不同的是每个元素都会关联一个double类型的分数。通过分数对集合成员从大到小排序 zset的成员是唯一的但score可以重复)

用于记录一些redis 的基础常用命令

### key 操作
-- set key_name value (设置指定的key值 如果key值已经存储其他的值 set会覆盖旧值,且无视类型) 
> 