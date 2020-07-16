# 2021秋招技术岗面试笔记
## 算法
### 排序算法
![复杂度分析](https://www.runoob.com/wp-content/uploads/2019/03/0B319B38-B70E-4118-B897-74EFA7E368F9.png)  
* 冒泡排序  
    > 无序区在前，有序区在后  
    > 对于长度为`n`的数组
    > 从无序区的第一位（`nums[0]`）开始，两两进行比较, 将较大/较小者不断后移至无序区末尾
      `nums[n-i]`, `i`为有序区的长度，即已经排序的次数（共需排序`n-1`次）    
    ![冒泡排序](https://www.runoob.com/wp-content/uploads/2019/03/bubbleSort.gif)
    ```java
        public int[] sortArray(int[] nums) {
                // 共排序n-1次
                for (int i=0; i<nums.length-1; i++) {
                    // 排序的标记
                    boolean flag = true;
                    // j+1的最大值为无序区的末尾 n-i, j的最大值是n-i-1
                    for (int j=0; j < nums.length - 1 - i; j++) {
                        // 两两交换
                        if (nums[j] > nums[j+1]) {
                            int temp = nums[j];
                            nums[j] = nums[j+1];
                            nums[j+1] = temp;
                            flag = false;
                        }
                    }
                    // 如果当前没有发生排序，证明排序已完成，提前终止
                    if (flag) break;
                }
                return nums;
      }
    ```
* 选择排序
    > 有序区在前，无序区在后
    > 对于长度为`n`的数组，遍历无序区（`nums[i]` ~ `nums[n-1]`), 将其中最大/最小元素放置在有序区的末尾之后（当前无序区的首位`nums[i]`)  
    ![选择排序](https://www.runoob.com/wp-content/uploads/2019/03/selectionSort.gif)
  ```java
      public int[] sortArray(int[] nums) {
              // 排序完成前，有序区的最大右边界为n-1(排除末尾元素)
              for (int i=0; i<nums.length-1; i++) {
                  // 当前最小元素的下标（开始为无序区的第一个元素）
                  int indexOfMin = i;
                  // 从无序区的第二个元素开始（i+1), 与当前最小元素进行比较，并记录下标
                  for (int j=i+1; j<nums.length; j++) {
                      if (nums[j] < nums[indexOfMin]) {
                          indexOfMin = j;
                      }
                  }
                  // 将当前无序区的最小元素移到最前
                  int temp = nums[i];
                  nums[i] = nums[indexOfMin];
                  nums[indexOfMin] = temp;
              }
              return nums;
      }
    ```
* 插入排序
    > 将第一待排序序列第一个元素看做一个有序序列，把第二个元素到最后一个元素当成是未排序序列。  
      从头到尾依次扫描未排序序列，将扫描到的每个元素插入有序序列的适当位置。（如果待插入的元素与有序序列中的某个元素相等，则将待插入元素插入到相等元素的后面。）
    > 有序区在前，无序区在后
    ![插入排序](https://www.runoob.com/wp-content/uploads/2019/03/insertionSort.gif)  
    ```java
    public int[] sortArray(int[] nums) {
            for (int i=1; i<nums.length; i++) {
                int j = i;
                // 无序区的首个元素
                int temp = nums[j];
                // 从有序区的末尾开始，不断前移直到找到比自己小的元素
                while (j > 0 && nums[j-1] > temp) {
                    // 所有大元素后移一位
                    nums[j] = nums[j-1];
                    j--;
                }
                // 插入当前位置
                nums[j] = temp;
            }
            return nums;
        }
    ```
 * 希尔排序
    >希尔排序是将待排序的数组元素 按下标的一定增量(gap)分组 ，分成多个子序列，然后对各个子序列进行直接插入排序算法排序；然后依次缩减增量再进行排序，直到增量为1时，进行最后一次直接插入排序，排序结束。  
    ![希尔排序](https://upload-images.jianshu.io/upload_images/6095354-ff984d80dbc0455f.png)
    ```java
   public int[] sortArray(int[] nums) {
           // 计算gap，从n/2到1
           for (int gap=nums.length/2; gap>0; gap /= 2) {
               // 针对每一种gap执行一次插入排序
               // 每次移动的距离由1变为gap
               for (int i=gap; i<nums.length; i+=gap) {
                   int j=i;
                   int temp = nums[j];
                   while (j > 0 && nums[j-gap] > temp) {
                       nums[j] = nums[j-gap];
                       j -= gap;
                   }
                   nums[j] = temp;
               }
           }
           return nums;
       }
    ```