是否还记得[这道题](../19.%20Merge%20Two%20Sorted%20Lists)呢，都是 merge，算法思路上并无太大差别。

这道题还降低了点难度，因为没有链表那些指来指去的指针。

思路主要是利用 A 数组富裕的地方（题意说明 A 的范围不必担心），即 A 数组后面的位置。这样才能保证 merge 的同时，不会破坏两个数组的完整性。

这就要求从后面迭代起了，在 A 和 B 都未迭代完的情况下，比较大小插入即可。值得注意的是，如果 A 先走完，还要继续插入 B 的剩下数据，反之，若 B 先走完，则不需要再做什么，因为本来就是 A 的数组。
```cpp
for (int k = m+n-1, i = m-1, j = n-1; k>=0; --k)
    if (i>=0 && j>=0) A[k] = A[i]>B[j]?A[i++]:B[j++];
    else if (j>=0) A[k] = B[j--];
```

太简单，我几乎又写了一遍答案。
