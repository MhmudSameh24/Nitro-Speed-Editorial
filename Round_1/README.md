# Editorial Round 1

### Problem A.Welcome In Nitro Speed

<details>
    <summary>Solution</summary>
      <p>Observe that since we are only allowed to choose <code>i≥2</code> to swap <code>ai</code> and <code>ai+1</code>
        , it means that a1 cannot be modified by the operation. Hence, <code>a1=1</code>
        must hold. We can prove that as long as <code>a1=1</code> , we will be able to sort the array.</p>
        <br>
    <p>
        Consider the largest element of the array. Let its index be i. Our objective is to move ai to the end of the array. If i=n, it means that the largest element is already at the end. Otherwise, since ai is the largest element, this means that ai−1 &lt; ai and ai &gt; ai+1. Hence, we can do an operation on index i and move the largest element one step closer to the end. We repeatedly do the operation until we finally move the largest element to the end of the array. Then, we can pretend that the largest element does not exist and do the same algorithm for the prefix of size n−1. Hence, we will able to sort the array by doing this repeatedly.
    </p>
</details>