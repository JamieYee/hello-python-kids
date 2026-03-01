# 🐍 Python 青少年编程课（课堂讲义版）

## 第三课：List 与 Tuple —— 数据的“收纳盒”

---

## 一、教学目标（本节 40～45 分钟）

本课结束后，学生能够：

1. 理解什么是列表（List），与单个变量的区别。
2. 掌握列表的创建、索引、切片、增删改查操作。
3. 了解元组（Tuple）的特性与使用场景。
4. 区分 List 和 Tuple 的可变性差异。
5. 独立完成"宝可梦背包"小练习。

---

## 二、课堂流程（建议）

| 环节 | 时间 | 教师动作 | 学生活动 |
| --- | --- | --- | --- |
| 导入 | 5 min | 用"收纳盒"比喻列表 | 想象多个物品的存储 |
| 新授1：列表基础 | 8 min | 演示列表创建与索引 | 跟着输入代码 |
| 新授2：列表操作 | 10 min | 讲解增删改查方法 | 观察每个方法的效果 |
| 新授3：元组与对比 | 10 min | 演示元组的不可变性 | 对比实验 |
| 实战练习 | 8 min | 发布"背包"任务 | 独立管理列表 |
| 总结与挑战 | 4 min | 回顾知识点，布置挑战 | 提交答案 |

---

## 三、导入话术（可直接使用）

"同学们，还记得上节课的'收纳盒'吗？一个盒子只能放一个东西。
但如果我想存100个宝可梦呢？难道要把100个盒子都贴标签？
今天我们学一个新的魔法盒子——**列表**。
它可以一次装下很多东西，而且我们能轻松地加东西、删东西、改东西。让我们开始吧！"

---

## 四、核心知识讲解

### 1）什么是列表（List）

列表是一个**有序、可变**的集合，用于存储**多个数据**。

#### 1.1 列表与单个变量的对比

```python
# ❌ 不用列表的方式
pokemon1 = "皮卡丘"
pokemon2 = "小火龙"
pokemon3 = "妙蛙种子"
pokemon4 = "杰尼龟"
# 100 个宝可梦？太麻烦了！

# ✅ 用列表的方式
pokemons = ["皮卡丘", "小火龙", "妙蛙种子", "杰尼龟"]
```

#### 1.2 列表的创建

```python
# 方式1：直接赋值
my_list = [1, 2, 3, 4, 5]

# 方式2：混合类型
mixed_list = ["名字", 100, 3.14, True]

# 方式3：空列表
empty_list = []

# 方式4：list() 函数
numbers = list(range(1, 6))  # [1, 2, 3, 4, 5]
```

#### 1.3 列表的长度

```python
fruits = ["苹果", "香蕉", "橙子"]
print(len(fruits))  # 3
```

### 2）列表的索引与切片

#### 2.1 索引（正向与反向）

规则：和字符串一样，从 0 开始。

```python
heroes = ["盖伦", "德玛西亚", "提莫", "金属", "瑞兹"]
# 索引:        0        1      2      3     4
# 反向:       -5       -4     -3     -2    -1

print(heroes[0])   # 盖伦
print(heroes[-1])  # 瑞兹
print(heroes[2])   # 提莫
```

快问快答：

- `heroes[3]` 输出什么？
- `heroes[-2]` 输出什么？

#### 2.2 切片（Slice）

语法：`list[开始:结束:步长]`

规则：**包括开始，不包括结束**

```python
numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

# 基础切片
print(numbers[2:5])      # [2, 3, 4]  从 index 2 到 4
print(numbers[:3])       # [0, 1, 2]  从开始到 index 2
print(numbers[7:])       # [7, 8, 9]  从 index 7 到末尾
print(numbers[:])        # [0, 1, 2, ..., 9]  复制整个列表

# 带步长的切片
print(numbers[::2])      # [0, 2, 4, 6, 8]  每隔 2 个取一个
print(numbers[1::2])     # [1, 3, 5, 7, 9]  从 index 1 开始，每隔 2 个
print(numbers[::-1])     # [9, 8, 7, ..., 0]  反向

# 反向切片
print(numbers[-3:])      # [7, 8, 9]  最后 3 个
print(numbers[:-2])      # [0, 1, ..., 7]  除了最后 2 个
```

