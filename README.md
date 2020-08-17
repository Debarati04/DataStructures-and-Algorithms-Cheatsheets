# Compilation of few of the most commonly used data structures and the methods in Java

## **Trees**
Understanding O(log n) and basic recursive algo of binary tree:
* http://www.cs.gettysburg.edu/~ilinkin/courses/Fall-2012/cs216/notes/bintree.pdf
* https://www.youtube.com/watch?v=pcKY4hjDrxk

#### *BFS*
* DEQUEUE used
* Level order traversal
* Use queue and put left and right child and dequeue it and add to result
* ALL connections at one time
* Repeat till queue is empty
* Time complexity: O(n)
* Space complexity: best: O(1), worst: O(n/2)=O(n)
https://www.geeksforgeeks.org/breadth-first-search-or-bfs-for-a-graph/

###### Binary Tree Level Order Traversal
Algorithm:
```
Take a global variable of list of lists - levels
List<List<Integer>> levels = new ArrayList<List<Integer>>();
If root is null
     return levels
else
    call helper function with level which is initially set to 0 (recursive function)
In the helper function:
If level is same as size of queue
    Create a new arraylist
if(root.left is not null)
   Call helper(root.left, level+1)
if(root.right is not null)
   Call helper(root.right, level+1)
```

#### *DFS*
* STACK used
* Push element in stack
* When pushed, add to result
* Also, when push, add to visited array
* 1 connection at one time
* Repeat till stack is empty
* Time complexity: O(n)
* Space complexity: best: O(log n) - avg. height of tree worst: O(n)

https://www.geeksforgeeks.org/depth-first-search-or-dfs-for-a-graph/

###### DFS traversals
1. Inorder (DFS: left, self, right)
2. Postorder (DFS: left, right, self)
3. Preorder (DFS: self, left, right)

https://www.geeksforgeeks.org/tree-traversals-inorder-preorder-and-postorder/

Duplicate value in trees - Insert at right subtree so that inorder traversal gives stable sort - number which is inserted later appears later in the result.

## **LinkedList**
#### *Iterators*

Iterate through a linked list using Iterators:
https://beginnersbook.com/2013/12/how-to-loop-linkedlist-in-java/
```
Iterator i = linkedlist.iterator();
while (i.hasNext()) {
    System.out.println(i.next());
}
```
i.next() gives the value, if you again do i.next(), it will get the next value.

#### *Poll() method*

1. poll() : This method retrieves and removes the head (first element) of this list.
2. pollFirst() : This method retrieves and removes the first element of this list, or returns null if this list is empty.
3. pollLast() : This method retrieves and removes the last element of this list, or returns null if this list is empty.

## **Queue**

#### *Poll() method*
The poll() method of Queue Interface returns and removes the element at the front of the container. It deletes the element in the container. The method does not throw an exception when the Queue is empty, it returns null instead.

Used in BFS - *Dequeue*
```
// create object of Queue
Queue<Integer> Q = new LinkedList<Integer>();

// Add numbers to end of Queue
Q.add(423);
Q.add(3432);

// print queue
System.out.println("Queue: " + Q);
  
// print head and deletes the head
System.out.println("Queue's head: " + Q.poll());
```
#### *Offer() method*
Inserts the specified element into this queue if it is possible to do so immediately without violating capacity restrictions. This method is preferable to add() method since this method does not throws an exception when the capacity of the container is full since it returns false.
```
if (Q.offer(10)) 
            System.out.println("The Queue is not full"
                               + " and 10 is inserted"); 
        else
            System.out.println("The Queue is full"); 
```
## **SubArray Sum**

#### Maximum Subarray Sum
https://hackernoon.com/kadanes-algorithm-explained-50316f4fd8a6

#### Circular subarray sum
https://leetcode.com/problems/maximum-sum-circular-subarray/discuss/633401/Kadane-Algorithm-Trick-beats-100-Java-Explained


## **HashMap**
#### *Iterate a HashMap*
https://mkyong.com/java/java-how-to-iterate-a-hashmap/

