# 一些解题需要的语法知识

## Arrays.copyOfRange

一般会用在数组的一段选取中。

copyOfRange(original,int from,int to)该方法是从original数组的下标from开始赋值，到下标to结束，不包括下标为to的元素。

```java
import java.util.Arrays;

public class Solution {
	public static void main(String[] args) {
		int[] n=new int[]{1,2,3,4,5};//Java中数组初始化
		int[] m=Arrays.copyOfRange(n, 0, 3);
		for(int i=0;i<m.length;i++) {
			System.out.print(m[i]+" ");
		}
	}	
}
```

运行结果：1 2 3



## Array 数组排序

```java
int[] arr = {4,3,5,1,7,9,3};
Arrays.sort(arr);
Arrays.sort(arr,1,4);
```





## ArrayList类

可以动态修改的数组，与普通数组的区别就是它是没有固定大小的限制，我们可以添加或删除元素。

```java
import java.util.ArrayList; // 引入 ArrayList 类

ArrayList<E> objectName =new ArrayList<>();　 // 初始化
```



常用方法整理

| 方法                                                         | 描述                                          |
| :----------------------------------------------------------- | :-------------------------------------------- |
| [add()](https://www.runoob.com/java/java-arraylist-add.html) | 将元素插入到指定位置的 arraylist 中           |
| [contains()](https://www.runoob.com/java/java-arraylist-contains.html) | 判断元素是否在 arraylist                      |
| [get()](https://www.runoob.com/java/java-arraylist-get.html) | 通过索引值获取 arraylist 中的元素             |
| [indexOf()](https://www.runoob.com/java/java-arraylist-indexof.html) | 返回 arraylist 中元素的索引值                 |
| [remove()](https://www.runoob.com/java/java-arraylist-remove.html) | 删除 arraylist 里的单个元素                   |
| [size()](https://www.runoob.com/java/java-arraylist-size.html) | 返回 arraylist 里元素数量                     |
| [isEmpty()](https://www.runoob.com/java/java-arraylist-isempty.html) | 判断 arraylist 是否为空                       |
| [subList()](https://www.runoob.com/java/java-arraylist-sublist.html) | 截取部分 arraylist 的元素                     |
| [set()](https://www.runoob.com/java/java-arraylist-set.html) | 替换 arraylist 中指定索引的元素               |
| [sort()](https://www.runoob.com/java/java-arraylist-sort.html) | 对 arraylist 元素进行排序                     |
| [toArray()](https://www.runoob.com/java/java-arraylist-toarray.html) | 将 arraylist 转换为数组                       |
| [toString()](https://www.runoob.com/java/java-arraylist-tostring.html) | 将 arraylist 转换为字符串                     |
| [lastIndexOf()](https://www.runoob.com/java/java-arraylist-lastindexof.html) | 返回指定元素在 arraylist 中最后一次出现的位置 |
| [removeRange()](https://www.runoob.com/java/java-arraylist-removerange.html) | 删除 arraylist 中指定索引之间存在的元素       |
| [forEach()](https://www.runoob.com/java/java-arraylist-foreach.html) | 遍历 arraylist 中每一个元素并执行特定操作     |
| [clear()](https://www.runoob.com/java/java-arraylist-clear.html) | 删除 arraylist 中的所有元素                   |



这里稍微介绍一下add方法，foreach方法，其他方法的使用大同小异。



add方法可以实现在某个特定位置输入元素，原位置的元素向后移动。

```java
import java.util.ArrayList;

class Main {
    public static void main(String[] args) {
        // 创建一个数组
        ArrayList<String> sites = new ArrayList<>();

        // 在该数组末尾插入元素
        sites.add("Google");
        sites.add("Runoob");
        sites.add("Taobao");
        System.out.println("ArrayList: " + sites);

        // 在第一个位置插入元素
        sites.add(1, "Weibo");
        System.out.println("更新 ArrayList: " + sites);
    }
}
```

输出结果：

```
ArrayList: [Google, Runoob, Taobao]
更新 ArrayList: [Google, Weibo, Runoob, Taobao]
```



然后介绍foreach方法：

forEach() 方法用于遍历动态数组中每一个元素并执行特定操作。

```java
import java.util.ArrayList;

class Main {
    public static void main(String[] args) {
        // 创建一个数组
        ArrayList<Integer> numbers = new ArrayList<>();

        // 往数组中添加元素
        numbers.add(1);
        numbers.add(2);
        numbers.add(3);
        numbers.add(4);
        System.out.println("ArrayList: " + numbers);

        // 所有元素乘以 10
        System.out.print("更新 ArrayList: ");
       
        // 将 lambda 表达式传递给 forEach
        numbers.forEach((e) -> {
            e = e * 10;
            System.out.print(e + " ");
        });
    }
}
```

执行以上程序输出结果为：

```
ArrayList: [1, 2, 3, 4]
更新 ArrayList: 10 20 30 40 
```



# 边界条件的注意

写一个while循环查找二维数组中的值的时候，边界条件的设置，要带入最小或最大的边界进行测试

```
while(row<=array.length-1 && col>=0){
            if(array[row][col]<target){
                row++;
            }else if(array[row][col]>target){
                col--;
            }else{
                return true;
            }
        }
```



> 面对复杂问题要通过具体例子找到规律



# 双引号，单引号

Java中char是用' '单引号，字符串用" "包起来即可。



# 位运算判断奇偶

**`1`**的二进制 表示形式为 **`00000001`**

所以：任何整数 & 1

  结果为 1 ，则为奇数

  结果为 0 ，则为偶数



# 二维数组的长度

二维数组int array[][] = new int [ 2 ] [ 3 ]; 

有多少行：array.length = 2

有多少列：array[i].length = 3



记忆方法：本身规格为2*3，那么array.length = 2,   array[i].length = 3



# 将字符串转换为String类型数组

将每个字符分开

` String[] s1 = s.split("");`

按单词划分

`String[] s1 = s.split(" ");`



> 注意：如果写成`String s1[]`则会降低运行效率，但是也可以通过编译



>  合并两个字符串或者数组的时候，从后往前进行复制可以提高效率 



# Stack类

```java
import java.util.Stack;

public class func_test {
    public static void main(String[] args){
        Stack<Integer> stack_1 = new Stack<Integer>();
        stack_1.push(1);
        stack_1.push(2);

        System.out.println("peek " +stack_1.peek());

        stack_1.pop();
        System.out.println("peek "+ stack_1.peek());
        System.out.println("size "+stack_1.size());
    }
}

```



其他方法：

| 1    | boolean empty()  测试堆栈是否为空。                          |
| ---- | ------------------------------------------------------------ |
| 2    | Object peek( ) 查看堆栈顶部的对象，但不从堆栈中移除它。      |
| 3    | Object pop( ) 移除堆栈顶部的对象，并作为此函数的值返回该对象。 |
| 4    | Object push(Object element) 把项压入堆栈顶部。               |
| 5    | int search(Object element) 返回对象在堆栈中的位置，以 1 为基数。 |



# Queue类

```java
import java.util.LinkedList;
import java.util.Queue;
 
public class Main {
    public static void main(String[] args) {
        //add()和remove()方法在失败的时候会抛出异常(不推荐)
        Queue<String> queue = new LinkedList<String>();
        //添加元素
        queue.offer("a");
        queue.offer("b");
        queue.offer("c");
        queue.offer("d");
        queue.offer("e");
        for(String q : queue){
            System.out.println(q);
        }
        System.out.println("===");
        System.out.println("poll="+queue.poll()); //返回第一个元素，并在队列中删除	poll=a
        for(String q : queue){
            System.out.println(q);
        }
        System.out.println("===");
        System.out.println("element="+queue.element()); //返回第一个元素  element=b
        for(String q : queue){
            System.out.println(q);
        }
        System.out.println("===");
        System.out.println("peek="+queue.peek()); //返回第一个元素  element=b
        for(String q : queue){
            System.out.println(q);
        }
    }
}
```









# 整型转String转char[]

```java
//整型转string转char[]
int m;
String str = String.valueOf(m);
//或者  String str1 = m+"";
char[] c = str.toCharArray();

//char转string
char[] num_char = {'1','2','3'};
String num = String.valueOf(num_char);

//string转int
String num = "123";
int a = Integer.valueOf(num);
```



# HashMap

```java
// 引入 HashMap 类      
import java.util.HashMap;

public class RunoobTest {
    public static void main(String[] args) {
        // 创建 HashMap 对象 Sites
        HashMap<Integer, String> Sites = new HashMap<Integer, String>();
        // 添加键值对
        Sites.put(1, "Google");
				//访问元素
        System.out.println(Sites.get(1));
        //删除元素
        Sites.remove(4);
        //删除所有键值对
        Sites.clear();
        //计算大小
        System.out.println(Sites.size());
        //迭代,迭代顺序和put的顺序相同
        for (Integer i : Sites.keySet()) {
            System.out.println("key: " + i + " value: " + Sites.get(i));
        }
      
      	// key 的映射存在于 HashMap 中
        // Not Found - 如果 HashMap 中没有该 key，则返回默认值
      	String value1 = sites.getOrDefault(1, "Not Found");
      
        //包含功能
        if(sites.containsKey(1)) {
            System.out.println("key 为 1 存在于 sites 中");
        }
        if(sites.keySet().contains(1)) {
            System.out.println("key 为 1 存在于 sites 中");
        }	// 这么写效率更高一点
        if(sites.containsValue("Runoob")) {
            System.out.println("Runoob 存在于 sites 中");
        }
        if(sites.values().contains(1)) {
            System.out.println("key 为 1 存在于 sites 中");
        }
      	
      
    }
}
```



 # HashSet

HashSet 基于 HashMap 来实现的，是一个不允许有重复元素的集合。

HashSet 允许有 null 值。

HashSet 是无序的，即不会记录插入的顺序。

HashSet 不是线程安全的， 如果多个线程尝试同时修改 HashSet，则最终结果是不确定的。 您必须在多线程访问时显式同步对 HashSet 的并发访问。

```java
import java.util.HashSet;

public class RunoobTest {
    public static void main(String[] args) {
    HashSet<String> sites = new HashSet<String>();
        sites.add("Google");
        sites.add("Runoob");
        sites.add("Taobao");
        sites.add("Zhihu");
        sites.add("Runoob");  // 重复的元素不会被添加
      	System.out.println(sites.contains("Taobao")); // 判断元素是否在set内
	      sites.remove("Taobao");  // 删除元素，删除成功返回 true，否则为 false
	      System.out.println(sites.size()); // 计算大小
        for (String i : sites) {	// 迭代输出
            System.out.println(i);
        }
	      sites.clear(); // 删除全部元素
    }
}
```







# StringBuilder

```java
public class RunoobTest{
    public static void main(String args[]){
        StringBuilder sb = new StringBuilder(10);
        sb.append("Runoob..");
        System.out.println(sb);  
        sb.append("!");
        System.out.println(sb); 
        sb.insert(8, "Java");
        System.out.println(sb); 
        sb.delete(5,8);
        System.out.println(sb);  
    }
}
```



```
Runoob..
Runoob..!
Runoob..Java!
RunooJava!
```

| 13   | String substring(int start) 返回一个新的 `String`，它包含此字符序列当前所包含的字符子序列。 |
| ---- | ------------------------------------------------------------ |
| 14   | String substring(int start, int end) 返回一个新的 `String`，它包含此序列当前所包含的字符子序列。 |
| 15   | String toString() 返回此序列中数据的字符串表示形式。         |

| 7    | int lastIndexOf(String str) 返回最右边出现的指定子字符串在此字符串中的索引。 |
| ---- | ------------------------------------------------------------ |
| 8    | int lastIndexOf(String str, int fromIndex) 返回 String 对象中子字符串最后出现的位置。 |
| 9    | int length()  返回长度（字符数）。                           |
| 10   | void setCharAt(int index, char ch) 将给定索引处的字符设置为 `ch`。 |



与string相互转换

```java
// sb to string			
StringBuilder sb = new StringBuilder();
sb.append("abc").append("efg");
String s = sb.toString();
 
// string to sb
String s = "hello";
StringBuilder sb = new StringBuilder(s);
```







# 数组转化list集合

```java
List<String> list = Arrays.asList("a","b","c");
```



# 二维数组排序

```java
// return a[1]-b[1]表示按照每个数组中的第二个元素顺序排序
// return b[0]-a[0]表示按照每个数组中的第一个元素逆序排序

int[][] nums=new int[][]{{1,3},{1,2},{4,5},{3,7}};

        Arrays.sort(nums,(a,b)->{
            if(a[0] == b[0]){
                return a[1]-b[1];
            }
            return b[0]-a[0];
        });
```



# 通过二维ArrayList得到二维数组

```java
List<int[]> result = new ArrayList<>(); // create

int[] newInterval = {1,2};	
result.add(newInterval);	// append

return result.toArray(new int[result.size()][]); // 
```







# JZ3 从尾到头打印链表

输入一个链表，按链表从尾到头的顺序返回一个ArrayList。



## 方法1 反转链表

设置一个新的链表头，反转链表，并将新的链表顺序输出

```java
/**
*    public class ListNode {
*        int val;
*        ListNode next = null;
*
*        ListNode(int val) {
*            this.val = val;
*        }
*    }
*
*/
import java.util.ArrayList;
public class Solution {
    public ArrayList<Integer> printListFromTailToHead(ListNode listNode) {
      //首先解决空指针输入和仅仅两个元素输入的情况
        if(listNode == null){
            ArrayList<Integer> out_null = new ArrayList<>();
            return out_null;
        }
        if(listNode.next.next == null){
            ArrayList<Integer> out_2element = new ArrayList<>();
            out_2element.add(0,listNode.next.val);
            out_2element.add(1,listNode.val);
        }
        
      
        ListNode head = listNode;
        //反转链表，以revertHead作为开头
        ListNode cur = head;
        ListNode revertHead = new ListNode(0);
        ListNode next = null;
        while(cur!=null){
            next = cur.next;
            cur.next = revertHead.next;
            revertHead.next = cur;
            cur = next;
        }

        //准备遍历输出
        ArrayList<Integer> out = new ArrayList<>();
        ListNode temp = revertHead;
        while(true){
            out.add(temp.next.val);
            temp = temp.next;
            if(temp.next == null){break;}
        }
        return out;

    }
}
```

## 方法2 使用add（0，val）

ArrayList 中有个方法是 add(index,value)，可以指定 index 位置插入 value 值

使用这种方法会导致每有一个数据需要输出，add方法就会将新的数据插入0的位置，后面的所有元素后移，整体复杂度和方法一相同，但是实际运行速度不如1。

```java
/**
*    public class ListNode {
*        int val;
*        ListNode next = null;
*
*        ListNode(int val) {
*            this.val = val;
*        }
*    }
*
*/

import java.util.*;
public class Solution {
    public ArrayList<Integer> printListFromTailToHead(ListNode listNode) {
        ArrayList<Integer> list = new ArrayList<>();
        ListNode tmp = listNode;
        while(tmp!=null){
            list.add(0,tmp.val);
            tmp = tmp.next;
        }
        return list;
    }
}
```

## 方法3 递归

使用递归的方法，利用系统的栈实现倒序打印

```java
import java.util.*;
public class Solution {
    ArrayList<Integer> list = new ArrayList();
    public ArrayList<Integer> printListFromTailToHead(ListNode listNode) {
        if(listNode!=null){
            printListFromTailToHead(listNode.next);
            list.add(listNode.val);
        }
        return list;
    }
}
```





# JZ4 重建二叉树

输入某二叉树的前序遍历和中序遍历的结果，请重建出该二叉树。假设输入的前序遍历和中序遍历的结果中都不含重复的数字。例如输入前序遍历序列{1,2,4,7,3,5,6,8}和中序遍历序列{4,7,2,1,5,3,8,6}，则重建二叉树并返回。



## 方法1 递归

```java
/**
 * Definition for binary tree
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
import java.util.Arrays;
public class Solution {
    public TreeNode reConstructBinaryTree(int [] pre,int [] in) {
        if (pre.length == 0){
            return null;
        }
        TreeNode root = new TreeNode(0);
        root.val = pre[0];
        
        //遍历查重root在中序遍历列表中的位置
         for (int i = 0; i < in.length; i++) {
         if (in[i] == pre[0]) {
             root.left = reConstructBinaryTree(Arrays.copyOfRange(pre,1,i+1),Arrays.copyOfRange(in,0,i));
             root.right = reConstructBinaryTree(Arrays.copyOfRange(pre,i+1,pre.length),Arrays.copyOfRange(in,i+1,in.length));
             }
         }
        
        return root;
    }
}
```





## 补充3种遍历方法

前序遍历，中序遍历，后序遍历递归方法

这里进行补充

```java
//前序遍历
public void preorderTraversal(){
    System.out.println(this);
    if(left!=null){
        this.left.preorderTraversal();
    }
    if(right!=null){
        this.right.preorderTraversal();
    }
}

//中序遍历
public void inorderTraversal(){
    if(left!=null){
        this.left.inorderTraversal();
    }
    System.out.println(this);
    if(right!=null){
        this.right.inorderTraversal();
    }
}

//后序遍历
public void postorderTraversal(){

    if(left!=null){
        this.left.postorderTraversal();
    }
    if(right!=null){
        this.right.postorderTraversal();
    }
    System.out.println(this);
}
```





# JZ4 用两个栈实现队列

用两个栈来实现一个队列，完成队列的Push和Pop操作。 队列中的元素为int类型。

## 方法1

第一个栈作为正常push的保存栈，第二个栈作为每次pop操作时的保存栈。

push时：直接push到第一个栈中

pop时：如果第二个栈非空，直接pop第二个栈的内容

​			   如果第二个栈为空，将第一个栈的内容全部压入第二个栈中，再pop第二个栈的内容



```java
import java.util.Stack;

public class Solution {
    Stack<Integer> stack1 = new Stack<Integer>();
    Stack<Integer> stack2 = new Stack<Integer>();
    
    public void push(int node) {
        stack1.push(node);
    }
    
    public int pop() {
        if(stack2.empty()){
        while(true){
            if(stack1.empty()){
                break;
            }
            stack2.push(stack1.pop());
        }
        return stack2.pop();
        }else{
            return stack2.pop();
        }
    }
}
```



另外，使用两个列表实现栈的功能也是可以实现

思路：

入栈：检查两个列表哪个为空，将元素加入不为空的列表

出栈：将size-1个元素都放入另一个栈中，然后将当前栈置空

```java
import java.util.*;

//使用两个列表实现栈的功能
public class List_stack_7 {
    public static void main(String[] args){
        Stack_by2List stack = new Stack_by2List();
        stack.list1.add(1);
        stack.list1.add(2);
        stack.list1.add(3);
        stack.pop();
        stack.push(4);
        stack.pop() ;
        stack.push(5);
        stack.show();
    }
}

class Stack_by2List{
    ArrayList<Integer> list1 = new ArrayList<Integer>();
    ArrayList<Integer> list2 = new ArrayList<Integer>();
    public void push(int node) {
        if(list1.isEmpty()){
            list2.add(node);
        }else{
            list1.add(node);
        }
    }

    public void pop() {
        if(list1.isEmpty()){
            int size = list2.size();
            int i = 0;
            while(true){
                if (i==size-1){
                    break;
                }
                list1.add(list2.get(i));
                i++;
            }
            list2.clear();
        }else{
            int size = list1.size();
            int j = 0;
            while(true){
                if (j==size-1){
                    break;
                }
                list2.add(list1.get(j));
                j++;
            }
            list1.clear();
        }
    }

    public void show(){
        System.out.println("list1:");
        list1.forEach((e)->{
            System.out.println(e);
        });
        System.out.println("list2:");
        list2.forEach((e)->{
            System.out.println(e);
        });
    }
}

```





# JZ6 旋转数组的最小数字

有一个长度为N的升序数组，比如[1,2,3,4,5]，将它进行旋转，即把一个数组最开始的若干个元素搬到数组的末尾，变成一个旋转数组，比如变成了[3,4,5,1,2]，或者[4,5,1,2,3]这样的。请问，给定这样一个旋转数组，求它的最小值。



使用二分查找递归的方法求解

首先需要判断是不是一个顺序序列，如果是，直接返回；然后判断是否left = right，如果是的话直接返回

然后用二分查找，如果mid>第一个数，说明最小值肯定在（mid+1,right）中；如果mid<第一个数，说明最小值肯定在（0,mid）中；如果第一个数和mid相等，那么只能使用顺序查找的方法

```java
import java.util.ArrayList;
public class Solution {
    public int minNumberInRotateArray(int [] array) {
        int left = 0;
        int right = array.length-1;
        return cal(array,left,right);
        
        
    }
    
    public int cal(int[] array, int left, int right){
        //顺序排列
        if(array[left]<array[right]){
            return array[left];
        }
        
        //当只有一个元素的时候
        if(left == right){
            return array[left];
        }
        
        int mid = (left+right)/2;
        if(array[mid]>array[0]){
            return cal(array,mid+1,right);
        }else if(array[mid]<array[0]){
            return cal(array,0,mid);
        }else{
            int min = 9999;
            for(int i = 0; i<array.length;i++){
                if(min>array[i]){
                    min = array[i];
                }
            }
            return min;
        }
    }
}
```



# JZ7-8,10斐波那契数列问题

都是斐波那契数列问题，f(n)=f(n-1)+f(n-2)的问题，如果使用递归的方法，会出现很多重复计算，所以使用for循环的方法，保存每次的计算结果以提高计算效率



代码：

jz7

```java
public class Solution {
    public int Fibonacci(int n) {
//         int fi0 = 0;
//         int fi1 = 1;
//         if(n == 0){return fi0;}
//         if(n == 1){return fi1;}
        
//         int fi_tmp1 = 0;
//         int fi_tmp2 = 1;
//         int res = 0;
//         for(int i = 2; i<=n;i++){
//             res = fi_tmp2+fi_tmp1;
//             fi_tmp1 = fi_tmp2;
//             fi_tmp2 = res;
//         }
//         return res;
        
        int fi0 = 0;
        int fi1 = 1;
        if(n == 0){return fi0;}
        if(n == 1){return fi1;}
        
        int res = Fibonacci(n-1)+Fibonacci(n-2);
        return res;
    }
}
```



Jz8

```java
public class Solution {
    public int jumpFloor(int target) {
                int fi0 = 1;
        int fi1 = 2;
        if(target == 1){return fi0;}
        if(target == 2){return fi1;}
        
        int fi_tmp1 = 1;
        int fi_tmp2 = 2;
        int res = 0;
        for(int i = 3; i<=target;i++){
            res = fi_tmp2+fi_tmp1;
            fi_tmp1 = fi_tmp2;
            fi_tmp2 = res;
        }
        return res;
    }
}
```



jz10

```java
public class Solution {
    public int rectCover(int target) {
        if(target == 0){return 0;}
        if(target == 1){return 1;}
        if(target == 2){return 2;}
        
        int fi1 = 1;
        int fi2 = 2;
        int res = 0;
        for(int i = 3;i<=target;i++){
            res = fi1+fi2;
            fi1 = fi2;
            fi2 = res;
        }
        
        return res;
    }
}
```



# JZ9 跳台阶拓展问题

一只青蛙一次可以跳上1级台阶，也可以跳上2级……它也可以跳上n级。求该青蛙跳上一个n级的台阶(n为正整数)总共有多少种跳法。

分析问题就会发现实际上就是f(n) = f(n-1) + f(n-2) +....+f(0)这个问题，正常使用递归可以解决

```java
public class Solution {
    public int jumpFloorII(int target) {
        if(target <= 1 ){return 1;}
        
        int res = 0;
        for (int i = 1;i<=target;i++){
            res += jumpFloorII(target-i);
        }
        return res;
    }
}
```



但是这样是时间复杂度O(n^2)，可以选择使用一个数组来记录已经计算过的值，将时间复杂度降低到O(n)

```java
public class Solution {
    
    int data[] = new int[10001];
    public int jumpFloorII(int target) {
        if(target <= 1 ){return 1;}
        if(data[target]!=0){
            return data[target];
        }
        
        for (int i = 0;i<target;i++){
            data[target]+=jumpFloorII(i);
        }
        return data[target];
    }
}

```



# JZ 11二进制中1的个数

输入一个整数，输出该数32位二进制表示中1的个数。其中负数用补码表示。

这里需要注意一下，逐位判断需循环 logn 次，所以逐位判断的时间复杂度位O(logn)



这里的思路1是将这个数右移一位，然后与1进行与运算，如果结果是1那么结果++

```java
public class Solution {
    public int NumberOf1(int n) {
        int ans = 0;
        while(n!=0){
            if((n&1)==1){
                ans++;
            }
            n = n>>>1;
        }
        return ans;
    }
}
```





# JZ 12 数值的整数次方

给定一个double类型的浮点数base和int类型的整数exponent。求base的exponent次方。

保证base和exponent不同时为0。不得使用库函数，同时不需要考虑大数问题，也不用考虑小数点后面0的位数。



解题主要需要考虑的是如果输入的次方是0或者负数，要怎么处理，不能仅仅考虑正整数情况

```java
public class Solution {
    public double Power(double base, int exponent) {
        if(exponent == 0){return 1;}
        if(exponent == 1){return base;}
        
        double res = 1;
        if(exponent > 0){
            for(int i = 1; i<=exponent; i++){
                res = res * base;
            }
        }else{
            for(int i = 1; i<=(exponent/-1); i++){
                res = res *(1/base);
            }
        }
        
        return res;
  }
}
```



# 打印1到最大的n位数

输入数字n，按顺序打印出从1最大的n位十进制数。比如输入3，则打印出1、2、3一直到最大的3位数即999。



https://www.cnblogs.com/yongh/p/9667104.html



# O(1)复杂度删除链表中的值

思路：将要删除节点的后一个节点的值赋给当前节点，然后用当前节点指向下一个节点的下一个节点；然后如果是最后一个节点的话，只能遍历查找



```java
package Sword_Offer;

public class O1deleteNode {
    public static void main(String[] args) {
        Node_delete node1 = new Node_delete(1);
        Node_delete node2 = new Node_delete(2);
        Node_delete node3 = new Node_delete(3);
        Node_delete node4 = new Node_delete(4);
        Node_delete node5 = new Node_delete(5);


        LinkedList_delete list = new LinkedList_delete();
        list.add(node1);
        list.add(node2);
        list.add(node3);
        list.add(node4);
        list.add(node5);

        list.show();

        System.out.println("----------------");
        list.delete(node2);
        list.delete(node5);
        list.show();
    }
}

class Node_delete{
    int val;
    Node_delete next;
    Node_delete(int val){
        this.val = val;
    }
    Node_delete(int val, Node_delete node){
        this.val = val;
        next = node;
    }

    @Override
    public String toString(){
        return "my value is "+val;
    }
}

class LinkedList_delete {
    Node_delete head = new Node_delete(0);

    //加入一个元素
    public void add(Node_delete nodeIn) {
        Node_delete temp = head;
        while (true) {
            if (temp.next == null) {
                break;
            }
            temp = temp.next;
        }
        temp.next = nodeIn;
    }

    public void delete(Node_delete node){
        //判断是否是最后一个
        if(node.next == null){
            Node_delete tmp = head;
            while(true){
                if(tmp.next.next == null)    break;
                tmp = tmp.next;
            }
            tmp.next = tmp.next.next;
            return;
        }
        
        //将当前节点的下一个节点数值复制给当前节点，然后删除当前节点后面的节点
        node.val = node.next.val;
        node.next = node.next.next;
    }

    //打印所有元素
    public void show() {
        if (head.next == null) {
            System.out.println("列表为空，输出个犊子");
        } else {
            Node_delete temp = head.next;
            while (true) {
                if (temp == null) {
                    break;
                }
                System.out.println(temp);
                temp = temp.next;
            }
        }
    }
}
```





# JZ13调整数组顺序使奇数位于偶数前面

输入一个整数数组，实现一个函数来调整该数组中数字的顺序，使得所有的奇数位于数组的前半部分，所有的偶数位于数组的后半部分，并保证奇数和奇数，偶数和偶数之间的相对位置不变。

```java
import java.util.*;


public class Solution {
    /**
     * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
     *
     * 
     * @param array int整型一维数组 
     * @return int整型一维数组
     */
    public int[] reOrderArray (int[] array) {
        // write code here
        ArrayList<Integer> even = new ArrayList<Integer>();
        ArrayList<Integer> odd = new ArrayList<Integer>();
        int m = 0;
        int j = 0;

        for(int i = 0;i<array.length; i++){
            if((array[i] & 1) == 0){
                even.add(array[i]);
                j++;
               
            }else{
                odd.add(array[i]);
                m++;
            }
            
        }
        int[] res = new int[array.length];
        int count = 0;
        for(int a = 0;a<odd.size();a++){
            res[count] = odd.get(a);
            count++;
        }
        for(int a = 0;a<even.size();a++){
            res[count] = even.get(a);
            count++;
        }
        return res;
    }
}
```





# **JZ14** **链表中倒数最后k个结点**

输入一个链表，输出一个链表，该输出链表包含原链表中从倒数第k个结点至尾节点的全部节点。

如果该链表长度小于k，请返回一个长度为 0 的链表。



主要思路就是使用两个指针，等第一个指针走过了k个节点之后第二个指针再开始走，这样第一个指针到达末尾时第二个指针的位置就是我们的目标位置

```java
import java.util.*;

/*
 * public class ListNode {
 *   int val;
 *   ListNode next = null;
 *   public ListNode(int val) {
 *     this.val = val;
 *   }
 * }
 */

public class Solution {
    /**
     * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
     *
     * 
     * @param pHead ListNode类 
     * @param k int整型 
     * @return ListNode类
     */
    public ListNode FindKthToTail (ListNode pHead, int k) {
        // write code here
        
        if(pHead == null || k <= 0){return null;}

        
        ListNode tmp1 = pHead;
        ListNode tmp2 = pHead;
        int count = 0;
        int flag = 0;
        
        while(tmp1.next != null){
            tmp1 = tmp1.next;
            count++;    //记录tmp1指针的位置
            if(count>=k){
                flag++;
                tmp2 = tmp2.next;
            }
        }
        if(count == k-1){return pHead;}
        if(flag == 0){return null;}

        return tmp2;
    }
}
```



# JZ15 反转链表

输入一个链表，反转链表后，输出新链表的表头。

思路就是创建一个新的链表头，然后使用两个指针cur和next指向原head的第一个和第二个节点。然后进行遍历插入操作，将需要插入的节点.next设置为新表头.next，然后新表头.next设置为当前需要插入的节点

```java
/*
public class ListNode {
    int val;
    ListNode next = null;

    ListNode(int val) {
        this.val = val;
    }
}*/
public class Solution {
    public ListNode ReverseList(ListNode head) {
        //特殊输入处理
        if(head == null){
            return null;
        }else if(head.next == null){
            return head;
        }
        
        ListNode newHead = new ListNode(0);
        ListNode cur = head;
        ListNode next;
        while(cur!=null){
            next = cur.next;
            cur.next = newHead.next;
            newHead.next = cur;
            cur = next;
        }
        return newHead.next;
    }
}
```



# JZ16 合并两个排序的链表

输入两个单调递增的链表，输出两个链表合成后的链表，当然我们需要合成后的链表满足单调不减规则。



首先排除输入的链表存在空的情况，然后创建一个新的链表头，进行list1和list2的大小对比，小的放在链表头后面，循环即可。

等其中一个list为空的时候直接将不为空的list放在目标链表后面即可

```java
public class Solution {
    public ListNode Merge(ListNode list1,ListNode list2) {
        if(list1 == null && list2 == null){
            return null;
        }else if(list1 == null && list2!=null){
            return list2;
        }else if(list1!=null && list2 == null){
            return list1;
        }
        
        ListNode newHead = new ListNode(0);
        ListNode cur = newHead;
        while(list1 != null && list2 != null){
            if(list1.val>list2.val){
                    cur.next = list2;
                    list2 = list2.next;
                }else{
                    cur.next = list1;
                    list1 = list1.next;
                }
            cur = cur.next;
        }
        
            if(list1 == null){
                cur.next = list2;
            }else if(list2 == null){
                cur.next = list1;
            }

        return newHead.next;
    }
}
```



# **JZ17** 树的子结构

输入两棵二叉树A，B，判断B是不是A的子结构。（ps：我们约定空树不是任意一个树的子结构）



主要是递归的思路，先写一个函数来判断当前输入的两个节点是否相等，这个函数只在node2为空（也就是node2整个都查完了）的时候才会为true，如果node1和node2不相等，以及node1为空了，都反回false

然后是主函数，首先root1和root2任何一个为空都返回false，然后如果当前节点相等，或者root1的左右子节点有任何一个与root2相等，都返回true

更加清晰的讲解：https://blog.csdn.net/qq_28081081/article/details/80777587

```java
/**
public class TreeNode {
    int val = 0;
    TreeNode left = null;
    TreeNode right = null;

    public TreeNode(int val) {
        this.val = val;

    }

}
*/
public class Solution {
    public boolean HasSubtree(TreeNode root1,TreeNode root2) {
        if(root1 == null || root2 == null){
            return false;
        }
        return isSame(root1,root2) || HasSubtree(root1.left,root2) || HasSubtree(root1.right,root2);
    }
    
    public boolean isSame(TreeNode node1, TreeNode node2){
        if(node2 == null){return true;}
        if(node1 == null){return false;}
        if(node1.val != node2.val){
            return false;
        }
        return isSame(node1.left,node2.left) && isSame(node1.right,node2.right);
    }
}
```



# **JZ18** 二叉树的镜像

操作给定的二叉树，将其变换为源二叉树的镜像。



思路就是前序遍历，只不过每次遍历的时候交换左右两个子节点，但是要注意空指针的特殊输入问题



```java
import java.util.*;

/*
 * public class TreeNode {
 *   int val = 0;
 *   TreeNode left = null;
 *   TreeNode right = null;
 *   public TreeNode(int val) {
 *     this.val = val;
 *   }
 * }
 */

public class Solution {
    /**
     * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
     *
     * 
     * @param pRoot TreeNode类 
     * @return TreeNode类
     */
    public TreeNode Mirror (TreeNode pRoot) {
        if(pRoot == null){
            return pRoot;
        }
        
        //前序遍历+反转
        TreeNode cur = new TreeNode(1);
        cur.left = pRoot.left;
        pRoot.left = pRoot.right;
        pRoot.right = cur.left;
        
        if(pRoot.left != null){
            Mirror(pRoot.left);
        }
        if(pRoot.right != null){
            Mirror(pRoot.right);
        }
        return pRoot;
    }
}
```





# JZ19 顺时针打印矩阵

输入一个矩阵，按照从外向里以顺时针的顺序依次打印出每一个数字，例如，如果输入如下4 X 4矩阵：

```
[[1,2,3,4],
[5,6,7,8],
[9,10,11,12],
[13,14,15,16]]
```

则依次打印出数字

```
[1,2,3,4,8,12,16,15,14,13,9,5,6,7,11,10]
```



主要思路就是设计四个边界，因为每次遍历完当前行或列的时候这一行或列以后就再也不会使用了，用这个思路去遍历就可以了

1. 向右走存入整行的值，当存入后，该行再也不会被遍历，代表上边界的 up 加一，同时判断是否和代表下边界的 down 交错
2. 向下走存入整列的值，当存入后，该列再也不会被遍历，代表右边界的 right 减一，同时判断是否和代表左边界的 left 交错
3. 向左走存入整行的值，当存入后，该行再也不会被遍历，代表下边界的 down 减一，同时判断是否和代表上边界的 up 交错
4. 向上走存入整列的值，当存入后，该列再也不会被遍历，代表左边界的 left 加一，同时判断是否和代表右边界的 right 交错



代码

```java
import java.util.ArrayList;
class Solution {
    public ArrayList<Integer> printMatrix(int [][] matrix) {

        ArrayList<Integer> res = new ArrayList<Integer>();
        if (matrix == null){return res;}

        int left = 0;
        int up = 0;
        int right = matrix[0].length-1;
        int down = matrix.length-1;

        while(true){
            for(int col = left;col<=right;col++){
                res.add(matrix[up][col]);
            }
            up++;
            if(up>down){
                break;
            }

            for(int row = up;row<=down;row++){
                res.add(matrix[row][right]);
            }
            right--;
            if(right<left){
                break;
            }

            for(int col = right;col>=left;col--){
                res.add(matrix[down][col]);
            }
            down--;
            if(down<up){
                break;
            }

            for(int row = down;row>=up;row--){
                res.add(matrix[row][left]);
            }
            left++;
            if(left>right){
                break;
            }
        }
        return res;


    }
}
```



# JZ20 包含min函数的栈

定义栈的数据结构，请在该类型中实现一个能够得到栈中所含最小元素的min函数，并且调用 min函数、push函数 及 pop函数 的时间复杂度都是 O(1)

push(value):将value压入栈中

pop():弹出栈顶元素

top():获取栈顶元素

min():获取栈中最小元素



具体思路就是设计两个栈，一个栈正常存储，另一个栈存储当前最小的元素

```java
import java.util.Stack;

public class Solution {

    private Stack<Integer> s1 = new Stack();
    private Stack<Integer> s1_help = new Stack();
    public void push(int node) {
        s1.push(node);
        
        if(s1_help.empty() == true){
            s1_help.push(node);
        }else{
            s1_help.push(Math.min(s1_help.peek(), node));
        }
    }
    
    public void pop() {
        s1.pop();
        s1_help.pop();
    }
    
    public int top() {
        return s1.peek();
    }
    
    public int min() {
        return s1_help.peek();
    }
}
```





# **JZ21** 栈的压入、弹出序列

输入两个整数序列，第一个序列表示栈的压入顺序，请判断第二个序列是否可能为该栈的弹出顺序。假设压入栈的所有数字均不相等。例如序列1,2,3,4,5是某栈的压入顺序，序列4,5,3,2,1是该压栈序列对应的一个弹出序列，但4,3,5,1,2就不可能是该压栈序列的弹出序列。（注意：这两个序列的长度是相等的）



两种思路都可以解决这个问题，一种思路循环出序列，一种思路循环压入序列



首先是循环出序列：主循环是一个for循环，循环判断每个出栈数据是否满足条件；然后利用while循环进行push的叠加，满足push列表遍历完成或可以pop的条件的时候break出while循环

```java
import java.util.Stack;

public class Solution {
    public boolean IsPopOrder(int [] pushA,int [] popA) {
        int index = 0;
        Stack<Integer> s = new Stack<Integer>();
        
        for(int i : popA){
            while(true){
                if(s.empty() == false && s.peek() == i){
                    s.pop();
                    break;
                    
                }else{
                    if(index>=pushA.length){
                        break;
                    }else{
                        s.push(pushA[index]);
                        index++;
                    }
                }
            }
        }
        
        if(s.empty() == true){
            return true;
        }else{
            return false;
        }
    }
}
```



然后是以压入数组为遍历对象的解法：每次循环都压入一个数字，然后循环判断当前栈顶与pop数组中的值是否相等，如果满足的话pop出栈顶的数字然后将p值++，最后判断p是否与出栈数组的长度相等即可

```java
import java.util.Stack;
 
public class Solution {
    public boolean IsPopOrder(int[] pushA, int[] popA) {
        Stack<Integer> stack = new Stack<>();
        int p = 0;
        for (int i = 0; i < pushA.length; i++) {
            stack.push(pushA[i]);
 
            while (!stack.empty() && stack.peek() == popA[p]) {
                stack.pop();
                p++;
            }
        }
 
        return p == popA.length;
    }
}
```



# **JZ22** 从上往下打印二叉树

从上往下打印出二叉树的每个节点，同层节点从左至右打印。



思路：设计一个队列存储之后要输出的点，首先将root放入队列，在队列非空的情况下，将当前队列中第一个值的左右子节点分别放入队列末尾，然后继续遍历队列中的值，直到全部遍历完毕

```java
import java.util.ArrayList;
/**
public class TreeNode {
    int val = 0;
    TreeNode left = null;
    TreeNode right = null;

    public TreeNode(int val) {
        this.val = val;

    }

}
*/
public class Solution {
    public ArrayList<Integer> PrintFromTopToBottom(TreeNode root) {
        ArrayList<TreeNode> queue = new ArrayList<TreeNode>();
        ArrayList<Integer> list = new ArrayList<Integer>();        
        
        if(root == null){
            return list;
        }
        queue.add(root);
        while(queue.size()!=0){
            TreeNode tmp = new TreeNode(0);
            tmp = queue.remove(0);
            list.add(tmp.val);
            
            if(tmp.left != null){
                queue.add(tmp.left);
            }
            if(tmp.right != null){
                queue.add(tmp.right);
            }
             
        }
        
        return list;
    }
}
```



# JZ23二叉搜索树的后序遍历序列

输入一个整数数组，判断该数组是不是某二叉搜索树的后序遍历的结果。如果是则返回true,否则返回false。假设输入的数组的任意两个数字都互不相同。（ps：我们约定空树不是二叉搜索树）

> 二叉查找树（Binary Search Tree），（又：二叉搜索树，二叉排序树）它或者是一棵空树，或者是具有下列性质的[二叉树](https://baike.baidu.com/item/二叉树/1602879)： 若它的左子树不空，则左子树上所有结点的值均小于它的[根结点](https://baike.baidu.com/item/根结点/9795570)的值； 若它的右子树不空，则右子树上所有结点的值均大于它的根结点的值





首先是递归的方法：先找到左子树右子树的分界点，然后递归，查看每个子树是否符合二叉查找树的定义

```java
import java.util.*;

class Solution {
    public boolean VerifySquenceOfBST(int [] sequence) {
        int index = sequence.length-1;
        if(index < 0){return false;}
        if(index == 0){return true;}

        ArrayList<Integer> left = new ArrayList<Integer>();
        ArrayList<Integer> right = new ArrayList<Integer>();

        int root_val = sequence[index];
        if(sequence[0]<root_val){
            left.add(sequence[0]);
        }else{
            right.add(sequence[0]);
        }
        for(int i = 1;i < index; i++){
            if(sequence[i]<root_val){
                if(right.size() != 0){return false;}
                left.add(sequence[i]);
            }else{
                right.add(sequence[i]);
            }
        }

        int[] left_ = new int[left.size()];
        for(int i= 0;i<left.size();i++){
            left_[i] = left.get(i);
        }

        int[] right_ = new int[right.size()];
        for(int i= 0;i<right.size();i++){
            right_[i] = right.get(i);
        }
        if(left_.length!=0 && right_.length!=0){
            return VerifySquenceOfBST(left_) && VerifySquenceOfBST(right_);
        }else if(left_.length!=0 && right_.length == 0){
            return VerifySquenceOfBST(left_);
        }else{
            return VerifySquenceOfBST(right_);
        }

        

    }
}

```



相同思路的简化版本：

```java
import java.util.*;
public class Solution {
    public boolean flag=true;
    public boolean VerifySquenceOfBST(int [] sequence) {
        if(sequence.length==0) return false;
        if(sequence.length==1) return true;
        int root=sequence[sequence.length-1];
        int i=0;
        for(;i<sequence.length-1;i++){
            if(sequence[i]>root) break;
        }
        int[] left=Arrays.copyOfRange(sequence, 0, i);
        int[] right=Arrays.copyOfRange(sequence, i, sequence.length-1);
        for(;i<sequence.length-1;i+ +){
            if(sequence[i]<root) return false;
        }
        boolean flagleft=true,flagright=true;
        if(left.length>0) flagleft=VerifySquenceOfBST(left);
        if(right.length>0) flagright=VerifySquenceOfBST(right);
        return flagright && flagleft;
    }
}
```







# JZ24 二叉树中和为某一值的路径

输入一颗二叉树的根节点和一个整数，按字典序打印出二叉树中结点值的和为输入整数的所有路径。路径定义为从树的根结点开始往下一直到叶结点所经过的结点形成一条路径。



思路

1. 如果当前节点的值大于目标值，则返回空链表

2. 如果当前节点的值等于目标值，且当前节点为叶子节点，则返回此条结果（路径要求必须到叶节点）

3. 如果当前节点值小于目标值，则更新目标值=目标值-当前节点的值
   3.1递归当前节点的左子树，寻找新目标值
   3.2递归当前节点的右子树，寻找新目标值
   （最后要注意节点的判空，避免空指针）



```java
import java.util.ArrayList;
/**
public class TreeNode {
    int val = 0;
    TreeNode left = null;
    TreeNode right = null;

    public TreeNode(int val) {
        this.val = val;

    }

}
*/
public class Solution {
    public ArrayList<ArrayList<Integer>> FindPath(TreeNode root,int target){
        ArrayList<ArrayList<Integer>> ans=new ArrayList<>();
        if(root == null){//为空，则返回空链表
            return ans;
        } 
        if(root.val >target){//根节点大于目标值，则代表没找到，返回空链表
            return ans;
        }
        if(root.val==target){//根节点等于目标值
            if(root.left == null && root.right == null){//根节点是叶节点
                ArrayList<Integer> list=new ArrayList<>();//将根节点值存入数组list中，并添加到结果ans中返回
                list.add(root.val);
                ans.add(list);
                return ans;
            }
            else{
                return ans;//根节点不是叶节点，返回空链表
            }
        }
        if(root.val<target){//根节点的值下于目标值
            ArrayList<ArrayList<Integer>> left=FindPath(root.left,target-root.val);//递归左子树，目标值为原目标值减去根节点的值
            ArrayList<ArrayList<Integer>> right=FindPath(root.right,target-root.val);//递归右子树，目标值为原目标值减去根节点的值
            if( left != null){
                for(int i=0;i<left.size();i++){//左子树存在结果值，可能有多组
                    ArrayList<Integer> tmp=new ArrayList<>();
                    tmp.add(root.val);//先加根节点，再加左子树的结果值，最后加到结果ans中
                    tmp.addAll(left.get(i));
                    ans.add(tmp);
                }
            }
            if(right != null){
                for(int i=0;i<right.size();i++){//右子树存在结果值，可能有多组
                    ArrayList<Integer> tmp=new ArrayList<>();
                    tmp.add(root.val);//先加根节点，再加右子树的结果值，最后加到结果ans中
                    tmp.addAll(right.get(i));
                    ans.add(tmp);
                }
            }
        }
        return ans;
    } 
}
```



# JZ25 复杂链表的复制

描述

输入一个复杂链表（每个节点中有节点值，以及两个指针，一个指向下一个节点，另一个特殊指针random指向一个随机节点），请对此链表进行深拷贝，并返回拷贝后的头结点。（注意，输出结果中请不要返回参数中的节点引用，否则判题程序会直接返回空）。 下图是一个含有5个结点的复杂链表。图中实线箭头表示next指针，虚线箭头表示random指针。为简单起见，指向null的指针没有画出。

<img src="/Users/lizhihan/Library/Application Support/typora-user-images/image-20210919105744962.png" alt="image-20210919105744962" style="zoom:33%;" />



用书上的思路去解决，将大问题拆分成三个小问题：

1. 将每个节点复制，复制后的节点放置在原节点的后面

2. 将原来的每个节点的random指针进行复制，使复制后的节点也拥有自己的random指针

   <img src="/Users/lizhihan/Library/Application Support/typora-user-images/image-20210919110041095.png" alt="image-20210919110041095" style="zoom:75%;" />

3. 将两个链表拆开，复制完成

```java
/*
public class RandomListNode {
    int label;
    RandomListNode next = null;
    RandomListNode random = null;

    RandomListNode(int label) {
        this.label = label;
    }
}
*/
public class Solution {
    public RandomListNode Clone(RandomListNode pHead) {
        if(pHead == null){return null;}
        
      //第一步
        RandomListNode tmp = pHead;
        while(tmp!=null){
           RandomListNode node = new RandomListNode(tmp.label);
           node.next = tmp.next;
           tmp.next = node;
           tmp = node.next;
        }
        
      //第二步
        RandomListNode tmp1 = new RandomListNode(0);
        tmp1 = pHead;
        while(tmp1!=null){
            if(tmp1.random !=null){
                tmp1.next.random = tmp1.random.next;
            }
            tmp1 = tmp1.next.next;
        }
        
      //第三步
        RandomListNode res = pHead.next;    //仅仅作为返回值，本身不进行遍历等操作
        tmp1 = pHead;    //原链表的遍历指针
        RandomListNode tmp3 = res;    //新链表的遍历指针
        while(tmp1!=null){
            tmp1.next = tmp3.next;
            tmp3.next = tmp1.next==null?null:tmp1.next.next;
            
            tmp1 = tmp1.next;
            tmp3 = tmp3.next;
        }
        return res;
    }
}
```



# JZ26 二叉搜索树与双向链表

输入一棵二叉搜索树，将该二叉搜索树转换成一个排序的双向链表。



<img src="https://uploadfiles.nowcoder.com/images/20210605/557336_1622886924427/E1F1270919D292C9F48F51975FD07CE2" alt="img" style="zoom:33%;" />



使用递归的思路，将左子节点变换为双链表，然后将左双链表的尾部与root节点相连；将右子节点变为双链表，然后将root节点与右双链表表头相连接

首先如果当前root节点为空则返回root，当前节点没有子节点则返回自己

然后将当前root节点的左子节点进行操作

遍历左子节点操作完成后的链表，将这个链表的尾部与root链接起来

然后对root节点的右子节点进行操作

将root节点和右子节点操作后的链表进行连接

返回头节点

```java
/**
public class TreeNode {
    int val = 0;
    TreeNode left = null;
    TreeNode right = null;

    public TreeNode(int val) {
        this.val = val;

    }

}
*/
public class Solution {
    public TreeNode Convert(TreeNode root) {
        if (root == null){return null;}
        if (root.left == null && root.right == null){
            return root;
        }
      
        // 1.将左子树构造成双链表，并返回链表头节点
        TreeNode left_tree = Convert(root.left);
        TreeNode tmp = left_tree;
        // 2.定位至左子树双链表最后一个节点
        while(tmp!=null && tmp.right != null){
            tmp = tmp.right;
        }
        // 3.如果左子树链表不为空的话，将当前root追加到左子树链表
        if(left_tree!=null){
            tmp.right = root;
            root.left = tmp;
        }
        // 4.将右子树构造成双链表，并返回链表头节点
        TreeNode right_tree = Convert(root.right);
        // 5.如果右子树链表不为空的话，将该链表追加到root节点之后
         if(right_tree!=null){
             root.right = right_tree;
             right_tree.left = root;
         }
        
        return left_tree == null?root:left_tree;
    }
    
}
```



# JZ27 字符串的排列

https://blog.nowcoder.net/n/a627e888fba84cbf94d2de9b194050b7?f=comment





# JZ28 数组中出现次数超过一半的数字

给一个长度为n的数组，数组中有一个数字出现的次数超过数组长度的一半，请找出这个数字。

例如输入一个长度为9的数组[1,2,3,2,2,2,5,4,2]。由于数字2在数组中出现了5次，超过数组长度的一半，因此输出2。



思路：

根据数组特性，创建三个int来保存数字，第一个数字num记录当前数量最多的那个，第二个数字index记录他的个数，第三个数字max记录当前最多的数字的数量。

遇到相同的num，index++，如果不同则index--，知道index小于0，num才更新为当前的max

```java
import java.util.*;

public class Solution {
    public int MoreThanHalfNum_Solution(int [] array) {
        if(array.length == 1){
            return array[0];
        }
    
        int num = array[0];
        int index = 1;
        int max = 1;
        
        for(int i = 1;i<array.length;i++){
            if(array[i] == num){
                index++;
                max++;
            }else{
                index--;
                if(index<0){
                    num = array[i];
                    index = max;
                }
            }
        }
        return num;
    }
}
```





# JZ29 最小的K个数

给定一个长度为n的可能有重复值的数组，找出其中不去重的最小的k个数。例如数组元素是4,5,1,6,2,7,3,8这8个数字，则最小的4个数字是1,2,3,4(任意顺序皆可)。



思路：

首先将前k个数字放入结果列表中，然后挨个判断后面的数字是否比结果列表中最大的那个小，如果小的话就替换掉结果列表中最大的那个

```java
import java.util.ArrayList;

public class Solution {
    public ArrayList<Integer> GetLeastNumbers_Solution(int [] input, int k) {
        ArrayList<Integer> res = new ArrayList<Integer>();
        if(k == 0){
            return res;
        }
        
        int max = 0;
        int index = 0 ;
        for(int i = 0;i<k;i++){
            res.add(input[i]);
            if(input[i]>max){
                max = input[i];
                index = i;
            }
        }
        
        for(int j = k;j<input.length;j++){
            if(input[j]<max){
                res.set(index, input[j]);
                max = 0;
                for(int i = 0;i<k;i++){
                    if(res.get(i)>max){
                        max = res.get(i);
                        index = i;
                    }
                }
            }
        }
        
        return res;
        
    }
}
```



# JZ30 连续子数组的最大和

输入一个长度为n的整型数组a，数组中的一个或连续多个整数组成一个子数组。求所有子数组的和的最大值。要求时间复杂度为 O(n).



思路：

动态规划算法的思想

1. 新建一个长度和输入数组相同的int[] dp， 我们会在这个list里存储:到每一个元素这里，我们此刻拥有的连续字数组的最大和。同时，我们需要定义这个list里的第一个数是array[0]，因为第一个数只能有自己，前面没有别的数来和他形成连续子数组了。同时，我们创建一个int max，来实时记录当前的最大和。
2. 遍历整个array，然后先新建一个int temp来储存当前遍历到的array[i]与前一位最大和的和，然后进行条件判断，如果这个temp大于当前的array[i]（即当前遍历到的数），我们就将temp储存入dp[i]，如果这个temp小于当前的array[i] (即如果我们只取当前这个数就已经比他加上原来所有的数都大了，我们便可以舍弃前面所有数，从这个数重新开始)，我们将array[i]储存进dp[i]里
3. 在2的遍历里，当我们走完上面的判断，我们还需要判断，当前的dp[i]是不是我们至今为止的最大和，如果是，更新我们前面创建的int max
4. 结束循环后，我们返回int max即可，这便是我们整个连续子数组的最大和

```java
public class Solution {
public int FindGreatestSumOfSubArray(int[] array) {
        if(array.length == 1){
            return array[0];
        }

        int max = array[0];
        int[] dp = new int[array.length];
        dp[0] = array[0];

        for(int i = 1;i<array.length;i++){
            int temp = dp[i-1]+array[i];
            dp[i] = temp<=array[i]?array[i]:temp;
            if(dp[i]>max){
                max = dp[i];
            }
        }
        return max;
    }
}
```





更加精巧的解法：

本质上还是判断循环中上一次循环的结果，是否大于0，如果大于0：当前值+之前的值即为可以新值；小于0则将当前值设置为新值。无论之前的值大小，都仍需判断新值是否可以更新max

```java
public class Solution {
public int FindGreatestSumOfSubArray(int[] array) {
    int max = array[0];
    for (int i = 1; i < array.length; i++) {
        array[i] += array[i - 1] > 0 ? array[i - 1] : 0;
        max = Math.max(max, array[i]);
    }
    return max;
}
}
```







# JZ31 整数中1出现的次数（从1到n整数中1出现的次数

输入一个整数 n ，求1～n这n个整数的十进制表示中1出现的次数
例如，1~13中包含1的数字有1、10、11、12、13因此共出现6次



思路：遍历即可，唯一需要注意的就是整型和string，char的转换；复杂度很高

```java
public class Solution {
    public int NumberOf1Between1AndN_Solution(int n) {
        int res = 0;
        for(int i = 1;i<=n;i++){
            res+=fi(i);
        }
        return res;
    }
    
    public int fi(int m){
        int count = 0;
        String str = String.valueOf(m);
        char[] c = String.valueOf(m).toCharArray();
        for(int i = 0;i<c.length; i++){
            if(c[i] == '1'){
                count++;
            }
        }
        return count;
    }
}
```



相对简化一些，可以使用两个for循环

```java
public int NumberOf1Between1AndN_Solution(int n) {
    int count=0;
    for(int i=n;i>0;i--){
        for(int j=i;j>0;j/=10){
            if(j%10==1) count++;
        }
    }return count;
```



# JZ32 把数组排成最小的数

输入一个正整数数组，把数组里所有数字拼接起来排成一个数，打印能拼接出的所有数字中最小的一个。例如输入数组{3，32，321}，则打印出这三个数字能排成的最小数字为321323



思路：遍历判断，一个数和它后面所有的数进行对比，他们排列方式为mn，nm；如果当前排列时的组合值大于反转后的，那么交换当前遍历的两个位置的值

```java
public class Solution {
    public String PrintMinNumber(int [] numbers) {
        String res = "";
        for(int i = 0;i < numbers.length;i++){
            for(int j = i+1;j<numbers.length;j++){
                Long a = Long.valueOf(""+numbers[i]+numbers[j]);
                Long b = Long.valueOf(""+numbers[j]+numbers[i]);
                if(a>b){
                    int t = numbers[i];
                    numbers[i] = numbers[j];
                    numbers[j] = t;
                }
            }
        }
        for(int i = 0;i<numbers.length;i++){
            res += numbers[i];
        }
        return res;
    }
}
```



# **JZ33** **丑数**

把只包含质因子2、3和5的数称作丑数（Ugly Number）。例如6、8都是丑数，但14不是，因为它包含质因子7。 习惯上我们把1当做是第一个丑数。求按从小到大的顺序的第 n个丑数。



思路：

首先1-6都是丑数，那么就将目前数组中所有元素都乘以2，3，5，分别找到大于目前的最大值的那一个，并取这三个中最小值作为新的丑数序列

```java
import java.util.*;

public class Solution {
    public int GetUglyNumber_Solution(int index) {
        if(index<=6){
            return index;
        }
        
        ArrayList<Integer> base = new ArrayList<Integer>();
        base.add(2);
        base.add(3);
        base.add(4);
        base.add(5);
        base.add(6);
        
        while(base.size()<index){
            int max = base.get(base.size()-1);
            int max_new = 0;
            for(int e = 0;e<base.size();e++){
                if(base.get(e)*2>max){
                    base.add(base.get(e)*2);
                    max_new = base.get(e)*2;
                    break;
                }
            }
            for(int e = 0;e<base.size();e++){
                if(base.get(e)*3>max && base.get(e)*3<max_new){
                    base.set(base.size()-1, base.get(e)*3);
                    max_new = base.get(e)*3;
                    break;
                }
            }
            for(int e = 0;e<base.size();e++){
                if(base.get(e)*5>max && base.get(e)*5<max_new){
                    base.set(base.size()-1, base.get(e)*5);
                    max_new = base.get(e)*5;
                    break;
                }
            }
        }
        return base.get(index-2);
        
    }
}
```



修改后的思路：上面的代码可以成功运行，但是效率比较低，我们发现如果想找到下一个丑数，可以将前一个丑数乘以2，3，5得到，那么就可以用这个思路，如果当前丑数没有乘过2/3/5，我们就用当前的数来进行计算，得到三个数取最小值作为下一个丑数；如果当前的丑数乘过2，那么就用下一个丑数✖️2，当前丑数✖️3/5，并取最小值作为下一个丑数

```java
import java.util.*;

public class Solution {
    public int GetUglyNumber_Solution(int index) {
        if(index<=6){
            return index;
        }
        int[] res = new int[index];
        res[0] = 1;
        int i2 = 0;
        int i3 = 0;
        int i5 = 0;
        
        for(int i = 1;i<index;i++){
            res[i] = Math.min(Math.min(res[i2]*2,res[i3]*3),res[i5]*5);
            if(res[i] == res[i2]*2){i2++;}
            if(res[i] == res[i3]*3){i3++;}
            if(res[i] == res[i5]*5){i5++;}
            
        }
        
        return res[index-1];
        
    }
}
```





# **JZ34** **第一个只出现一次的字符**

在一个长为 字符串中找到第一个只出现一次的字符,并返回它的位置, 如果没有则返回 -1（需要区分大小写）.（从0开始计数）

数据范围：![img](https://www.nowcoder.com/equation?tex=0%20%5Cle%20n%20%5Cle%2010000%20%5C)，且字符串只有字母组成。

要求：空间复杂度 ![img](https://www.nowcoder.com/equation?tex=O(n)%20%5C)，时间复杂度 ![img](https://www.nowcoder.com/equation?tex=O(n)%20%5C)



思路：遍历整个字符串，使用一个hashmap存储第一次遍历的结果；遍历传入的字符串，如果map值为1，就输出当前字符的索引

```java
import java.util.*;
public class Solution {
    public int FirstNotRepeatingChar(String str) {
        if(str.length() == 0 || str == null){
            return -1;
        }
        
        HashMap<Character,Integer> res = new HashMap<Character,Integer>();
        for(int i = 0;i<str.length();i++){
            if(!res.keySet().contains(str.charAt(i))){
                res.put(str.charAt(i),1);
            }else{
                res.put(str.charAt(i),res.get(str.charAt(i))+1);
            }
        }
        
        for(int i = 0;i<str.length();i++){
            if(res.get(str.charAt(i)) == 1){
                return i;
            }
        }
        return -1;
    }
}
```







# **JZ35** **数组中的逆序对**

在数组中的两个数字，如果前面一个数字大于后面的数字，则这两个数字组成一个逆序对。输入一个数组,求出这个数组中的逆序对的总数P。并将P对1000000007取模的结果输出。 即输出P mod 1000000007



思路：

使用归并排序的思想，递归整个函数，直到start>=end

分成两段的数组都是排序过的，用指针进行这两个数组的对比，如果前面数组的值大于后面的，那么count增加前面数组中包含当前数字及以后数字的数量的值，在对比过程中进行排序，并最终将排序后的序列的值更新在原始nums中



```java
public class Solution {
    public int InversePairs(int [] array) {
        return merge(array, 0, array.length-1);
    }

    public int merge(int[] nums, int start, int end){
        if(start >= end){//分解到不能分解的时候的边界
            return 0;
     }
        int mid = (start + end)/2;// mid为中心左右各一半
        int count = 0;
        count += merge(nums, start, mid);
        count += merge(nums,mid+1, end);
        //上面两行是反复对问题进行分解，直到分解到最小
        //将最小问题合并成次小问题之后的处理，也是最核心的部分
        int[] temp = new int[end-start+1];
//temp数组:构建一个和当前合并的数组大小一样的数组，temp就是将两部分合并并且排序
        int i = start;//合并是左边和右边合并，一个指向左边的元素的指针
        int j = mid+1;//一个指向右边的元素的指针
        int p = 0;//temp中的指针
        while(i <= mid && j <= end){//左边部分的边界mid，右边部分的边界end
//这个while实际就是将两个部分，进行合并的时候排序。
            if(nums[i] < nums[j]){
                temp[p] = nums[i];
                p++;  //先复制，再++,对我而言可读性更高，逻辑理解更通顺。
                i++;
            }else{//否则，i就比j大，就说明出现了逆序对，因此维护count。
//这里值得说道说道，temp的长度等于左边+右边的长度。既然有了排序的念头，那么合并之前也排好了
//那么左边部分已经有序，右边部分也有序，比如此时进行{1,5,9}和{3,7,8}合并
//则i=1,mid=2,j=3时进入else，可以看到，通过mid-i+1=2，拿到的是{5,3}，{9,3}两组逆序对
//所以count+2,然后j的角标移动，下次比较的是5和7了。这样避免了重复的比较，提高了效率
//这样的操作必须配合排序，如果不排序，就不能这么玩，而不能这么玩的时候，过程如下：
//{1,5,9}和{3,7,8}合并,由于不知道是否有序，5和3形成逆序后，应当count++
//然后移动一次你自己标记的指针。然后你总会通过移动指针比较一次9和3，然后count++。
//而通过排序，这两个count++就变成了一次操作，因此，排序会提升效率，空间复杂度稍微高点。
//因为你用到了额外的数组，合并排序，并且再复制给原数组。
                count = (count+(mid-i+1))%1000000007;
                temp[p] = nums[j];
                p++;
                j++;
            }
        }
//下面的过程也值得一提，当两个序列合并时，左边或者右边先通过指针移动完毕，全复制进temp后，
//就需要将另一边的数据，也全部复制给temp。
//所以下面两个if分别对应左边先复制完了，专门去复制右边，和右边先复制完了，再去复制左边。
        if(i <= mid){
            while(i <= mid){
                temp[p++] = nums[i];
                i++;
            }
        }
        if(j <= end){
            while(j <= end){
                temp[p++] = nums[j];
                j++;
            }
        }
        for(int k = 0;k < end-start+1; k++){//将合并好的数组再复制回nums，以保证有序。
            nums[start+k] = temp[k];
        }
     return count;
    }
}
//这里再谈谈%1000000007的理解，应该是为了防止溢出，所以必须在每次加的时候进行操作
//而不能放在return语句中
```



# **JZ36** **两个链表的第一个公共结点**

输入两个无环的单向链表，找出它们的第一个公共结点，如果没有公共节点则返回空。（注意因为传入数据是链表，所以错误测试数据的提示是用其他方式显示的，保证传入数据是正确的）



直接遍历的时间复杂度是O(mn)，但是我们知道，如果链表有公共节点，那么根据链表的性质，说明这两个链表的结尾部分是相同的，那么我们可以先各自遍历知道两个链表的长度分别是多少，然后将长的那个链表先向后遍历长度之差步，然后再一起遍历两个链表，直到他们的next是相同的，即可解决问题，这样的时间复杂度是O(m+n)，空间复杂度为O(1)

```java
/*
public class ListNode {
    int val;
    ListNode next = null;

    ListNode(int val) {
        this.val = val;
    }
}*/
public class Solution {
    public ListNode FindFirstCommonNode(ListNode pHead1, ListNode pHead2) {
        if(pHead1 == null || pHead2 == null){return null;}
        
        ListNode tmp1 = pHead1, tmp2 = pHead2;
        int count1 = 0,count2 = 0;
        while(tmp1!=null){
            count1++;
            tmp1 = tmp1.next;
        }
        while(tmp2!=null){
            count2++;
            tmp2 = tmp2.next;
        }
        
        if(count1>count2){
            while(count1!=count2){
                count1--;
                pHead1 = pHead1.next;
            }
        }else{
            while(count1!=count2){
                count2--;
                pHead2 = pHead2.next;
            }
        }
        
        while(pHead1!=pHead2){
            pHead1 = pHead1.next;
            pHead2 = pHead2.next;
        }
        return pHead1;
    }
}
```







# **JZ37** **数字在升序数组中出现的次数**

给定一个长度为 n 的非降序数组和一个非负数整数 k ，要求统计 k 在数组中出现的次数



思路：二分查找的思路，寻找到mid是需要找到的k时，这时候k肯定仅仅在当前left到right之间

```java
public class Solution {
    public int GetNumberOfK(int [] array , int k) {
       if(array==null||array.length==0) return 0;
       int left = 0;
       int right = array.length-1;
       int res = 0;
       int mid = 0;
       while(left<right){// 不能是等于，否则在数组中没出现目标k时，进入无限循环
           mid = left + (right-left)/2;
           if(array[mid]<k){
               left = mid+1;
           }else if(array[mid]>k){
               right = mid;
           }else{
               break;
           }
       }
        
        for(int i = left;i<=right;i++){
            if(array[i] == k){res++;}
        }
        return res;
    }
}
```



# **JZ38** **二叉树的深度**

输入一棵二叉树，求该树的深度。从根结点到叶结点依次经过的结点（含根、叶结点）形成树的一条路径，最长路径的长度为树的深度。



思路：递归的想法就是，当前树的深度等于它的左子树和右子树中更高的那个+1

```java
/**
public class TreeNode {
    int val = 0;
    TreeNode left = null;
    TreeNode right = null;

    public TreeNode(int val) {
        this.val = val;
    }
}
*/
public class Solution {
    public int TreeDepth(TreeNode root) {
    	if(root==null){
        return 0;
    	}
    	int left=TreeDepth(root.left);
    	int right=TreeDepth(root.right);
    	return Math.max(left,right)+1;
	}
}
```



# **JZ39** **平衡二叉树**

输入一棵节点数为 n 二叉树，判断该二叉树是否是平衡二叉树。

在这里，我们只需要考虑其平衡性，不需要考虑其是不是排序二叉树

**平衡二叉树**（Balanced Binary Tree），具有以下性质：它是一棵空树或它的左右两个子树的高度差的绝对值不超过1，并且左右两个子树都是一棵平衡二叉树。



方法一：可以用上一题中的深度函数，然后遍历每个节点，只有当全部节点都是true的时候才满足

```java
public class Solution {
    public boolean IsBalanced_Solution(TreeNode root) {
        if(root == null){return true;}
        
        int left_H = getHigh(root.left);
        int right_H = getHigh(root.right);
        if(Math.abs(left_H-right_H)>1){
            return false;
        }
        return (IsBalanced_Solution(root.left) && IsBalanced_Solution(root.right));
        }
    
    public int getHigh(TreeNode root){
        if(root == null){
            return 0;
        }
        int left = getHigh(root.left);
        int right = getHigh(root.right);
        return Math.max(left,right)+1;
    }

}
```

这种方法可以适当的优化，通过直接在计算深度的函数中判断left和right的深度是否符合标准，如果找到不符合标准的那个，直接返回，可以省很多计算步骤

```java
public class Solution {
    public boolean IsBalanced_Solution(TreeNode root) {
        if(root == null){return true;}
        
        int left_H = getHigh(root.left);
        if(left_H == -1){return false;}
        int right_H = getHigh(root.right);
        if(right_H == -1){return false;}
        if(Math.abs(left_H-right_H)>1){
            return false;
        }
        return (IsBalanced_Solution(root.left) && IsBalanced_Solution(root.right));
        }
    
    public int getHigh(TreeNode root){
        if(root == null){
            return 0;
        }
        int left = getHigh(root.left);
        int right = getHigh(root.right);
        if(Math.abs(left-right)>1){return -1;}
        return Math.max(left,right)+1;
    }

}
```







# **JZ40** **数组中只出现一次的两个数字**

一个整型数组里除了两个数字只出现一次，其他的数字都出现了两次。请写程序找出这两个只出现一次的数字。

要求：空间复杂度 ![img](https://www.nowcoder.com/equation?tex=O(1)%20%5C)，时间复杂度 ![img](https://www.nowcoder.com/equation?tex=O(n)%20%5C)

应该用位运算的，用哈希表一样可以达到要求

```java
import java.util.*;


public class Solution {
    /**
     * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
     *
     * 
     * @param array int整型一维数组 
     * @return int整型一维数组
     */
    public int[] FindNumsAppearOnce (int[] array) {
        // write code here
        int[] res = new int[2];
        HashMap<Integer,Integer> hash = new HashMap<Integer,Integer>();
        for(int i = 0;i<array.length;i++){
            hash.put(i,array[i]);
            
        }
        int tmp = 0;
        for(int i = 0;i<array.length;i++){
            int tempo = hash.remove(i);
            if(hash.containsValue(tempo) == false){
                res[tmp] = tempo;
                tmp++;
            }
            hash.put(i,tempo);
            if(tmp == 2){
                break;
            }
        }
        if(res[0]<res[1]){
            return res;
        }else{
            int tmp1 = res[0];
            res[0] = res[1];
            res[1] = tmp1;
            return res;
        }


    }
}
```





# **JZ41** **和为S的连续正数序列**

小明很喜欢数学,有一天他在做数学作业时,要求计算出9~16的和,他马上就写出了正确答案是100。但是他并不满足于此,他在想究竟有多少种连续的正数序列的和为100(至少包括两个数)。没多久,他就得到另一组连续正数和为100的序列:18,19,20,21,22。现在把问题交给你,你能不能也很快的找出所有和为S的连续正数序列? Good Luck!



穷举，用双指针的方法之后再做

https://blog.nowcoder.net/n/e70422cbd34d498aa0b55696def12391?f=comment

```java
import java.util.ArrayList;
public class Solution {
    public ArrayList<ArrayList<Integer> > FindContinuousSequence(int sum) {
       ArrayList<ArrayList<Integer> > res = new ArrayList<>();
       int tmp = 1;
       int f = 0;
       int flag = 0;
       while(tmp<sum){
           for(int i = tmp;i<sum;i++){
               f += i;
               if(f>sum){
                   f = 0;
                   break;
               }
               if(f == sum){
                   ArrayList<Integer> fi = new ArrayList<Integer>();
                   for(int j = tmp;j<=i;j++){
                       fi.add(j);
                   }
                   res.add(fi);
               }
           }
           tmp++;
       }
       return res;
    }
}
```







# **JZ42** **和为S的两个数字**

输入一个递增排序的数组和一个数字S，在数组中查找两个数，使得他们的和正好是S，如果有多对数字的和等于S，返回两个数的乘积最小的，如果无法找出这样的数字，返回一个空数组即可。



既然是排序的数组，那么我们可以用双指针，一个指开头一个指结尾，如果和大于目标值，结尾指针前移；和小于目标值，开头指针后移

```java
import java.util.ArrayList;
public class Solution {
    public ArrayList<Integer> FindNumbersWithSum(int [] array,int sum) {
        ArrayList<Integer> res = new ArrayList<Integer>();
        if(array.length<=0){
            return res;
        }
        int a = 0;
        int b = array.length-1;
        while(a < b){
            if(array[a]+array[b] == sum){
                res.add(array[a]);
                res.add(array[b]);
                break;
            }else if(array[a]+array[b]<sum){
                a++;
            }else{
                b--;
            }
            
        }
        return res;
    }
}
```





# **JZ43** **左旋转字符串**

汇编语言中有一种移位指令叫做循环左移（ROL），现在有个简单的任务，就是用字符串模拟这个指令的运算结果。对于一个给定的字符序列 S，请你把其循环左移 K 位后的序列输出（保证 K 小于等于 S 的长度）。例如，字符序列S=”abcXYZdef”,要求输出循环左移 3 位后的结果，即“XYZdefabc”。是不是很简单？OK，搞定它！



主要思路就是，左移三位的实质就是先将这个字符串反转，然后再分别反转前三位和后面的位数，再将反转之后的结果拼接起来

```java
public class Solution {
    public String LeftRotateString(String str,int n) {
        if(str.length() == 0){return "";}
        
        String rev1 = reverse(str);
        String rev2_1 = rev1.substring(0,str.length()-n);
        String rev2_2 = rev1.substring(str.length()-n,str.length());
        return reverse(rev2_1)+reverse(rev2_2);
    }
    
    public String reverse(String str){
        char[] tmp = str.toCharArray();
        char[] c = str.toCharArray();
        for(int i = 0;i<tmp.length;i++){
            c[tmp.length-1-i] = tmp[i];
        }
        return String.copyValueOf(c);
    }
}
```







# **JZ44** **翻转单词序列**

牛客最近来了一个新员工Fish，每天早晨总是会拿着一本英文杂志，写些句子在本子上。同事Cat对Fish写的内容颇感兴趣，有一天他向Fish借来翻看，但却读不懂它的意思。例如，“nowcoder. a am I”。后来才意识到，这家伙原来把句子单词的顺序翻转了，正确的句子应该是“I am a nowcoder.”。Cat对一一的翻转这些单词顺序可不在行，你能帮助他么？





先写一个反转字符串的函数，先翻转整个字符串，然后再挨个翻转每个单词

```java
public class Solution {
    public String ReverseSentence(String str) {
        String rever_1 = reverse(str);
        String[] split1 = rever_1.split(" ");
        String res = "";
        for(int i = 0;i<split1.length;i++){
            split1[i] = reverse(split1[i]);
            res+=split1[i]+" ";
        }
        return res.substring(0, res.length() -1);
        
    }
    
    public String reverse(String str){
        char[] c = str.toCharArray();
        char[] copy = str.toCharArray();
        
        for(int i = 0;i < c.length;i++){
            copy[c.length-1-i] = c[i];
        }
        String res = String.valueOf(copy);
        return res;
    }
}
```







# **JZ45** **扑克牌顺子**

现在有2副扑克牌，从扑克牌中随机五张扑克牌，我们需要来判断一下是不是顺子。
有如下规则：

1. A为1，J为11，Q为12，K为13，A不能视为14
2. 大、小王为 0，0可以看作任意牌
3. 如果给出的五张牌能组成顺子（即这五张牌是连续的）就输出true，否则就输出false。
4. 数据保证每组5个数字，每组最多含有4个零，数组的数取值为 [0, 13]



要求：空间复杂度 ![img](https://www.nowcoder.com/equation?tex=O(1)%20%5C)，时间复杂度 ![img](https://www.nowcoder.com/equation?tex=O(nlogn)%20%5C)，本题也有时间复杂度 ![img](https://www.nowcoder.com/equation?tex=O(n)%20%5C) 的解法





思路1：先排序，排序的复杂度为 ![img](https://www.nowcoder.com/equation?tex=O(nlogn)%20%5C)，所以满足要求。排序后计算除去0以外的后一位减去前一位-1，加和，如果这个sum小于0的个数，说明可以用0补齐，但是需要注意有两个数相等的时候也是不满足要求的，所以需要进行判断

```java
import java.util.*;

public class Solution {
    public boolean IsContinuous(int [] numbers) {
        if(numbers.length<=4){
            return false;
        }
        
        Arrays.sort(numbers);
        int count = 0;
        int sum = 0;
        for(int i = 0; i<numbers.length; i++){	//求0的个数
            if(numbers[i] == 0){
                count++;
            }
        }
        
        for(int i = numbers.length-1;i>count;i--){	//求缺的位数
            if(numbers[i] == numbers[i-1]){return false;}
            sum += numbers[i]-numbers[i-1]-1;
        }
        if(count>=sum){	//0可以补齐缺的位数吗？
            return true;
        }else{
            return false;
        }
    }
}
```



# JZ？n个骰子的点数





# **JZ46** **孩子们的游戏(圆圈中最后剩下的数)**

每年六一儿童节,牛客都会准备一些小礼物去看望孤儿院的小朋友,今年亦是如此。HF作为牛客的资深元老,自然也准备了一些小游戏。其中,有个游戏是这样的:首先,让 n 个小朋友们围成一个大圈。然后,他随机指定一个数 m ,让编号为0的小朋友开始报数。每次喊到 m-1 的那个小朋友要出列唱首歌,然后可以在礼品箱中任意的挑选礼物,并且不再回到圈中,从他的下一个小朋友开始,继续0... m-1报数....这样下去....直到剩下最后一个小朋友,可以不用表演,并且拿到牛客名贵的“名侦探柯南”典藏版(名额有限哦!!^_^)。请你试着想下,哪个小朋友会得到这份礼品呢？(注：小朋友的编号是从0到 n-1)

如果没有小朋友，请返回-1

数据范围：![img](https://www.nowcoder.com/equation?tex=0%20%5Cle%20n%20%5Cle%205000%20%5C)，![img](https://www.nowcoder.com/equation?tex=0%20%5Cle%20m%20%5Cle%201000%20%5C)

要求：空间复杂度 ![img](https://www.nowcoder.com/equation?tex=O(1)%20%5C)，时间复杂度 ![img](https://www.nowcoder.com/equation?tex=O(n)%20%5C)



数学方法可以做到复杂度要求，但是这里我用的是链表的方法

```java
public class Solution {
    public int LastRemaining_Solution(int n, int m) {
        if(n<=0){return -1;}
        
        TreeNode root = new TreeNode(0);
        TreeNode tmp = root;
        for(int i = 1;i<n;i++){
            tmp.next = new TreeNode(i);
            tmp = tmp.next;
        }
        tmp.next = root;	//比较巧妙的点在于这个tmp目前在0的前一个，这也就保证了后面达到要求需要的步数是一致的
        int k = 0;
        while(tmp.next!=tmp){
            k++;
            if(k == m){
                tmp.next = tmp.next.next;
                k = 0;
            }else{
                tmp = tmp.next;
            }
        }
        return tmp.val;
    }
    
    public class TreeNode {
        int val = 0;
        TreeNode next = null;

        public TreeNode(int val) {
            this.val = val;
    }
}
}
```



# **JZ47** **求1+2+3+...+n**

求1+2+3+...+n，要求不能使用乘除法、for、while、if、else、switch、case等关键字及条件判断语句（A?B:C）。



数学方法：求和公式，利用了int数字右移一位等于数字除以二

```java
public class Solution {
    public int Sum_Solution(int n) {
        int sum = (int)Math.pow(n,2)+n;
        return sum>>1;
    }
}
```



递归：&&的特性是如果前面的判断为真，那么后面的式子不判断，通过这个特性实现if的功能

```java
public class Solution {
    public int Sum_Solution(int n) {
      boolean a = (n>1) && (n+=Sum_Solution(n-1))>1;
      return n;
    }
}
```



# **JZ48** **不用加减乘除做加法**

写一个函数，求两个整数之和，要求在函数体内不得使用+、-、*、/四则运算符号。



首先看十进制是如何做的： 5+7=12，三步走
第一步：相加各位的值，不算进位，得到2。
第二步：计算进位值，得到10. 如果这一步的进位值为0，那么第一步得到的值就是最终结果。
第三步：重复上述两步，只是相加的值变成上述两步的得到的结果2和10，得到12。

同样我们可以用三步走的方式计算二进制值相加： 5-101，7-111 

第一步：相加各位的值，不算进位，得到010，二进制每位相加就相当于各位做异或操作，101^111。
第二步：计算进位值，得到1010，相当于各位做与操作得到101，再向左移一位得到1010，(101&111)<<1。
第三步重复上述两步， 各位相加 010^1010=1000，进位值为100=(010&1010)<<1。
继续重复上述两步：1000^100 = 1100，进位值为0，跳出循环，1100为最终结果 





不用递归

```java
public class Solution {
    public int Add(int num1,int num2) {
        int result = 0;
        int carry = 0;
        do{
            result = num1 ^ num2;       //不带进位的加法
            carry = (num1 & num2) << 1; //进位
            num1 = result;  
            num2 = carry;   
        }while(carry != 0); // 进位不为0则继续执行加法处理进位
        return result;
    }
}
```



用递归

```java
public class Solution {
    public int Add(int num1,int num2) {
        return num2 !=0 ? Add(num1^num2, (num1&num2)<<1) : num1;
    }
}
```



# **JZ49** **把字符串转换成整数**

将一个字符串转换成一个整数，要求不能使用字符串转换整数的库函数。 数值为0或者字符串不是一个合法的数值则返回0



主要需要注意的点：异常输入（仅仅允许第一位输入+，-这两个特殊字符，其他位必须为数字），数字大小超出int的范围，

```java
public class Solution {
    public int StrToInt(String str) {
        if(str.length()<=0){return 0;}
        
        char[] orig  = str.toCharArray();
        boolean isNegative = false;
        long res = 0;    //用long来保存数字，防止越界
        
        for(int i = 0;i<str.length();i++){
            //判断正负
            if(i == 0 && orig[i] == '-'){
                isNegative = true;
            }else if(i == 0 && orig[i] == '+'){
                isNegative = false;
            }else{
            //判断第一位之后是否是数字
            int a = (int)(orig[i]-'0');
            if(a<0 || a>9){
                return 0;
            }else{
                if(isNegative){
                    res = res*10-a;
                }else{
                    res = res*10+a;
                }
            }
            }
            // 判断是否超出int的范围
            if(res>Integer.MAX_VALUE || res<Integer.MIN_VALUE){
                return 0;
            }
            
        }
        
        return (int)res;
    }
}
```





