# 🐍 Python 青少年编程课（课堂讲义版）

## 第六课：Dict 与 Set —— 高效的“查找字典”

---

## 一、教学目标（本节 40～45 分钟）

本课结束后，学生能够：

1. 理解字典（Dict）的概念——键值对的映射。
2. 掌握字典的创建、访问、增删改查操作。
3. 运用字典解决实际问题（如数据关联、计数等）。
4. 了解集合（Set）的特性与用途——去重与集合操作。
5. 独立完成"学生信息管理系统"小练习。

---

## 二、课堂流程（建议）

| 环节 | 时间 | 教师动作 | 学生活动 |
| --- | --- | --- | --- |
| 导入 | 5 min | 用"字典"的比喻 | 理解键值映射 |
| 新授1：字典基础 | 8 min | 演示字典的创建与访问 | 跟着输入代码 |
| 新授2：字典操作 | 10 min | 讲解增删改查方法 | 观察字典变化 |
| 新授3：集合与对比 | 10 min | 演示集合的特性 | 对比实验 |
| 实战练习 | 8 min | 发布"信息系统"任务 | 独立管理数据 |
| 总结与挑战 | 4 min | 回顾知识点，布置挑战 | 提交答案 |

---

## 三、导入话术（可直接使用）

"同学们，假设你要保存 100 个学生的信息：
- 用列表？`[92, 85, 78, 95]`——没人知道 92 属于谁！
- 用变量？`score_xiaoming = 92, score_xiaohong = 85`——得个 100 个变量！

有没有办法把'名字'和'分数'关联起来？
答案是**字典**！它像真正的字典一样：根据'单词'（键）快速查找'定义'（值）。"

---

## 四、核心知识讲解

### 1）什么是字典（Dictionary）

字典是一种**键值对**的有序集合。每个值都通过一个唯一的**键**来访问。

#### 1.1 字典 vs 列表

```python
# ❌ 用列表（无意义）
scores = [92, 85, 78]  # 谁是谁？

# ✅ 用字典（清晰）
scores = {
    "小明": 92,
    "小红": 85,
    "小刚": 78
}
print(scores["小明"])  # 92
```

#### 1.2 创建字典

```python
# 方式1：直接定义
student = {
    "name": "小明",
    "age": 15,
    "grade": 9,
    "score": 92
}

# 方式2：混合类型
mixed = {
    "string": "hello",
    "number": 42,
    "list": [1, 2, 3],
    "bool": True
}

# 方式3：空字典
empty_dict = {}

# 方式4：dict() 函数
dict_from_tuples = dict([("a", 1), ("b", 2)])
# {"a": 1, "b": 2}

# 方式5：fromkeys() 创建相同值的字典
keys_dict = dict.fromkeys(["x", "y", "z"], 0)
# {"x": 0, "y": 0, "z": 0}
```

### 2）字典的访问与查询

#### 2.1 访问值

```python
person = {
    "name": "张三",
    "age": 25,
    "city": "北京"
}

# 方式1：直接索引
print(person["name"])  # 张三

# 方式2：get() 方法（更安全）
print(person.get("age"))  # 25
print(person.get("job"))  # None（不会报错）
print(person.get("job", "未知"))  # 未知（有默认值）

# ❌ 危险：如果键不存在会报错
# print(person["job"])  # KeyError!
```

#### 2.2 检查键是否存在

```python
data = {"a": 1, "b": 2}

if "a" in data:
    print("键 'a' 存在")

if "c" not in data:
    print("键 'c' 不存在")
```

#### 2.3 获取所有键、值、项

```python
book = {
    "title": "Python 100 天",
    "author": "何峻",
    "pages": 500
}

# 获取所有键
print(book.keys())    # dict_keys(['title', 'author', 'pages'])

# 获取所有值
print(book.values())  # dict_values(['Python 100 天', '何峻', 500])

# 获取所有(键, 值)对
print(book.items())   # dict_items([('title', 'Python 100 天'), ...])

# 遍历
for key in book.keys():
    print(f"{key}: {book[key]}")

for key, value in book.items():
    print(f"{key}: {value}")
```

