
整理一波最近的FB高频率 顺便求米。。<https://www.1point3acres.com/bbs/thread-469442-1-1.html>

1. Integer to English word
> https://leetcode.com/problems/in ... -easy-to-understand
2. findFirstBugCommit (binary search)
> https://leetcode.com/problems/first-bad-version/description/
```
二分法的变种,看一下正常的二分法,找第一个,找最后一个

https://leetcode.com/problems/fi ... -array/description/
```
3. binary string相加 (^ ^ ^)
> https://leetcode.com/problems/ad ... va-with-explanation
4. alien dictionary (Map<Character, Set<Character>> BFS)
```java
public String alienOrder(String[] words) {
    Map<Character, Set<Character>> map=new HashMap<Character, Set<Character>>();
    Map<Character, Integer> degree=new HashMap<Character, Integer>();
    String result="";
    if(words==null || words.length==0) return result;
    for(String s: words){
        for(char c: s.toCharArray()){
            degree.put(c,0);
        }
    }
    for(int i=0; i<words.length-1; i++){
        String cur=words;
        String next=words[i+1];
        int length=Math.min(cur.length(), next.length());
        for(int j=0; j<length; j++){
            char c1=cur.charAt(j);
            char c2=next.charAt(j);
            if(c1!=c2){
                Set<Character> set=new HashSet<Character>();
                if(map.containsKey(c1)) set=map.get(c1);
                if(!set.contains(c2)){
                    set.add(c2);
                    map.put(c1, set);
                    degree.put(c2, degree.get(c2)+1);
                }. From 1point 3acres bbs
                break;
            }
        }
    }
    Queue<Character> q=new LinkedList<Character>();
    for(char c: degree.keySet()){
        if(degree.get(c)==0) q.add(c);
    }
    while(!q.isEmpty()){
        char c=q.remove();
        result+=c;
        if(map.containsKey(c)){
            for(char c2: map.get(c)){
                degree.put(c2,degree.get(c2)-1);
                if(degree.get(c2)==0) q.add(c2);
            }
        }
    }
    if(result.length()!=degree.size()) return "";
    return result;
}
```
5. find k largest number in an array (quick select-怎么破? || 最小堆优先队列)
> https://www.jiuzhang.com/solutions/kth-largest-element/
```java
public int kthLargestElement(int k, int[] nums) {
        if(nums == null || nums.length == 0 || k < 1 || k > nums.length){
                return 0;
        }

        return partition(nums, 0, nums.length - 1, nums.length - k);
}

public int partition(int[] nums, int start, int end, int k){
        if(start >= end){//这个是啥意思
                return nums[k];. check 1point3acres for more.
        }
        int left = start, right = end;
        int pivot = nums[(start + end) / 2];
        while(left <= right){
                while(left <= right && nums[left] < pivot){
                        left++;
                }
                while(left <= right && nums[right] >= pivot){
                        right--;
                }
                if(left <= right){
                        swap(nums, left, right);
                        left++;
                        right--;
                }
        }
        // 循环退出后应该是right + 1 = left
        if (k <= right) { // K在左边,继续往左边划分
        return partition(nums, start, right, k);
    }
    if (k >= left) { // K在右边,右边继续划分
                return partition(nums, left, end, k);
        }
    return nums[k];//这行代码应该不会被执行吧?
}

public void swap(int[] nums, int left, int right){
        int temp = nums[left];
        nums[left] = nums[right];
        nums[right] = temp;
}
```
6. leetcode 91 Decode ways (dp)
7. leetcode 639 Decode ways||
8. Move Zeroes (two pointers)
9. leetcode 158 Read N Characters Given Read4 II - Call multiple times(k size char, read pointer, write pointer, size k)
10. clone graph
11. merge intervals
12. Longest Increasing Subsequence
13. Binary Tree Maximum Path Sum
14. Is Subsequence (index of)
15. Serialize and Deserialize Binary Tree
16. continuous subarray = k
17. get all permutations string
18. leetcode 346 moving avg
19. rectangle put string (binary search)
20. 103. Binary Tree Zigzag Level Order Traversal (two stack)
21. Continuous Subarray Sum(Hash Map)
22. 211. Add and Search Word - Data structure design(Trie Node)
23. maximum subarray(prefix sum / greedy)
24. maximum sum of 3 non overlapping subarrays
25. merge sorted array
26. Task Scheduler(变形)
27. invalid number
28. inorder traversal
29. Binary Search Tree Iterator
30. Insert Delete GetRandom O(1)
31. 438. Find All Anagrams in a String (Two pointers)
32. Pow(x, n)
33. divide two numbers(binary search << shift / recursion)
34. lowest common ancestor (Find path / divide and conquer)
35. 304. Range Sum Query 2D - Immutable
36. Minimum Window Substring
37. merge intervals(Intersection)
38. Serialize and Deserialize Binary Tree
39. valid palindrome (II greedy)
40. Binary Tree Paths
41. 127. Word Ladder
42 408. Valid Word Abbreviation
43. Meeting room
44. Binary Tree Vertical Order Traversal
45. vertical order(Map<Integer, List<Integer>>, Queue<Integer> qCol, Queue<Integer> queue)
46. single number (bit operation)
(https://leetcode.com/problems/si ... mber-Series-Summary)
47. Group Anagrams
48. 给一个只有0 和 1的矩阵 0在左边 1 在右边，要求最靠左的1的index，对每一行做二分查找就行
49. 226. Invert Binary Tree
50.  给一个字符串判断是不是数字，注意考虑负数和小数就行了
51. next permutation
52. 301. Remove Invalid Parentheses. From 1point 3acres bbs
53. add string
54. 稀疏向量
55. String permutation
56. 美式足球(dp)
57. custom sort string (O(n) count[26]). From 1point 3acres bbs
58. basic calculator. From 1point 3acres bbs
59. Longest Substring Without Repeating Characters
60. meeting rooms
61. 251 flattern 2D vector
62. (300)一个一维数组，输出连续增subarray的最长长度
fu1:允许跳过一个字母，输出连续增subarray最长长度
fu2:允许跳过k个字母，输出连续增subarray最长长
63. 输入是两个数组，一个是words 另一个是一个新定义的alphabet，return words是不是sorted order。
例如：words = ["cat", "ba", "baa"], alphabet是["c", "b", "a"]
64. 138. Copy List with Random Pointer
65. 找数组第三大元素 要欧N
66. 数组找任一peak元素 followup用二分法
67. income和pay tax的梯度. check 1point3acres for more.
68. leetcode 75 sort colors
69. 339. Nested List Weight Sum
70. k个最近坐标 （quick select / priority queue）
71. sort k array
72. 给一系列task和对应的dependencies
  （某个task能执行当且仅当所有dependencies都已经被执行），
   输出一个可能的task执行序列（拓扑排序）
73.339. Nested List Weight Sum
74 Best time to buy and sell stock (I II IIIdp)
75. 是给你一个功能， 获取好友,  可以返回这个user的所有好友。 
    要求你： 1 返回两个用户的共同好友。 
    2 让你实现一个推荐好友的功能。
   比如， 如果好友1 是 好友2 的好友， 好友2 是 好友3的好友，
   则好友3是好友1的推荐好友。要求返回好友1的所有推荐好友，
   并且把他们按照共同好友的数目来排序(HashMap, bucketsort)
76. 题目也不难，就是给一个字符串，
    中间是有 [name] 这样需要替换的key。-baidu 1point3acres
    有一个gettoken() API可以调用，
    比如gettoken('name')=Steve，
   要求返回替换了key以后的字符串。
   lz 问了一些clarification，说了一下思路，
   然后意识到一个edge case就是 [name[company]] 这样的 input
   怎么处理。(FInd all anagrams)
77. valid palindrome
78. 238. Product of Array Except Self
79. integer division
80. 迷宫题（左上到右下 / 全部路径 / 最短路径）
81. flatten binary tree to double linked list
82. insert interval
83. 413. Arithmetic Slices
84. 第一题 给一段html，查询其中一个节点，并且按要求print位置信息。.1point3acres网. From 1point 3acres bbs

比如说 <html>. 围观我们@1point 3 acres
              <body><node><node><body>
              <node><node>
          <html>
. 1point3acres. 1point3acres
查询node的话打印两条字符串，0:html->0:body->0:node和0:html->1:node

第二题给一串括号，用树的形式表示出来
85. Letter Combinations of a Phone Number    
86. 给两个没有duplicate element的sorted list, 找到公共元素
followup1: 如果有duplicate，只需要存一个. 1point3acres
followup2: 如果其中一个list特别长，没有duplicate
followup3: 如果其中一个list特别长，有duplicate，所有duplicate都要存下来-baidu 1point3acres
87.622. Design Circular Queue
88. 282. Expression Add Operators
89. post order
90.10. Regular Expression Matching
91. 题目是给一个binary tree，在tree上装camera，每一个camera能够监视到parent，自己和两个子节点。问最少安装多少个camera。
Resulttype(include root / without including root (minimum))
92. 新题是
class IOBuf {
  char[] data;
  int length;
  IOBuf next;
}
匹配俩个list的内容是否一样
比如list: [h,e] -> [l, l, o] -> null 和 [h,e,l] -> [l, o] -> null return true. check 1point3acres for more.
注意data可以为null, length可以为0：
[h,e] -> [l, l, o] -> [] -> [] -> null 和 [h,e,l] -> [l, o] -> null return true
93. Intersection of Two Arrays II