### 3）列表的增删改查

#### 3.1 增（Add）：append() 和 insert()

```python
my_list = [1, 2, 3]

# append()：在末尾添加
my_list.append(4)
print(my_list)  # [1, 2, 3, 4]

# insert()：在指定位置插入
my_list.insert(1, 99)
print(my_list)  # [1, 99, 2, 3, 4]

# 一次添加多个（扩展）
my_list.extend([5, 6, 7])
print(my_list)  # [1, 99, 2, 3, 4, 5, 6, 7]
```

#### 3.2 删（Remove）：pop()、remove()、clear()

```python
my_list = ['a', 'b', 'c', 'd', 'e']

# pop()：删除指定索引的元素，并返回该元素
removed = my_list.pop(2)  # 删除 'c'
print(removed)  # c
print(my_list)  # ['a', 'b', 'd', 'e']

# pop() 默认删除最后一个
last = my_list.pop()  # 删除 'e'
print(last)  # e
print(my_list)  # ['a', 'b', 'd']

# remove()：删除第一个匹配的值
my_list.remove('b')
print(my_list)  # ['a', 'd']

# clear()：清空列表
my_list.clear()
print(my_list)  # []
```

#### 3.3 改（Update）：直接赋值

```python
scores = [90, 85, 92, 78]

# 修改单个元素
scores[2] = 95
print(scores)  # [90, 85, 95, 78]

# 修改一段（切片赋值）
scores[1:3] = [88, 90]
print(scores)  # [90, 88, 90, 78]

# 替换为不同长度的列表
scores[1:3] = [99]
print(scores)  # [90, 99, 78]
```

#### 3.4 查（Query）：index() 和 in

```python
fruits = ["苹果", "香蕉", "橙子", "葡萄"]

# index()：查找元素的位置
pos = fruits.index("香蕉")
print(pos)  # 1

# in：检查元素是否存在
if "苹果" in fruits:
    print("有苹果")  # ✅ 输出这行

if "榴莲" in fruits:
    print("有榴莲")  # ❌ 不输出

# count()：计算某元素出现次数
colors = ['红', '蓝', '红', '绿', '红']
print(colors.count('红'))  # 3
```

### 4）元组（Tuple）

#### 4.1 什么是元组

**元组是一个不可变（Immutable）的集合**。一旦创建，就无法修改。

```python
# 列表（可变）
my_list = [1, 2, 3]
my_list[0] = 99  # ✅ 可以改
print(my_list)  # [99, 2, 3]

# 元组（不可变）
my_tuple = (1, 2, 3)
# my_tuple[0] = 99  # ❌ TypeError!
```

#### 4.2 元组的创建

```python
# 方式1：用圆括号
tuple1 = (1, 2, 3)

# 方式2：混合类型
tuple2 = ("名字", 100, True)

# 方式3：单元素元组（注意逗号！）
single = (42,)  # ✅
wrong = (42)    # ❌ 这只是括号表达式，不是元组

# 方式4：tuple() 函数
tuple3 = tuple([1, 2, 3])  # (1, 2, 3)

# 方式5：不用圆括号（隐式元组）
auto_tuple = 1, 2, 3  # (1, 2, 3)
```

#### 4.3 元组的索引和切片（和列表一样）

```python
coords = (100, 200, 50)

print(coords[0])   # 100
print(coords[:2])  # (100, 200)
print(len(coords)) # 3
```

#### 4.4 元组的操作（只有查，没有增删改）

```python
my_tuple = (1, 2, 3)

# ✅ 可以这样
print(my_tuple[0])      # 1
print(len(my_tuple))    # 3
print(2 in my_tuple)    # True
print(my_tuple.count(2))  # 1

# ❌ 不能这样
# my_tuple[0] = 99       # TypeError!
# my_tuple.append(4)     # AttributeError!
# del my_tuple[0]        # TypeError!
```

