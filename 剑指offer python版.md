##面试总结

###剑指offer

####1.数组查找

**题目**：在一个二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。

**思路**:  对于在一个每一行从左到右依次递增，每一列从上到下依次递增的二维数组查找一个元素，可以选择从数组左上角开始查找array\[i][j]，如果目标元素大于array\[i][j]，i+=1，如果元素小于array\[i][j]，j-=1，依次循环直至找到这个数。

+ Python常用知识：

  数据结构list：创建一个列表，只要把逗号分隔的不同的数据项使用方括号括起来即可

​             eg：list2 = [1, 2, 3, 4, 5 ]

```python
@requires_authorization
# -*- coding:utf-8 -*-
class Solution:
    def Find(self, target, array):
        if array==[]:
            return False
        rawnum=len(array)
        columnum=len(array[0])
        i=0
        j=columnum-1
        while i<rawnum and j>=0:
            if array[i][j]>target:
                j-=1
            elif array[i][j]<target:
                i+=1
            else:
                return True
        return False
array = [[1, 2, 8, 9],
         [2, 4, 9, 12],
         [4, 7, 10, 13],
         [6, 8, 11, 15]]
findtarget = Solution()
print(findtarget.Find(10,array))
```

####2.替换空格

**题目** ：请实现一个函数，将一个字符串中的空格替换成“%20”。例如，当字符串为We Are Happy.则经过替换之后的字符串为We%20Are%20Happy。

**思路** ：直接将‘ ’换成20%

+ Python常用知识：

  replace()函数：字符串常用函数，替换字符

```python
class Solution:
    # s 源字符串
    def replaceSpace(self, s):
        s1=s.replace(' ', '%20')
        return s1
```

####3.从尾到头打印字符串

**题目**：输入一个链表，从尾到头打印链表每个节点的值。

**思路**：将节点保存到列表中，对列表倒置

+ Python常用知识：

  append（）：向list中添加元素

  列表倒置的三种方法：(1)   reversed()函数

  ​                                    （2）使用sorted()函数：sorted(a,cmp=None, key=None, reverse=True) 

  ​                                             注意：其中reverse=True是按降序排列，reverse=False是按照升序排列

  ​                                    （3）使用分片：[::-1]代表从后向前取值，每次步进值为1

```python 
class Solution:
    # 返回从尾部到头部的列表值序列，例如[1,2,3]
    def printListFromTailToHead(self, listNode):
        # write code here
        result=[]
        p=listNode
        while(p):
             result.append(p.val)
             p=p.next
        return result[::-1]
```

#### 4.重建二叉树

**题目** ：输入某二叉树的前序遍历和中序遍历的结果，请重建出该二叉树。假设输入的前序遍历和中序遍历的结果中都不含重复的数字。例如输入前序遍历序列{1,2,4,7,3,5,6,8}和中序遍历序列{4,7,2,1,5,3,8,6}，则重建二叉树并返回。

**思路** ：

- Python常用知识：

  List的pop()：pop() 函数用于移除列表中的一个元素（默认最后一个元素），并且返回该元素的值。

  index()：index() 函数用于从列表中找出某个值第一个匹配项的索引位置。

  ```python
  # -*- coding:utf-8 -*-
  # class TreeNode:
  #     def __init__(self, x):
  #         self.val = x
  #         self.left = None
  #         self.right = None
  class Solution:
      # 返回构造的TreeNode根节点
      def reConstructBinaryTree(self, pre, tin):
          # write code here
          if pre==[] or tin==[]:        
          #if not pre or not tin:
              return None
          p=pre.pop(0)
          rootNode=TreeNode(p)
          loc=tin.index(p)
          rootNode.left=self.reConstructBinaryTree(pre,tin[:loc])
          rootNode.right=self.reConstructBinaryTree(pre,tin[loc+1:])
          return rootNode
  ```

  ​



​             

​         

