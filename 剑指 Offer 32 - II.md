[从上到下打印二叉树 II](https://leetcode-cn.com/problems/cong-shang-dao-xia-da-yin-er-cha-shu-ii-lcof/)

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
    vector<vector<int>> levelOrder(TreeNode* root) {
        vector<vector<int>> res;
        
        std::queue<TreeNode*> q;
        if (root != NULL)
            // 加入根节点
            q.push(root);

        while (q.size() > 0)
        {
            vector<int> levels;
            int size = q.size();
            for (int i = 0; i < size; i++)
            {
                TreeNode* node = q.front(); 
                levels.push_back(node->val);

                if (node->left != NULL)
                    // 加入左子节点
                    q.push(node->left);

                if (node->right != NULL)
                    // 加入右子节点
                    q.push(node->right);

                q.pop();
            }

            res.push_back(levels);
        }

        return res;
    }
};
```
