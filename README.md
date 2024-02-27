## ExpNo 3 : Implement Breadth First Search Traversal of a Graph
### Name: VAISHNAVI S
### Register Number: 212222230165
## Aim:
To Implement Breadth First Search Traversal of a Graph using Python 3.
## Theory:
Breadth-First Traversal (or Search) for a graph is like the Breadth-First Traversal of a tree.
The only catch here is that, unlike trees, graphs may contain cycles so that we may come to the same node again. To avoid processing a node more than once, we divide the vertices into two categories:

1.Visited

2.Not Visited

A Boolean visited array is used to mark the visited vertices. For simplicity, it is assumed that all vertices are reachable from the starting vertex. BFS uses a queue data structure for traversal.
### How does BFS work?
  Starting from the root, all the nodes at a particular level are visited first, and then the next level nodes are traversed until all the nodes are visited.
To do this, a queue is used. All the adjacent unvisited nodes of the current level are pushed into the queue, and the current-level nodes are marked visited and popped from the queue.
Illustration:
Let us understand the working of the algorithm with the help of the following example.
### Step1: 
Initially queue and visited arrays are empty.
![277148319-8acdebf8-ecc2-4d10-a208-45cce441f059](https://github.com/Vaishnavi-saravanan/19AI405ExpNo3/assets/118541897/fe81d68e-0752-47ef-80b2-cee9752e651a)


Queue and visited arrays are empty initially.
### Step2:
Push node 0 into queue and mark it visited.

![277148352-0e9ce012-8e1f-43d7-b7b9-c0fb19fe0c3f](https://github.com/Vaishnavi-saravanan/19AI405ExpNo3/assets/118541897/0c889faf-1449-413d-a329-1f94de43641a)



Push node 0 into queue and mark it visited.
### Step 3: 
Remove node 0 from the front of queue and visit the unvisited neighbours and push them into queue.
![277148379-67d8fa3b-ce9e-46c2-9dd7-089e204e667a](https://github.com/Vaishnavi-saravanan/19AI405ExpNo3/assets/118541897/a04f2313-b5ae-4951-a4de-75948bfaa76a)


### Step 4:
Remove node 1 from the front of queue and visit the unvisited neighbours and push them into queue.

![277148430-b0cf0fde-8a86-41cb-a054-36875ac24ab0](https://github.com/Vaishnavi-saravanan/19AI405ExpNo3/assets/118541897/4edb37d7-7a7b-43f7-aeea-b4891fac1579)


### Step 5:
Remove node 2 from the front of queue and visit the unvisited neighbours and push them into queue.
![277148459-8968a163-6b3a-4f7e-8ad4-bbf24f326b9b](https://github.com/Vaishnavi-saravanan/19AI405ExpNo3/assets/118541897/ca3a02f0-0d21-425d-8f62-cc2084f52307)


### Step 6:
Remove node 3 from the front of queue and visit the unvisited neighbours and push them into queue. 
As we can see that every neighbours of node 3 is visited, so move to the next node that are in the front of the queue.
![277148500-7a1c1b16-ea69-497f-a099-8440200f6dc0](https://github.com/Vaishnavi-saravanan/19AI405ExpNo3/assets/118541897/62b3d531-1796-4cbb-bc95-f4e6f4b9802b)


### Steps 7: 
Remove node 4 from the front of queue and visit the unvisited neighbours and push them into queue. 
As we can see that every neighbours of node 4 are visited, so move to the next node that is in the front of the queue.

![277148529-8e16ffa3-c3d6-4774-822b-6eb84adedad9](https://github.com/Vaishnavi-saravanan/19AI405ExpNo3/assets/118541897/6df79f8a-fa6b-42be-bcfe-ca6338d752a8)

Remove node 4 from the front of queue and visit the unvisited neighbours and push them into queue.
Now, Queue becomes empty, So, terminate these process of iteration.



## Algorithm:
1.Construct a Graph with Nodes and Edges

2.Breadth First Uses Queue and iterates through the Queue for Traversal.

3.Insert a Start Node into the Queue.

4.Find its Successors Or neighbors and Check whether the node is visited or not.

5.If Not Visited, add it to the Queue. Else Continue.

6.Iterate steps 4 and 5 until all nodes get visited, and there are no more unvisited nodes.

## Sample Input:

7 9 

A B 

A C 

A F 

C E 

C F 

C D 

D E 

D G 

G F 

## Sample Output:

['A', 'B', 'C', 'F', 'E', 'D', 'G']


## Sample Input:

5 6 

0 1

0 2 

1 2 

1 3 

2 4 

3 4 

## Sample Output:

['0', '1', '2', '3', '4']

## Program:
```
from collections import deque
from collections import defaultdict

def bfs(graph,start,visited,path):
    queue = deque()
    path.append(start)
    queue.append(start)
    visited[start] = True
    while len(queue) != 0:
        tmpnode = queue.popleft()
        for neighbour in graph[tmpnode]:
            if visited[neighbour] == False:
                path.append(neighbour)
                queue.append(neighbour)
                visited[neighbour] = True
    return path

graph = defaultdict(list)
v,e = map(int,input().split())
for i in range(e):
    u,v = map(str,input().split())
    graph[u].append(v)
    graph[v].append(u)

start = 'A'
path = []
visited = defaultdict(bool)
traversedpath = bfs(graph,start,visited,path)
print(traversedpath)
```
```
from collections import deque
from collections import defaultdict

def bfs(graph,start,visited,path):
    queue = deque()
    path.append(start)
    queue.append(start)
    visited[start] = True
    while len(queue) != 0:
        tmpnode = queue.popleft()
        for neighbour in graph[tmpnode]:
            if visited[neighbour] == False:
                path.append(neighbour)
                queue.append(neighbour)
                visited[neighbour] = True
    return path

graph = defaultdict(list)
v,e = map(int,input().split())
for i in range(e):
    u,v = map(str,input().split())
    graph[u].append(v)
    graph[v].append(u)

start = '0'
path = []
visited = defaultdict(bool)
traversedpath = bfs(graph,start,visited,path)
print(traversedpath)
```
## Output:

![307603268-5360e818-99df-4ee1-a8f0-fc01b9e1037a](https://github.com/Vaishnavi-saravanan/19AI405ExpNo3/assets/118541897/bf8b5894-e5ee-42fc-9d37-ad72686e8c1c)

![307603276-9978ad7d-cbb5-4a26-8754-e7c072027f77](https://github.com/Vaishnavi-saravanan/19AI405ExpNo3/assets/118541897/46409507-6094-42f2-a226-395e4bc6ffc4)

## Result:

Thus,a Graph was constructed and implementation of Breadth First Search for the same graph was done successfully.