### 3）字典的增删改查（CRUD）

#### 3.1 增加（Add）

```python
student = {"name": "小明", "score": 90}

# 添加新键值对
student["age"] = 15
student["city"] = "北京"
print(student)
# {"name": "小明", "score": 90, "age": 15, "city": "北京"}

# setdefault()：如果键不存在则添加
student.setdefault("grade", 9)  # 添加
student.setdefault("name", "新名字")  # 键已存在，不改
print(student)
```

#### 3.2 删除（Delete）

```python
data = {"a": 1, "b": 2, "c": 3}

# pop()：删除并返回值
value = data.pop("a")
print(value)  # 1
print(data)   # {"b": 2, "c": 3}

# pop() 如果键不存在有默认值
data.pop("x", None)  # 不报错

# del：删除指定键
del data["b"]
print(data)   # {"c": 3}

# clear()：清空字典
data.clear()
print(data)   # {}

# popitem()：删除最后一个项
d = {"x": 1, "y": 2}
key, value = d.popitem()
print(key, value)  # y 2
```

#### 3.3 改（Update）

```python
config = {"language": "python", "version": "3.11"}

# 方式1：直接赋值
config["language"] = "java"

# 方式2：update() 多个键值对
config.update({"version": "3.12", "debug": True})
print(config)
# {"language": "java", "version": "3.12", "debug": True}
```

### 4）字典的遍历与推导式

#### 4.1 遍历字典

```python
scores = {"小明": 90, "小红": 85, "小刚": 92}

# 遍历键
for name in scores:
    print(name)

# 遍历值
for score in scores.values():
    print(score)

# 遍历键值对（推荐）
for name, score in scores.items():
    print(f"{name}: {score}")
```

#### 4.2 字典推导式

```python
# 基础推导式
numbers = {i: i**2 for i in range(1, 6)}
print(numbers)  # {1: 1, 2: 4, 3: 9, 4: 16, 5: 25}

# 带条件的推导式
age_group = {
    name: age
    for name, age in {"小明": 15, "小红": 18, "小刚": 12}.items()
    if age >= 15
}
print(age_group)  # {"小明": 15, "小红": 18}

# 字符串列表转字典
words = ["apple", "banana", "cherry"]
word_lengths = {word: len(word) for word in words}
print(word_lengths)
# {"apple": 5, "banana": 6, "cherry": 6}
```

### 5）集合（Set）

#### 5.1 什么是集合

集合是一个**无序、不重复**的元素集合。

```python
# 集合的特性
fruits = {"苹果", "香蕉", "苹果", "橙子"}
print(fruits)  # {"苹果", "香蕉", "橙子"}  ← 自动去重！

# ⚠️ 注意：{} 是空字典，不是空集合
empty_dict = {}
empty_set = set()
```

#### 5.2 创建集合

```python
# 方式1：直接定义
set1 = {1, 2, 3, 4}

# 方式2：混合类型
set2 = {"a", 1, 3.14, True}

# 方式3：set() 函数
set3 = set([1, 2, 2, 3, 3, 3])
print(set3)  # {1, 2, 3}  ← 去重了

# 方式4：从字符串
set4 = set("hello")
print(set4)  # {'h', 'e', 'l', 'o'}  ← 'l' 只出现一次
```

#### 5.3 集合的操作

```python
# 添加
s = {1, 2, 3}
s.add(4)
print(s)  # {1, 2, 3, 4}

# 删除
s.discard(2)  # 存在就删，不存在也不报错
print(s)  # {1, 3, 4}

# remove() 如果不存在会报错
# s.remove(99)  # KeyError

# 检查包含
print(3 in s)  # True

# 长度
print(len(s))  # 3

# 清空
s.clear()
print(s)  # set()
```

#### 5.4 集合的数学运算

集合可以进行**并集、交集、差集、对称差**等运算。

