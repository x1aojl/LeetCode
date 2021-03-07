# LeetCode

### BFS 广度优先搜索
```
std::queue<T*> q;

// 压入头节点
q.push(root)

while (q.size() > 0)
{
    int size = q.size();
    for (int i = 0; i < size(); i++)
    {
        T* node = q.front();
        for (int j = 0; j < node->children.size(); j++)
            // 压入全部子节点
            q.push(node->children[j]);

        // 弹出当前节点
        q.pop();
    }
}
```
