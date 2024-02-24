def elect_next_budget_item(votes, balances, costs):
    """
    Implements one step of the Fragman method for budget allocation.

    Args:
        votes: A list of sets, where each set represents a citizen's preferred items.
        balances: A list of floats representing each citizen's remaining balance.
        costs: A dictionary mapping item names to their costs.

    Prints:
        - The amount of additional balance added to each supporting citizen.
        - The elected item.
        - The updated balances of all citizens.
    """

    # Find the item with the minimum additional balance needed for election
    min_additional_balance = float('inf')
    item_to_elect = None
    for item, cost in costs.items():
        total_current_balance = sum(balances[i] for i, vote in enumerate(votes) if item in vote)
        additional_balance_needed = cost - total_current_balance
        if 0 < additional_balance_needed < min_additional_balance:
            min_additional_balance = additional_balance_needed
            item_to_elect = item

    # If no item can be elected, inform and return
    if item_to_elect is None:
        print("No item can be elected with the current balances.")
        return

    # Calculate the additional balance needed per supporting citizen
    citizens_supporting = sum(1 for vote in votes if item_to_elect in vote)
    if citizens_supporting == 0: 
        print("No citizens support the item to be elected.")
        return

    additional_per_citizen = min_additional_balance / citizens_supporting

    # Update balances and elect the item
    for i, vote in enumerate(votes):
        if item_to_elect in vote:
            balances[i] += additional_per_citizen
            balances[i] = round(balances[i], 2)  # Round balances for clarity

    # Print the results
    print(f'After adding {additional_per_citizen:.2f} to each supporting citizen, "{item_to_elect}" is chosen.')
    for i, balance in enumerate(balances):
        print(f'Citizen {i+1} has {balance:.2f} remaining balance.') 

# Example usage
votes = [{'Park'}, {'Park', 'Library'}, {'Library'}]
balances = [0.0, 0.0, 0.0]
costs = {'Park': 1.0, 'Library': 1.5}

elect_next_budget_item(votes, balances, costs)
