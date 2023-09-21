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

   ## 基本思想

   (1)两分区从小到大合并

   (2)递归二分

   ### 两分区从小到大合并

   left, right, index的值会变, L,R,mid值不变

   有3种情况需要考虑: (1) 两半区都有数 (2)只有左半区有数 (3)只有右半区有数

   > 情况(2):当左半区拷贝完时, 右半区直接接上

   ```python
   def merge(arr, tmparr, L:int, mid:int, R:int):
       left = L        # 左半区第一个下标
       right = mid + 1 # 右半区第一个下标
       index = L       # 临时数组下标
       
       # 两半区都有数
       while left <= mid and right <= R :
           if arr[left] < arr[right]:
               tmparr[index] = arr[left]
               index += 1
               left += 1
           else :
               tmparr[index] = arr[right]
               index += 1
               right += 1
               
       # 只有左半区有数
       while left <= mid:
           tmparr[index] = arr[left]
           index += 1
           left += 1
           
       # 只有右半区有数
       while right <= R:
           tmparr[index] = arr[right]
           index += 1
           right += 1
       
       #排好序的tmp复制到arr
       while L <= R:
           arr[L] = tmparr[L]
           L += 1
   ```

   > 利用下标来判断分区是否为空

   ### 递归二分

   一边递归二分, 一边分到底再合并

   ```python
   def msort(arr, tmparr, L:int, R:int):
       if L < R:
           mid = int((L + R) / 2)
           msort(arr, tmparr, L, mid)
           msort(arr, tmparr, mid+1, R)
           merge(arr, tmparr, L , mid, R)
   ```

   ```python
   def merge_sort(arr, n:int):
       tmparr = [i for i in range(n)]
       msort(arr, tmparr, 0, n-1)
       
    merge_sort(arr,len(arr))
   ```

   > 视频参考: B站 BV1Pt4y197VZ

4. ## 二分查找算法

   前提:在一个有序数组中, 找到target, 返回坐标

   常见的四个问题:

   问题1 找到第一个>=target的元素

   问题2 找到最后一个<target的元素

   问题3 找到第一个>target的元素

   问题4 找到最后一个<=target的元素

   ## 基本思路

   (1) 考虑哪些数是左边区域, 哪些数是右边区域

   (2) 思考什么条件才能将数判定为左边区域

   (3)

   ### 问题1

   找到第一个>=target的元素

   ```python
   def is_left_area(arr, mid, target):
       # 第一个>= target
       if arr[mid] < target:
           return True
       else:
           return False
   
   def binarySearch(target, arr, n):
       left = -1
       right = n
       while left+1 != right:
           mid = int((left+right)/2)
           if is_left_area(arr, mid, target):
               left = mid
           else:
               right = mid
       return right
   ```

   > 如果不存在大于等于target的元素, 会返回n

5. ## BFPRT（线性查找算法）

6. ## DFS（深度优先搜索）

7. ## BFS（广度优先搜索）

8. ## Dijkstra算法

9. ## 动态规划算法

10. ## 朴素贝叶斯分类算法