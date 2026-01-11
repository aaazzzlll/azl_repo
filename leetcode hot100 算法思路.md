# 二叉树

1. 二叉树的直径
递归：使用ans全局记录所有路径中节点数的最大值，初始值为1。递归函数返回值是Node子树的深度，题目要求的是边数，最终结果是ans-1

2. 二叉树的层序遍历
使用res数组保存结果，queue搭配while循环，每进行一次循环都是对当前层的节点进行遍历。
在while循环内部使用for循环，每取出一个节点就往队列中添加他的左右子节点（存在则添加，不存在不添加），同时将该节点的值push到res[res.length-1]中

3. 将有序数组转换为二叉搜索树
使用递归思想，总是选择中间位置左边的数字作为根节点，根节点的下标为 mid=(left+right)/2，递归求根节点的左右子节点

4. 验证二叉搜索树
迭代：使用中序遍历思想，判断pop出的当前节点值是否大于前一个节点的值，如果大于inorder=root.val,否则return false
递归：根节点的合法值域是 `(-∞, +∞)`，无边界限制；
       递归左子树收缩右边界，递归右子树收缩左边界；
       每个节点必须严格在 `(lower, upper)` 范围内，且左右子树都合法。

5. 二叉搜索树中第K小的元素
使用层序遍历二叉搜索树，将每一层的最后一个节点值保存到res中

6. 二叉树展开为链表
使用前序遍历递归算法得到保存二叉树前序遍历序列的list，然后将里面的节点left赋值为null，right设为下一个节点

7. 从前序与中序遍历序列构造二叉树
```
/**
 * @param {number[]} preorder
 * @param {number[]} inorder
 * @return {TreeNode}
 */
var buildTree = function(preorder, inorder) {
    const n = preorder.length;
    // 1. 构造哈希映射（JS用普通对象模拟Map），快速定位中序遍历中根节点的索引
    const indexMap = {};
    for (let i = 0; i < n; i++) {
        indexMap[inorder[i]] = i;
    }

    // 2. 递归构建树的核心函数
    // preLeft: 前序遍历的左边界
    // preRight: 前序遍历的右边界
    // inLeft: 中序遍历的左边界
    // inRight: 中序遍历的右边界
    const myBuildTree = function(preLeft, preRight, inLeft, inRight) {
        // 递归终止条件：边界交叉，说明子树为空
        if (preLeft > preRight) {
            return null;
        }

        // 3. 找到前序遍历中的根节点（前序第一个元素）
        const preRoot = preLeft;
        // 4. 从哈希表中快速找到根节点在中序遍历中的索引
        const inRoot = indexMap[preorder[preRoot]];

        // 5. 构建当前层的根节点
        const root = new TreeNode(preorder[preRoot]);
        // 6. 计算左子树的节点数量（关键：用于拆分前序遍历的左右子树）
        const sizeLeftSubtree = inRoot - inLeft;

        // 7. 递归构建左子树
        // 前序左边界：preLeft + 1（根节点下一个）
        // 前序右边界：preLeft + sizeLeftSubtree（左子树的最后一个元素）
        // 中序左边界：inLeft（原左边界）
        // 中序右边界：inRoot - 1（根节点左边的最后一个元素）
        root.left = myBuildTree(preLeft + 1, preLeft + sizeLeftSubtree, inLeft, inRoot - 1);

        // 8. 递归构建右子树
        // 前序左边界：preLeft + sizeLeftSubtree + 1（左子树之后的第一个元素）
        // 前序右边界：preRight（原右边界）
        // 中序左边界：inRoot + 1（根节点右边的第一个元素）
        // 中序右边界：inRight（原右边界）
        root.right = myBuildTree(preLeft + sizeLeftSubtree + 1, preRight, inRoot + 1, inRight);

        // 9. 返回当前构建好的根节点
        return root;
    };

    // 10. 调用递归函数，初始边界是整个遍历序列的范围
    return myBuildTree(0, n - 1, 0, n - 1);
};
```
