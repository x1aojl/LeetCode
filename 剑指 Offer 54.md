[二叉搜索树的第k大节点](https://leetcode-cn.com/problems/er-cha-sou-suo-shu-de-di-kda-jie-dian-lcof/)
```
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int kthLargest(TreeNode* root, int k) {
        std::vector<int> v;

        std::queue<TreeNode*> q;
        if (root != NULL)
            // 压入根节点
            q.push(root);

        while (q.size())
        {
            int size = q.size();
            for (int i = 0; i < size; i++)
            {
                TreeNode* node = q.front();

                // 记录当前节点值
                v.push_back(node->val);

                if (node->left != NULL)
                    // 压入左子节点
                    q.push(node->left);

                if (node->right != NULL)
                    // 压入右子节点
                    q.push(node->right);


                // 弹出当前节点
                q.pop();
            }
        }

        // 升序排序
        std::sort(v.begin(), v.end());
        return v[v.size() - k];
    }
};
```
