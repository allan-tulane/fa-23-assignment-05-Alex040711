# CMPS 2200 Assignment 5

## Answers

**Name:**________Alex Li _________________

- **1a. logd n**
- **1b. O(lg n), O(lg n)**
- **1c. O(E log V)**
- **1d. d=|V|^ϵ**
- **2a.**
- **The shortest path from vertex 0 to vertex 0 is 0.**
- The shortest path from vertex 0 to vertex 1 is 2.
- The shortest path from vertex 0 to vertex 2 is -2.
- There is no path from vertex 1 to vertex 0 that uses only vertices up to 2, thus it remains infinity.
- The shortest path from vertex 1 to vertex 1 is 0.
- The shortest path from vertex 1 to vertex 2 is 1.
- There is no path from vertex 2 to vertex 0 or from vertex 2 to vertex 1 that uses only vertices up to 2, thus they remain infinity.
- The shortest path from vertex 2 to vertex 2 is 0.
- **2b. APSP(i,j,2)=Min(APSP(i,j,1), APSP(i,2,1) + APSP(2,j,1))**
- **2c.APSP(i,j,k)=Min(APSP(i,j,k-1), APSP(i,k,k-1) + APSP(k,j,k-1))**
- **2d. n^3, O(n^3)**
- **2e. O(n^3), O(n^2 log n + nE), when edges E is close to n^2, our algorithm is better**
- **3a. A solution to the MST problem is not guaranteed to be a solution to the MMET problem.**
- The objectives of the MST and MMET problems are fundamentally different, leading to potentially different solutions. An MST is not necessarily an MMET, as the MST focuses on minimizing the total weight, while the MMET focuses on minimizing the maximum weight of any edge in the tree.
- **3b.**

function findSecondBestMST(graph):
    T = findMST(graph)  // Use Kruskal's or Prim's algorithm
    secondBestWeight = infinity
    secondBestTree = null

    for each edge e in T:
        remove e from T
        for each edge e' in graph:
            if e' connects the two subtrees created by removing e and e' != e:
                T' = T + e'
                if weight(T') < secondBestWeight and weight(T') > weight(T):
                    secondBestWeight = weight(T')
                    secondBestTree = T'
        add e back to T

    return secondBestTree


3c. O(V* E log E)