### 5）List vs Tuple 对比

| 特性 | List | Tuple |
| --- | --- | --- |
| **符号** | `[]` | `()` |
| **可变性** | ✅ 可变 | ❌ 不可变 |
| **性能** | 较慢 | ⚡ 较快 |
| **内存** | 占用更多 | 占用更少 |
| **增删改** | append/remove/pop | ❌ 无 |
| **用途** | 频繁修改的数据 | 固定的数据 |

**何时用元组？**

```python
# 1. 函数返回多个值
def get_player_info():
    return ("小明", 25, "北京")  # 用元组返回

name, age, city = get_player_info()

# 2. 作为字典的 key（列表不行）
location_map = {}
location_map[("北京", "朝阳")] = "某街道"  # ✅ 元组可以
# location_map[[1, 2]] = "fail"  # ❌ 列表不行

# 3. 保存重要的固定数据
DIRECTIONS = ("上", "下", "左", "右")  # 不想被意外修改
```

### 6）列表的遍历与推导式

#### 6.1 用 for 循环遍历

```python
numbers = [1, 2, 3, 4, 5]

# 遍历元素
for num in numbers:
    print(num * 2)
# 输出: 2 4 6 8 10

# 遍历索引
for i in range(len(numbers)):
    print(f"Index {i}: {numbers[i]}")

# 同时遍历索引和元素
for i, num in enumerate(numbers):
    print(f"{i}: {num}")
# 输出:
# 0: 1
# 1: 2
# ...
```

#### 6.2 列表推导式（List Comprehension）

快速创建列表的优雅方式。

```python
# 基础推导式
squares = [x**2 for x in range(1, 6)]
print(squares)  # [1, 4, 9, 16, 25]

# 带条件的推导式
evens = [x for x in range(1, 11) if x % 2 == 0]
print(evens)  # [2, 4, 6, 8, 10]

# 字符串列表推导式
names = ["alice", "bob", "charlie"]
capitals = [name.upper() for name in names]
print(capitals)  # ['ALICE', 'BOB', 'CHARLIE']

# 嵌套推导式
matrix = [[i*j for j in range(1, 4)] for i in range(1, 4)]
print(matrix)
# [[1, 2, 3],
#  [2, 4, 6],
#  [3, 6, 9]]
```

---

## 五、课堂练习：我的宝可梦背包

### 任务1：背包管理系统

```python
# 初始化背包（包含 5 个宝可梦）
backpack = ["皮卡丘", "小火龙", "妙蛙种子", "杰尼龟", "波波"]

print(f"背包里有 {len(backpack)} 只宝可梦: {backpack}")

# 第1步：添加新宝可梦
backpack.append("小霞的golduck")
print(f"捕捉了新宝可梦: {backpack}")

# 第2步：替换第一只（升级了）
backpack[0] = "雷丘"
print(f"皮卡丘进化: {backpack}")

# 第3步：删除第4只（宝可梦逃走了）
escaped = backpack.pop(3)
print(f"{escaped} 逃走了! 现在: {backpack}")

# 第4步：查询和排序
if "小火龙" in backpack:
    pos = backpack.index("小火龙")
    print(f"小火龙在第 {pos+1} 位")

# 第5步：查看最后 3 只
last_three = backpack[-3:]
print(f"最后捕捉的 3 只: {last_three}")
```

### 任务2：成绩处理

```python
# 学生成绩列表
scores = [92, 85, 78, 95, 88, 76, 92]

# 第1步：查询平均分
average = sum(scores) / len(scores)
print(f"平均分: {average:.2f}")

# 第2步：找出最高分和最低分
print(f"最高分: {max(scores)}")
print(f"最低分: {min(scores)}")

# 第3步：统计及格人数（>=60）
passed = len([s for s in scores if s >= 60])
print(f"及格人数: {passed}")

# 第4步：统计 92 分的学生
count_92 = scores.count(92)
print(f"92 分的学生: {count_92} 人")

# 第5步：所有分数加 5 分（老师太好了！）
boosted_scores = [s + 5 for s in scores]
print(f"加分后: {boosted_scores}")

# 第6步：排序
sorted_scores = sorted(scores)
print(f"从低到高: {sorted_scores}")
print(f"从高到低: {sorted(scores, reverse=True)}")
```

