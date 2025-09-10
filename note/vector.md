### 初始化
```
vector<int> vec2(5); // 创建大小为 5 的 vector，每个元素初始化为 0 (int 的默认值)
vector<string> vec3(3); // 创建大小为 3 的 vector，每个元素初始化为空字符串
vector<int> vec4(5, 10); 
```
**注意后面什么都不写的话才是空vector，如果写了个数字的话可是构造了一些0或者空值的，和数组要区分开**
### 访问元素
- cout << v.front(); // 等价于 v[0]，输出第一个元素
- cout << v.back();  // 等价于 v[v.size()-1]，输出最后一个元素
- size(): 返回当前 vector 中元素的数量。v.push_back(1); // v: [1]
- v.pop_back();弹出

### 插入
```
vector<int> v = {1, 3};
auto it = v.begin() + 1; // 迭代器指向 '3'
v.insert(it, 2); // 在 3 之前插入 2 -> v: [1, 2, 3]

// 插入多个相同元素
v.insert(v.end(), 3, 4); // 在末尾插入 3 个 4 -> v: [1, 2, 3, 4, 4, 4]

// 插入另一个容器的区间
vector<int> source = {5, 6};
v.insert(v.begin(), source.begin(), source.end()); // v: [5, 6, 1, 2, ...]
```
**与图区分，vector的insert需要填写索引，图的insert不需要**
**与list区分，it是可以加n的，list不可以**

### 删除
```
vector<int> v = {10, 20, 30, 40};
v.erase(v.begin() + 1); // 删除第2个元素 (20) -> v: [10, 30, 40]
v.erase(v.begin(), v.begin() + 2); // 删除前两个元素 -> v: [40]
erase可以设置首尾
```

**排序：sort(a.begin(),a.end().cmp),vector没有自己的排序函数**
