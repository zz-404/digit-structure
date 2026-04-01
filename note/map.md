# 支持自动排序功能
- 可以用来表示类似于，一堆数从小到大排，且知道他们的出现次数，的东西
- map<int , int , greater<int>>
- map的迭代器一直有效，特别强大

```
for (auto it = m.begin(); it != m.end(); ++it) {
    if (条件)
        m.erase(it); // ❌ 错误！删除后 it 立刻失效，++it 崩溃
}
for (auto it = m.begin(); it != m.end(); ) {
    if (需要删除)
        it = m.erase(it); // ✅ erase 返回下一个有效迭代器
    else
        ++it;
}
```