### 任务3：命令行背包

```python
# 这是一个简单的背包管理程序（可选实现）

backpack = []

def show_menu():
    print("\n=== 宝可梦背包管理系统 ===")
    print("1. 查看背包")
    print("2. 添加宝可梦")
    print("3. 删除宝可梦")
    print("4. 查询宝可梦")
    print("5. 退出")

def show_backpack(bp):
    if not bp:
        print("背包是空的")
    else:
        for i, pokemon in enumerate(bp, 1):
            print(f"{i}. {pokemon}")

# 简化版示例
def add_pokemon(bp, name):
    bp.append(name)
    print(f"✅ 已添加 {name}")

def remove_pokemon(bp, name):
    if name in bp:
        bp.remove(name)
        print(f"✅ 已移除 {name}")
    else:
        print(f"❌ 没有找到 {name}")

# 测试
backpack = []
add_pokemon(backpack, "皮卡丘")
add_pokemon(backpack, "小火龙")
show_backpack(backpack)
remove_pokemon(backpack, "皮卡丘")
show_backpack(backpack)
```

---

## 六、课后挑战（分层）

### A 级（基础）

1. 创建一个列表 `[1, 2, 3, 4, 5]`，输出：
   - 第 3 个元素
   - 最后一个元素
   - 前 3 个元素（切片）

2. 填空：
   - 向列表添加元素用 `_______()` 方法
   - 从列表删除元素用 `_______()` 方法
   - 查询列表长度用 `_______()` 函数

### B 级（提高）

写一个程序，实现以下功能：

```python
# 输入：一个包含数字的列表
numbers = [5, 2, 8, 2, 9, 1, 2]

# 输出：
# 1. 最大值：____
# 2. 最小值：____
# 3. 元素 2 出现次数：____
# 4. 删除所有 2 后的列表：____
# 5. 列表反向：____
```

### C 级（挑战）

**实现一个简单的"数据去重"函数：**

```python
def remove_duplicates(items):
    """
    移除列表中的重复元素，保持原有顺序
    
    输入: [1, 2, 2, 3, 1, 4, 3]
    输出: [1, 2, 3, 4]
    """
    result = []
    for item in items:
        if item not in result:
            result.append(item)
    return result

test_cases = [
    [1, 2, 2, 3, 1, 4, 3],
    ["苹果", "香蕉", "苹果", "橙子"],
    [True, False, True, False]
]

for case in test_cases:
    print(f"原: {case}")
    print(f"去重后: {remove_duplicates(case)}")
    print()
```

**进阶思考：** 如果想保持原顺序情况下去重，该怎么做？

---

## 七、知识总结卡

```
┌─────────────────────────────────────────────┐
│          List vs Tuple                      │
├─────────────────────────────────────────────┤
│ List:  my_list = [1, 2, 3]  ← 可改、可删  │
│ Tuple: my_tuple = (1, 2, 3) ← 固定不变    │
│                                             │
│ 创建: []括号  删除: pop/remove             │
│ 修改: [i] = x  查询: index/in              │
│ 切片: list[a:b:step]  (list & tuple通用)  │
└─────────────────────────────────────────────┘

┌─────────────────────────────────────────────┐
│       5 个关键方法                          │
├─────────────────────────────────────────────┤
│ append(x)    - 末尾添加                    │
│ insert(i,x)  - 指定位置插入                 │
│ pop(i)       - 删除并返回                  │
│ remove(x)    - 删除第一个匹配              │
│ index(x)     - 查找元素位置                │
└─────────────────────────────────────────────┘
```

