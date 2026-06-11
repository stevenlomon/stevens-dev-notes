# Recursion
When dealing with recursion or path finding, we don't want to worry about the entire graph. It serves us to shift our focus to just two elements: **the current node** and **the target node.**  

At its core, **recursion is programmatic induction.** Thus - just like in Mathematics - we need to trust the inductive hypothesis!  
Our recursive function should only ever look at its immediate surroundings, trusting that if it manages the immediate transition perfectly, the engine will solve the rest of the path.  
***<mark>We don't manage the path, we manage the transition</mark>***  

**Context delegation** is what unlocks infinite scale.  
If we consider a standard depth-first search: `dfs(currentNode, targetNode)`, when a neighbor or `currentNode` steps into the recursive function call:  
* `targetNode` remains the constant objective  
* `currentNode` acts as a dynamic vantage point  

***<mark>targetNode remains the North Star of the entire recursive traversal!</mark>***  

The most vivid brain chemistry altering moment for me when re-visiting [Tideman](https://github.com/stevenlomon/tideman.js) was when the looping index `i` stepped into the shoes of `currentNode`!  
```
function lock_pairs() {
    for (let pair of pairs) {
        // Theoretical check: Start at the loser, try to reach the winner only through "arrows we've already drawn"
        if (dfs(pair.loser, pair.winner) === true) {
            // If we CAN reach the winner from the loser, locking this edge creates a cycle! So we do nothing and skip it.
        } else {
            // No cycle found. Lock it in!
            locked[pair.winner][pair.loser] = true;
        }

        function dfs(currentNode, targetNode) {
            // Base Case: If the node I am standing on IS the target, I found a loop!
            if (currentNode === targetNode) return true;

            for (let i = 0; i < candidate_count; i++) {
                // If `currentNode` points to `i`, meaning `i` is a neighbor..
                if (locked[currentNode][i]) { 
                    // ..we delegate the task to `i`! We ask "hey i, you are now currentNode. Can *you* travel from where you are to targetNode?"
                    if (dfs(i, targetNode)) { // IF `i` now *eventually* reaches `targetNode`..
                        return true; // .. a cycle would be created! Return `true`!
                    }
                }
            }
            
            // Default if no paths lead to the target
            return false; 
        }
    }
};
```
As the code comments suggests, *the task is ***delegated*** to `i`*!  

<mark>*We aren't rewriting code; we are simply shifting the coordinate frame of the observer. The objective stays fixed, but the perspective migrates.</mark>*  
Because every single stack frame executes this exact same micro-logic from a dynamically updated point of view, the system scales effortlessly whether we are traversing 3 nodes or 3 million!

A simple real-life scenario would be to find out which row you are in a massive concert hall!  
The micro-logic is *tap the shoulder of the person in front of you and ask "Hey, what row are you in?"*  
This chain of shoulder-tapping travels all the way down the theater, person by person. Each person is simply ***delegating*** the question to the next. At the front row, we find the base case! "I'm row 1!"  
Now, the signal bubbles back through the crowd. "Alright, then I'm row 2" bubbling all the way back to the person in the row in front of you saying "Turns out I'm row 31". Turns out you're in row 32!  
You didn't count all the rows in the theater. You only had to manage **one simple transition**: tap the shoulder in front of you, wait for the signal to return, and add 1. *The concert hall call-stack solved the rest of the path for you*