3 ways:

1. For each loop
```
Map<String, String> map = new HashMap<>();
    map.forEach((key, value) -> System.out.println("[Key] : " + key + " [Value] : " + value));
```
2. Normal for loop in entrySet
```
Map<String, String> map = new HashMap<>();

for (Map.Entry<String, String> entry : map.entrySet()) {
    System.out.println("[Key] : " + entry.getKey() + " [Value] : " + entry.getValue());
}
```
3. Iterator - classic
```
Map<String, String> map = new HashMap<>();

Iterator iter = map.entrySet().iterator();
while (iter.hasNext()) {
    Map.Entry entry = (Map.Entry) iter.next();
    System.out.println("[Key] : " + entry.getKey() + " [Value] : " + entry.getValue());
}
```
#### *Get key set and value from key*
```
for(int key: map.keySet()){
    int value = map.get(key);
}
```
#### *computeIfAbsent*
Compute value for a given key using the given mapping function, if key is not already associated with a value (or is mapped to null) and enter that computed value in Hashmap else null.
```
map.computeIfAbsent("key5", k -> 2000 + 33000);
```

## **Convert int to long in java**
```
int i=100;  
long l1= new Long(i);//first way
long l2=Long.valueOf(i);//second way 
//Best way - takes care of overflow
long l3 = Math.abs(Long.valueOf(i));
       System.out.println(Math.abs(1.0 / 0)); // prints Infinity

```

## **StringBuilder Methods**

* **insert method** - public StringBuilder insert(int offset, char c)
Inserts the character c at the index denoted by offset.

```
StringBuilder str = new StringBuilder("Tutorial");
System.out.println("string = " + str);

// insert character value at offset 8
str.insert(8, 's');

// prints StringBuilder after insertion
System.out.print("After insertion = ");
System.out.println(str.toString());

Output:
string = Tutorial
After insertion = Tutorials
```

* **indexOf method** - public int indexOf(String str)
The indexOf(String str) method of StringBuilder class is the inbuilt method used to return the index within the String for first occurrence of passed substring as parameter. If substring str is not present then -1 is returned.

```
StringBuilder str = new StringBuilder("GeeksForGeeks");

// print string
System.out.println("String contains = " + str);

// get index of string For
int index = str.indexOf("For");

// print results
System.out.println("index of string 'For' = "+ index); // answer: 5
```
## **Set**

#### **Add method**
If element does not exist in set, it is added and return true
Else returns false
```
// Creating an empty Set
Set<String> s = new HashSet<String>();
  
// Use add() method to add elements into the Set
s.add("Welcome");
```

## **Division**
To divide two integers and get the float value do the below:
```
int a = 1;
int b = 2;
double ans = (double)(a/b);
```

## **String**

#### **Split string by whiteSpace**
```
String[] textWords = text.split(" ");
```
#### **Remove whitespaces from a String**
```
public String replace(char oldch, char newch)
public String replaceAll(String regex, String replace_str)
public String replaceFirst(String regex, String replace_str)
```

#### **Remove whitespace from beginning and end of string**
```
str.trim()
```
#### **Join Strings by delimiters**
```
public static String join(CharSequence delimiter,CharSequence... elements)

Eg:
String[] sentence = {"a","bcd","de"};
String.join("^",sentence);
Output: a^bcd^de
```

#### **Capitalize first letter of string**
```
String str = "hello world!";

// capitalize first letter
String output = str.substring(0, 1).toUpperCase() + str.substring(1);
```

#### **Sort String array based on length of the string -  Use Comparator**
```
//doing this will sort the strings lexicographically
Arrays.sort(textWords)

//doing this will sort strings according to length
Arrays.sort(textWords, Comparator.comparingInt(String::length));

//same as above (another version of using comparator)
Arrays.sort(textWords, (a,b) -> Integer.compare(a.length(), b.length()));
```

#### **Convert char array to String**
```
char[] array = s.toCharArray();
String new = new String(array);
```
Note: Do Not Use arr.toString() - will return the reference of the new string and not the string itself.

