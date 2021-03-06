[对称的二叉树](https://leetcode-cn.com/problems/dui-cheng-de-er-cha-shu-lcof/)
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
    bool isSymmetric(TreeNode* root) {
        std::vector<TreeNode*> v;

        std::queue<TreeNode*> q;
        if (root != NULL)
            // 压入根节点
            q.push(root);

        while (q.size() > 0)
        {
            int size = q.size();
            for (int i = 0; i < size; i++)
            {
                TreeNode* node = q.front();

                // 将子节点按从左到右顺序存入数组
                v.push_back(node->left);
                v.push_back(node->right);
                
                if (node->left != NULL)
                    // 压入左子节点
                    q.push(node->left);

                if (node->right != NULL)
                    // 压入右子节点
                    q.push(node->right);
                
                // 弹出当前节点
                q.pop();
            }

            // 检查对称性
            for (int i = 0, j = v.size() - 1; i < j; i++, j--)
            {
                if (v[i] == NULL && v[j] == NULL)
                    continue;

                if (v[i] == NULL && v[j] != NULL)
                    return false;

                if (v[i] != NULL && v[j] == NULL)
                    return false;

                if (v[i]->val != v[j]->val)
                    return false;
            }

            // 清空数组
            v.clear();
        }

        return true;
    }
};
```
