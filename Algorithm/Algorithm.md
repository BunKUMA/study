# Algorithm

1. ## 快速排序算法

   ### 核心思想:

    小于指定元素的数放在左边, 大于的数放在右边

   ### 基本思路:

   (0)需要注意的变量  index:pivot的坐标, i:迭代器

   (1)选定pivot(我是选arr的第一个)

   (2)遍历, 跟pivot比大小

   (3)arr[i]如果小于pivot; arr[index], arr[index+1], arr[i] = arr[i], pivot, arr[index+1]

   (4)递归流程(1)(2)(3)

   ```python
   def partition(arr,left,r):
       pivot = arr[left]
       index = left
       for i in range(left+1,r+1):
           if arr[i] <= pivot:
               idx_next = index + 1
               arr[index] , arr[idx_next] , arr[i] = arr[i] ,  pivot , arr[idx_next]
               index = idx_next
       return index
   
   def quick_sort(arr, left, r):
       if left < r:
           index = partition(arr,left,r)
           quick_sort(arr,left,index-1)
           quick_sort(arr,index+1,r)
   
   quick_sort(arr, 0, len(arr)-1) 
   ```

2. ## 堆排序算法

   复杂度: O(NlogN)

   ## 基本思想:

   (1) 堆的性质维护

   (2) 创建堆

   (3) 排序

   ### 堆的性质维护

   以坐标0开始,子节点的数要小于父节点

   左子节点坐标:[当前节点坐标]*2+1

   右子节点坐标:[当前节点坐标]*2+2

   ```python
   def heapify(arr, n:int, i:int):
       """
           n:数组的大小
           i:当前节点的下标    
       """
       largest = i
       lson = i * 2 + 1
       rson = i * 2 + 2
       if lson < n and arr[largest] < arr[lson]:
           largest = lson
       if rson < n and arr[largest] < arr[rson]:
           largest = rson
       if largest != i:
           arr[i], arr[largest] = arr[largest], arr[i]
           heapify(arr, n , largest)
   ```

   ### 创建堆

   倒着遍历数组, 并维护堆性质

   父节点坐标:([当前节点坐标] - 1)  / 2

   ### 排序

   以大顶堆为例(arr[0]值最大),堆顶跟堆底对换, 排除堆底部, 再维护堆

   ```python
   def heapSort(arr, n):
       # 创建堆
       for i in reversed(range(n)):
           heapify(arr, n ,int((i-1)/2) )
   
       # 排序
       for i in reversed(range(n)):
           arr[0], arr[i] = arr[i], arr[0]
           heapify(arr, i ,0)
    
   heapSort(arr, len(arr))
   ```

   > 维护堆的性质(堆化)是从上往下, 创建堆和排序是从下往上

3. ## 归并排序

4. ## 二分查找算法

5. ## BFPRT（线性查找算法）

6. ## DFS（深度优先搜索）

7. ## BFS（广度优先搜索）

8. ## Dijkstra算法

9. ## 动态规划算法

10. ## 朴素贝叶斯分类算法