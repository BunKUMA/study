Algorithm

1. 快速排序算法

   ![](img\quick_sort.png)

   ```python
   def partition(arr,left,r):
       pivot = arr[left]
       index = left
       for i in range(left+1,r+1):
           if arr[i] <= pivot:
               arr[index] = arr[i]
               index +=1
               arr[i] , arr[index] = arr[index] , pivot
       return index
   
   def quick_sort(arr, left, r):
       if left < r:
           index = partition(arr,left,r)
           quick_sort(arr,left,index-1)
           quick_sort(arr,index+1,r)
   
   quick_sort(arr, 0, len(arr)-1)   
   ```

   

2. 堆排序算法

3. 归并排序

4. 二分查找算法

5. BFPRT（线性查找算法）

6. DFS（深度优先搜索）

7. BFS（广度优先搜索）

8. Dijkstra算法

9. 动态规划算法

10. 朴素贝叶斯分类算法