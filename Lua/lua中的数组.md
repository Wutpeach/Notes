## 数组

数组，就是相同数据类型的元素按一定顺序排列的集合，可以是一维数组和多维数组。

Lua 数组的索引键值可以使用整数表示，数组的大小不是固定的。

### 数组定义

在定义变量时，把值用中括号**{}**括起来，那么一个数组就定义完成了

```lua
a = {};
b = {1,2,3};
c = {'哈罗', 1, 2, '哈哈'}
```

### 一维数组

一维数组是最简单的数组，其逻辑结构是线性表。一维数组可以用for循环出数组中的元素

```lua
array = {"Lua", "Tutorial"};

for i= 0, 2 do
   print(array[i]);
end
```

默认状态下，数组的索引值是从1开始的，这一点有别于JS，但是我们可以通过方法来指定数组从任意值开始索引

```lua
--初始化数组
array = {}
--为这个数组添加数组元素
for i= -2, 2 do
   array[i] = i *2
end
--通过for循环遍历数组值
for i = -2,2 do
   print(array[i])
end
```

### 多维数组

多维数组即**数组中包含数**组或**一维数组的索引键**对应一个数组。

以下是一个三行三列的阵列多维数组：

```lua
-- 初始化数组
array = {}
for i=1,3 do
   array[i] = {}
      for j=1,3 do
         array[i][j] = i*j
      end
end

-- 访问数组
for i=1,3 do
   for j=1,3 do
      print(array[i][j])
   end
end
```

### 数组中的键值对索引

```lua
--初始化数组
a = {'a','b',name = '哈哈','c'}
--[[
在a这个数组中，有4个值，分别是'a'，'b'，name = '哈哈','c'
而他们对应的键值为，1，2，name，3
因为name在数组中属于键值对，它有自己的键，所以数组会忽略它，并把默认的键3赋予它身后的值。
所以我们在我们需要读取a数组中的'c'值时，可以用以下语句
]]--
print(a[3]); --输出'c'
--如果我们要读取键值对的内容，可以用以下语句
print(a['name']) --输出'哈哈'
```

### 对已存在的表进行写入

```lua
a = {1,2,3}
--如果要对a表写入新值，可以用以下2种方式
--方式1
a[4] = 4;
--方式2
a.test = 5; --语法糖，写法上不严格
或者
a['test'] = 5; --严格写法，推荐使用

--最终表的内容为
a = {1,2,3,4,test = 5}
```

### 对已存在的表进行读取

```lua
a = {'a','b',name = '哈哈','c'}
--读取a，b，c，3个值
print(a[1]); --输出'a'
print(a[2]); --输出'b'
print(a[3]); --输出'c'，这里的键3不等于name的解释在【数组中的键值对索引】有解释
--读取name的值
print(a['name']) --输出'哈哈'
--还有一种读取数组内键值对的方法
test = 'name'; --先为test赋值'name'
print(a[test]); --'name'会替代test,实现对表内值读取，效果如>7
```

### 遍历数组

```lua
--[[
遍历数组主要使用for循环，for循环的基本语法如下
]]--
for k, v in ipairs(table) do
    --block
end
或者
for k, v in pairs(table) do
    --block
end
--k，v只是一个形参不需要提前定义，广义上认定k=key（键）；v=value（值）
--方法ipairs和pairs的区别前者不会打印键值对，后者会把键值对也打印出来：先遍历所有下标，遍历完下标后再遍历键值对

```

### 多维数组小案例

```lua
--初始化数组
Street = {};
--在数组中写入一个数组1
Street['杭州'] = 
{
    1,
    2,
    3,
    4,
    5
};
--在数组中再写入一个数组2
Street['金华'] = 
{
    '测试一',
    '测试二',
    '测试三'
};
--最终表
Street = 
{
    杭州 = {1,2,3,4,5},
    金华 = {'测试一', '测试二', '测试三'}
}
--用for循环遍历杭州
for k,v in ipairs(Street['杭州']) do
    print(k,v)
end
--随机遍历杭州
mth.randomseed(os.time()) --定义随机种子
function CreatAdd (city) --定义CreatAdd函数
    if Street[city].re == nil or Street[city].re == 0 then --在Street[city]数组中新添加一个re键值对，此时的re未nil值
        Street[city].re = #Street[city] --将re键值对赋值为Street[city]的长度，#不会读取键值对，所以该值为5
    end
    local c = math.random(Street[city].re) --在1-5中随机取值并把值赋给c
    local s = Street[city][c] --得到Street[city][随机值]中的值，比如4
    Street[cicty][c] = Street[city][Street[city].re] --把数组第5位的值赋给第4位
    Street[city][Street[city].re] = s --把数组第4位的值赋给第4位
    Street[city].re = Street[city].re -1 --把数组的长度-1
    return city..s
end
for i=1,5 do
    print(CreatAdd('杭州'))
end
```