```python
set_a = {1, 2, 3, 4}
set_b = {3, 4, 5, 6}

# 并集（Union）：所有元素
print(set_a | set_b)  # {1, 2, 3, 4, 5, 6}
print(set_a.union(set_b))

# 交集（Intersection）：共有元素
print(set_a & set_b)  # {3, 4}
print(set_a.intersection(set_b))

# 差集（Difference）：在 A 但不在 B
print(set_a - set_b)  # {1, 2}
print(set_a.difference(set_b))

# 对称差（Symmetric difference）：不重合的部分
print(set_a ^ set_b)  # {1, 2, 5, 6}
print(set_a.symmetric_difference(set_b))

# 子集判断
print({1, 2} <= set_a)  # True
print({1, 7} <= set_a)  # False

# 超集判断
print(set_a >= {1, 2})  # True
```

### 6）Dict vs Set

| 特性 | Dict | Set |
| --- | --- | --- |
| **符号** | `{}` 或 `dict()` | `{}` 或 `set()` |
| **元素** | 键值对 | 单个元素 |
| **有序** | ✅ 有序 | ❌ 无序 |
| **重复** | 键不重复 | ❌ 不重复 |
| **用途** | 关联数据 | 去重、集合运算 |

### 7）实用案例

#### 7.1 计数器（Counter）

```python
# 统计每个元素出现的次数
sentence = "hello python"

counter = {}
for char in sentence:
    if char in counter:
        counter[char] += 1
    else:
        counter[char] = 1

print(counter)
# {'h': 1, 'e': 1, 'l': 2, 'o': 2, ' ': 1, 'p': 1, 'y': 1, 't': 1, 'n': 1}

# 或更优雅的方式
from collections import Counter
result = Counter(sentence)
print(result)
```

#### 7.2 分组（Grouping）

```python
# 按年龄分组
students = [
    {"name": "小明", "age": 15},
    {"name": "小红", "age": 16},
    {"name": "小刚", "age": 15},
    {"name": "小李", "age": 16}
]

# 按年龄分组
groups = {}
for student in students:
    age = student["age"]
    if age not in groups:
        groups[age] = []
    groups[age].append(student["name"])

print(groups)
# {15: ['小明', '小刚'], 16: ['小红', '小李']}
```

#### 7.3 去重并排序

```python
# 去除重复元素并排序
numbers = [3, 1, 4, 1, 5, 9, 2, 6, 5, 3]

# 方式1：使用集合
unique = sorted(set(numbers))
print(unique)  # [1, 2, 3, 4, 5, 6, 9]

# 方式2：使用字典（保持原顺序）
unique_dict = {}
for num in numbers:
    unique_dict[num] = None
print(sorted(unique_dict.keys()))
```

---

## 五、课堂练习：学生信息管理系统

### 任务1：基础学生档案

```python
# 创建学生信息
students_db = {
    "小明": {"age": 15, "score": 92, "city": "北京"},
    "小红": {"age": 16, "score": 88, "city": "上海"},
    "小刚": {"age": 15, "score": 95, "city": "深圳"}
}

# 查询某个学生信息
name = "小明"
if name in students_db:
    info = students_db[name]
    print(f"{name} 的信息:")
    for key, value in info.items():
        print(f"  {key}: {value}")

# 添加新学生
students_db["小李"] = {"age": 14, "score": 85, "city": "广州"}

# 修改学生信息
students_db["小明"]["score"] = 95

# 删除学生
del students_db["小刚"]

print(f"\n现有学生: {list(students_db.keys())}")
```

### 任务2：成绩统计

```python
# 成绩列表
grades = {
    "小明": 92,
    "小红": 85,
    "小刚": 92,
    "小李": 88,
    "小王": 95
}

# 统计最高分和最低分
max_score = max(grades.values())
min_score = min(grades.values())
print(f"最高分: {max_score}, 最低分: {min_score}")

# 计算平均分
avg_score = sum(grades.values()) / len(grades)
print(f"平均分: {avg_score:.2f}")

# 找出及格（≥60）的学生
passed = {name: score for name, score in grades.items() if score >= 60}
print(f"及格的学生: {passed}")

# 按分数排序
sorted_grades = sorted(grades.items(), key=lambda x: x[1], reverse=True)
print("排名:")
for rank, (name, score) in enumerate(sorted_grades, 1):
    print(f"  {rank}. {name}: {score}")
```

