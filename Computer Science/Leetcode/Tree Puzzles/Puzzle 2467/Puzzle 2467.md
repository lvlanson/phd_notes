## Most Profitable Path in a Tree

There is an undirected tree with `n` nodes labeled from `0` to `n - 1`, rooted at node `0`. You are given a 2D integer array `edges` of length `n - 1` where `edges[i] = [ai, bi]` indicates that there is an edge between nodes `ai` and `bi` in the tree.

At every node `i`, there is a gate. You are also given an array of even integers amount, where `amount[i]` represents:

- the price needed to open the gate at node `i`, if `amount[i]` is negative, or,
- the cash reward obtained on opening the gate at node `i`, otherwise.

The game goes on as follows:

- Initially, Alice is at node `0` and Bob is at node `bob`.
- At every second, Alice and Bob each move to an adjacent node. Alice moves towards some leaf node, while Bob moves towards node `0`.
- For **every** node along their path, Alice and Bob either spend money to open the gate at that node, or accept the reward. Note that:
	 - If the gate is **already open**, no price will be required, nor will there be any cash reward.
	- If Alice and Bob reach the node **simultaneously**, they share the price/reward for opening the gate there. In other words, if the price to open the gate is `c`, then both Alice and Bob pay `c / 2` each. Similarly, if the reward at the gate is `c`, both of them receive `c / 2` each.
- If Alice reaches a leaf node, she stops moving. Similarly, if Bob reaches node `0`, he stops moving. Note that these events are **independent** of each other.

Return the **maximum** net income Alice can have if she travels towards the optimal leaf node.

#### Example 1
![[Pasted image 20250224120856.png]]

```
Input: edges = [[0,1],[1,2],[1,3],[3,4]], bob = 3, amount = [-2,4,2,-4,6]
Output: 6
```
Explanation: 
The above diagram represents the given tree. The game goes as follows:
- Alice is initially on node 0, Bob on node 3. They open the gates of their respective nodes.
  Alice's net income is now -2.
- Both Alice and Bob move to node 1. 
  Since they reach here simultaneously, they open the gate together and share the reward.
  Alice's net income becomes -2 + (4 / 2) = 0.
- Alice moves on to node 3. Since Bob already opened its gate, Alice's income remains unchanged.
  Bob moves on to node 0, and stops moving.
- Alice moves on to node 4 and opens the gate there. Her net income becomes 0 + 6 = 6.
Now, neither Alice nor Bob can make any further moves, and the game ends.
It is not possible for Alice to get a higher net income.

#### Example 2
![[Pasted image 20250224120953.png]]

```
Input: edges = [[0,1]], bob = 1, amount = [-7280,2350]
Output: -7280
```
Explanation: 
Alice follows the path 0->1 whereas Bob follows the path 1->0.
Thus, Alice opens the gate at node 0 only. Hence, her net income is -7280. 

--- 

## My Solution

```go
func mostProfitablePath(edges [][]int, bob int, amount []int) int {
    pathMap := make(map[int][]int, 0)
    max     := 0
    for _, edge := range edges{
        if edge[0] > max{
            max = edge[0]
        }
        if edge[1] > max{
            max = edge[1]
        }
        pathMap[edge[0]] = append(pathMap[edge[0]], edge[1])
        pathMap[edge[1]] = append(pathMap[edge[1]], edge[0])
 
    }

    /* Building Bobs Path, because it is deterministic going from node bob to node 0 */
    bobsPath       := []int{bob}                        // bobs path is predetermined and is contained here
    bobVisited     := make([]bool, max+1, max+1)        // helper structure for building bobs path
    bobVisited[bob] = true                              // initial position is already visited
    buildBobsPath(bob, pathMap, &bobsPath, &bobVisited) // building bobs path

    /* Preparing helper variables for finding optimal alice path */
    bobVisited        = make([]bool, max+1, max+1)      // if Bob visits `node`, it will be turned true at `bobvisited[node] = true`
                                                        // indicating the reward has been reaped already
    aliceVisited     := make([]bool, max+1, max+1)      // same for Alice
    aliceVisited[0]   = true                            // initial position has been visited
    bobVisited[bob]   = true                            // initial position has reward reaped
    rewardAlice      := amount[0]                       // Alice initial position is base reward
    collectedRewards := make([]int, 0)                  // keeping track of all collected rewards during recursion
    
    /* Building Alice Path */
    checkAlicePath(0, 0, pathMap, &bobsPath, &bobVisited, &amount, &rewardAlice, &collectedRewards, &aliceVisited)

    maxReward := collectedRewards[0]
    for _, reward := range collectedRewards[1:]{
        if reward > maxReward{
            maxReward = reward
        }
    }
    return maxReward
}

func checkAlicePath(pos int, stepBob int, pathMap map[int][]int, bobsPath *[]int, rewardUsed *[]bool, amount *[]int, reward *int, collectedRewards *[]int, aliceVisited *[]bool){
    if nodes, _ := pathMap[pos]; len(nodes) == 1 && (*aliceVisited)[nodes[0]]{
        (*collectedRewards) = append((*collectedRewards), *reward)  
        return
    }else{
        bobMoved := false
        bobsNode := 0
        // if Bob can do a step
        if stepBob < len((*bobsPath))-1{
            bobMoved = true
            stepBob++
            bobsNode = (*bobsPath)[stepBob]
            flipReward(bobsNode, rewardUsed)
        }
        
        for _, next := range nodes{
            
            if (*aliceVisited)[next]{               // if alice has visited a node, take next node
                continue
            }

            
            (*aliceVisited)[next] = true            // mark node as visited
            addedReward := 0
            if bobMoved && bobsNode == next{        // if bob and alice vist node at same time
                addedReward = (*amount)[next]/2
            }else if !(*rewardUsed)[next]{          // if bob has not reaped reward yet
                addedReward = (*amount)[next]
            }
            *reward += addedReward                  // add reward for current path     
            checkAlicePath(next, stepBob, pathMap, bobsPath, rewardUsed, amount, reward, collectedRewards, aliceVisited)
            *reward -= addedReward                  // remove reward for next path
            (*aliceVisited)[next] = false           // remove visit mark
        }

        if bobMoved{ // cleanup after end of paths, each possible next step had a move of bob before
            flipReward(bobsNode, rewardUsed)
        }
        
    }
}

func flipReward(node int, rewardUsed *[]bool){
    (*rewardUsed)[node] = !(*rewardUsed)[node]
}

func buildBobsPath(pos int, pathMap map[int][]int, bobsPath *[]int, bobVisited *[]bool) bool{
    if pos == 0{
        return true
    }
    if nodes, ok := pathMap[pos]; !ok{
        return false
    }else{
        for _, next := range nodes{
            if (*bobVisited)[next]{
                continue
            }
            (*bobVisited)[next] = true
            (*bobsPath) = append((*bobsPath), next)
            if buildBobsPath(next, pathMap, bobsPath, bobVisited){
                return true
            }
            (*bobVisited)[next] = false
            (*bobsPath) = (*bobsPath)[:len((*bobsPath))-1]
        }
    }
    return false
}


```