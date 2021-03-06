[二叉树的深度](https://leetcode-cn.com/problems/er-cha-shu-de-shen-du-lcof/)
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
    int maxDepth(TreeNode* root) {
        int depth = 0;

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

                if (node->left != NULL)
                    // 压入左子节点
                    q.push(node->left);

                if (node->right != NULL)
                    // 压入右子节点
                    q.push(node->right);

                // 弹出当前节点
                q.pop();
            }

            // 更新深度值
            depth++;
        }

        return depth;
    }
};
```