### 任务3：集合操作——课程选择

```python
# 三个班级的选课学生
class_a = {"小明", "小红", "小刚", "小李"}
class_b = {"小刚", "小李", "小王", "小张"}
class_c = {"小李", "小王", "小周"}

print("=== 集合运算 ===")

# 所有选课的学生
all_students = class_a | class_b | class_c
print(f"所有选课学生: {all_students}")

# 三个班都选课的学生
all_three = class_a & class_b & class_c
print(f"三个班都选的: {all_three}")

# 只在 A 班的学生
only_a = class_a - class_b - class_c
print(f"只在 A 班的: {only_a}")

# A 班和 B 班共有的学生
ab_shared = class_a & class_b
print(f"A 和 B 的共有: {ab_shared}")

# 统计
print(f"\n总共 {len(all_students)} 个学生")
```

### 任务4：单词频率统计

```python
# 文本分析
text = "python is awesome python is great python is fun"

# 方式1：用字典计数
word_count = {}
for word in text.split():
    word_count[word] = word_count.get(word, 0) + 1

print("词频统计 (字典):")
for word, count in sorted(word_count.items(), key=lambda x: x[1], reverse=True):
    print(f"  {word}: {count}")

# 方式2：用集合找出唯一单词
unique_words = set(text.split())
print(f"\n唯一单词数: {len(unique_words)}")
print(f"唯一单词: {sorted(unique_words)}")
```

---

## 六、课后挑战（分层）

### A 级（基础）

1. 创建一个字典表示你的信息（名字、年龄、城市）
2. 添加一个新的键值对
3. 删除其中一个键

### B 级（提高）

**创建一个简单的"电话簿"系统：**

```python
phonebook = {}

def add_contact(name, phone):
    phonebook[name] = phone
    print(f"✅ 已添加 {name}")

def search_contact(name):
    return phonebook.get(name, "未找到")

def list_contacts():
    return phonebook

# 补全代码并测试
add_contact("小明", "13800138000")
add_contact("小红", "13900139000")
print(search_contact("小明"))
```

### C 级（挑战）

**实现一个"数据去重并统计频率"的系统：**

```python
def analyze_data(items):
    """
    输入: [1, 2, 2, 3, 1, 3, 3, 4]
    输出: 
    - 唯一元素: {1, 2, 3, 4}
    - 频率: {1: 2, 2: 2, 3: 3, 4: 1}
    - 最常见: 3
    """
    
    unique = set(items)
    frequency = {item: items.count(item) for item in unique}
    most_common = max(frequency, key=frequency.get)
    
    return {
        "unique": unique,
        "frequency": frequency,
        "most_common": most_common
    }

result = analyze_data([1, 2, 2, 3, 1, 3, 3, 4])
print(result)
```

---

## 七、知识总结卡

```
┌─────────────────────────────────────────────┐
│          Dict 与 Set 对比                  │
├─────────────────────────────────────────────┤
│ Dict: {"key": value}  键值对映射           │
│       访问: dict["key"]   有序、可重复键   │
│                                             │
│ Set: {1, 2, 3}        单个元素集合         │
│      - 无序、不重复    & | - ^ 集合运算    │
└─────────────────────────────────────────────┘

┌─────────────────────────────────────────────┐
│          Dict 的 5 个关键方法               │
├─────────────────────────────────────────────┤
│ dict[key]        - 访问值（可能报错）     │
│ dict.get(key)    - 安全访问                │
│ dict.keys()      - 获所有键                │
│ dict.values()    - 获所有值                │
│ dict.items()     - 获所有键值对            │
└─────────────────────────────────────────────┘

┌─────────────────────────────────────────────┐
│          Set 的集合运算                     │
├─────────────────────────────────────────────┤
│ A | B   并集（含A和B所有元素）            │
│ A & B   交集（A和B共有的）                │
│ A - B   差集（在A但不在B）                │
│ A ^ B   对称差（要么A要么B）              │
└─────────────────────────────────────────────┘
```

