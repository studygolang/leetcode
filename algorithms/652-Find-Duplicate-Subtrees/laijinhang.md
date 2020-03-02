解题思路
利用递归遍历的特性从节点构造出一个序列化字符串

1、如果为空树，直接返回nil
2、除一开始的那个根节点外，其他节点建立节点映射序列化 *TreeNode => string
3、建立完之后，通过序列化映射节点切片，string => []*TreeNode
4、遍历 步骤3，找出序列化字符串 对应的 节点地址，大于1的
5、返回结果

代码

```go
/**
 * 	Definition for a binary tree node.
 * 	type TreeNode struct {
 * 		Val int
 * 		Left *TreeNode
 * 		Right *TreeNode
 *	 }
   */
   func findDuplicateSubtrees(root *TreeNode) []*TreeNode {
   if root == nil {
       return nil
   }
   // 每个节点当成一颗树
   // 记录从那个节点开始的路径
   sbt := make(map[*TreeNode]string)
   usbt := make(map[string][]*TreeNode)

   sbt[root.Left] = SerializedBinaryTree(root.Left, sbt)
   sbt[root.Right] = SerializedBinaryTree(root.Right, sbt)

   for k, v := range sbt {
       usbt[v] = append(usbt[v], k)
   }
   res := []*TreeNode{}
   for _, v := range usbt {
       if len(v) > 1 {
           res = append(res, v[0])
       }

```

