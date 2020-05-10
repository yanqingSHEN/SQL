### Question Link: [Hackerrank/Binary Tree Nodes](https://www.hackerrank.com/challenges/binary-search-tree-1/problem)


## Solution
SELECT N,
       IF(P IS NULL,'Root',IF((SELECT COUNT(*) FROM BST WHERE P=B.N)>0,'Inner','Leaf'))
FROM   BST AS B
ORDER BY N
