def max_removals(main_string, substrings, memo):
    if main_string in memo:
        return memo[main_string]
    
    max_removed = 0
    for sub in substrings:
        # Find and remove all occurrences of substring `sub` in `main_string`
        start_idx = main_string.find(sub)
        if start_idx != -1:  # Substring `sub` is found
            # Remove the substring and get the new string
            new_string = main_string[:start_idx] + main_string[start_idx+len(sub):]
            # Recurse on the new string and compute maximum number of removals
            max_removed = max(max_removed, 1 + max_removals(new_string, substrings, memo))
    
    memo[main_string] = max_removed
    return max_removed

def solve():
    N = int(input())  # number of substrings
    substrings = input().split()  # list of substrings
    main_string = input().strip()  # the main string
    
    # Memoization dictionary
    memo = {}
    
    # Call the recursive function and print the result
    result = max_removals(main_string, substrings, memo)
    print(result)