#### **Sorting of arrays - API**
```
public static void sort(Object[] a, int fromIndex, int toIndex)
```

## **HashSet**

containsAll() method:
check whether two sets contain the same elements or not. It takes one set as a parameter and returns True if all of the elements of this set is present in the other set.

// all elements of set2 are present in set1
set1.containsAll(set2);
## **Arrays**
#### **copyOf**
copyOf(int[] original,int newLength) method copies the specified array, truncating or padding with zeros (if necessary) so the copy has the specified length.

```
int[] org = new int[] {1, 2 ,3};
int[] copy = Arrays.copyOf(org, 5); //copy = {1,2,3,0,0}
int[] copy = Arrays.copyOf(org, 2); //copy = {1,2}
```

## **Comparison**

#### **Arrays**
Below is used to check of 2 arrays are equal:
```
if(Arrays.equals(array1, array2)){
    System.out.println(“equal array”);
}
```
#### **Hashmaps**
Below is used to check if 2 hashmaps are equal:
```
if(map1.equals(map2)){
    System.out.println(“equal hashmap”);
}
```
## **ArrayList**

#### **Sort an ArrayList**
```
ArrayList<Integer> list = new ArrayList<>();
Collections.sort(list);
```
Character array of 128 characters to compare ASCII characters since ASCII has 128 characters and extended ASCII has 256 characters.

#### **Add two ArrayLists**

```
arrlist1 = {2,4,6};
arrlist2 = {3,5,7};
arrlist1.addAll(arrlist2) // {2,4,6,3,5,7}
```

#### **Difference between arraylist.set(index, element) and arraylist.add(index, element)**
set method replaces the element in the specified position with the new element. But in add(position, element) will add the element in the specified position and shifts the existing elements to right side of the array .
```
ArrayList<String> al = new ArrayList<String>();

al.add("a");
al.add(1, "b");
System.out.println(al);

al.set(0, "c");
System.out.println(al);

al.add(0, "d");
System.out.println(al);

---------------Output -------------------------------------

[a, b]

[c, b]

[d, c, b]
        
```
## **Random class**
#### **nextInt()**
Returns the next pseudorandom, uniformly distributed int value from this random number generator's sequence.

#### **nextInt(int bound)**
Returns a pseudorandom, uniformly distributed int value between 0 (inclusive) and the specified value (exclusive), drawn from this random number generator's sequence.
https://docs.oracle.com/javase/8/docs/api/java/util/Random.html

## **Bit Manipulation**

* Binary representation of -K (negative number K) as a N-bit number is concat(1,2<sup>N-1</sup> - K).
* Left shift is equivalent to multiplication by 2
* Logical Right shift is shifting bits and putting 0 in most significant bit.
* Arithmetic Right shift is equivalent to division by 2 and adding 1 (shifts bits to right and fills new bits with value of sign bit)

https://www.youtube.com/watch?v=NLKQEOgBAnw

## **Dynamic Programming**

* Top-down (Memoization)
* Bottom-Up (Tabulation)

https://www.geeksforgeeks.org/tabulation-vs-memoization/
https://cs.stackexchange.com/questions/2644/is-there-a-difference-between-top-down-and-bottom-up-dynamic-programming
https://www.youtube.com/watch?v=NFJ3m9a1oJQ

## **Heaps**

* Implemented using Priority Queue
* Min Heap
```
PriorityQueue<Integer> minHeap = new PriorityQueue<Integer>();
```
* Max Heap
```
PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder());
```

## **TreeMap**

* Keys are always sorted
* ceilingKey(key)
  The ceilingKey() function of TreeMap Class returns the least key greater than or equal to the given key or null if the such a key is absent.
* floorKey
  The floorKey() method is used to return the greatest key less than or equal to given key from the parameter.
  
## **Regex**
Regex is expensive, avoid wherever possible to improve runtime.
Example: replaceAll uses regex

## **Notes**

1. ArrayList has indexOf method, Array does not have this method.
2. Javadocs recommends to use ArrayDeque, and not Stack as a stack implementation
