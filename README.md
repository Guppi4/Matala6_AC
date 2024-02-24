
**Fragman Budget Allocation Method**

This repository contains a Python implementation of a single step in the Fragman method for budget allocation.  The method allows for a fair and democratic allocation of resources.

**What is the Fragman Method?**

The Fragman method is a participatory budgeting process where citizens vote on their preferred budget items. The method iteratively calculates the minimum cost to elect the next item and distributes that cost proportionally amongst the item's supporters.

**Code Usage**

The core function is `elect_next_budget_item()`. Here's how to use it:

```python
def elect_next_budget_item(votes, balances, costs):
   """Implements one step in the Fragman method. See function docstring for details."""
   # ... implementation ... 
```

**Parameters**

* **votes**: A list of sets, where each set represents a single citizen's preferred items.
* **balances**: A list of floats representing each citizen's remaining balance.
* **costs**:  A dictionary mapping item names to their costs.

**Example**

```python
votes = [{'Park'}, {'Park', 'Library'}, {'Library'}]
balances = [0.0, 0.0, 0.0]
costs = {'Park': 1.0, 'Library': 1.5}

elect_next_budget_item(votes, balances, costs)
```

**Dependencies**

* Python 3.10 

**Additional Notes**

* This implementation demonstrates a single step within the Fragman method. A complete budget allocation process would likely involve multiple iterations of this function.
* For clarity, the example assumes a simple voting system. More complex voting mechanisms could be incorporated.


