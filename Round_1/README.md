# Editorial Round 1

### Problem B. Permutation Swaps

<details>
    <summary>Solution</summary>
      <p>Observe that since we are only allowed to choose <code>i≥2</code> to swap <code>ai</code> and <code>ai+1</code>
        , it means that a1 cannot be modified by the operation. Hence, <code>a1=1</code>
        must hold. We can prove that as long as <code>a1=1</code> , we will be able to sort the array.</p>
        <br>
    <p>
        Consider the largest element of the array. Let its index be i. Our objective is to move ai to the end of the array. If i=n, it means that the largest element is already at the end. Otherwise, since ai is the largest element, this means that <code>ai−1 &lt; ai</code> and <code>ai &gt; ai+1</code>. Hence, we can do an operation on index i and move the largest element one step closer to the end. We repeatedly do the operation until we finally move the largest element to the end of the array. Then, we can pretend that the largest element does not exist and do the same algorithm for the prefix of size <code>n−1</code>. Hence, we will able to sort the array by doing this repeatedly.
    </p>
</details>


### Problem C. Equal Parity?

<details>
    <summary>Solution</summary>
    <br><br>
    <p>
        Note is that after doing two operations of the same type, they are "cancelled out" in terms of parity, since we would change the parity of all elements once, then change it back again. <br><br>
        So, we know that we will do each operation exactly 0 or 1
        time. It is possible to check all possible cases just by simulating, or we can notice that all elements on all indices of the same parity must have the same parity and if they do we can always find an answer, by doing just a single type of operation a single time (in case the array doesn't already contain all elements of the same parity). <br><br>
        The time complexity is O(n).
    </p>
</details>




### Problem D. Teams Maker Machine

<details>
    <summary>Solution</summary>
    <br>
    <p>
        Let's write our <code>"unique"</code> function. Keep the array of the taken elements <i><b>used</b></i>. Iterate over all elements in the array a and if the current element is not used (<i><b>used[a<sub>i</sub>]</b></i>=<i><b>false</b></i>) then add its index i to the answer and set <i><b>used[a<sub>i</sub>]</b></i>:=<i><b>true</b></i>. When finished, check the number of distinct values (that is the size of answer array). If it is less than <i><b>k</b></i>, print "NO". Otherwise print "YES" and output the first <i><b>k</b></i> elements of the answer.
    </p>
</details>


### Problem E. Strings Parser Pro Max

<details>
    <summary>Solution</summary>
    <br>
    <p>
        Let's iterate through the given string from the left to the right. In a variable <i><b>cnt</b></i>
        we will store the number of letters "x" which were before the current letter in a row. If the current letter does not equal to "x" we should make <i><b>cnt</b></i>=0
        . In the other case, the current letter equals to "x". If <i><b>cnt</b></i> &lt; 2
        , we should increase cnt
        by one. In the other case, we should add one to the answer because the current letter should be removed.
    </p>
</details>
