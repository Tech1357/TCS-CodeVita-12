def cost_of_moving_hour_hand(degrees, direction, P, Q):
    if direction == "clockwise":
        if degrees <= 90:
            return degrees * P
        else:
            return (90 * P) + ((degrees - 90) * Q)
    elif direction == "counterclockwise":
        if degrees <= 90:
            return degrees * Q
        else:
            return (90 * Q) + ((degrees - 90) * P)
    return 0

def cost_of_moving_minute_hand(degrees, direction, X, Y):
    if direction == "clockwise":
        if degrees <= 90:
            return degrees * X
        else:
            return (90 * X) + ((degrees - 90) * Y)
    elif direction == "counterclockwise":
        if degrees <= 90:
            return degrees * Y
        else:
            return (90 * Y) + ((degrees - 90) * X)
    return 0

def compute_current_angle(hour, minute):
    # Calculate the angle between the two hands at any given time
    minute_angle = (minute % 60) * 6
    hour_angle = ((hour % 12) * 30) + (minute / 60) * 30
    angle = abs(hour_angle - minute_angle)
    return min(angle, 360 - angle)

def solve():
    # Read the input
    time = input().strip()
    N = int(input().strip())
    A, B = map(int, input().split())
    P, Q = map(int, input().split())
    X, Y = map(int, input().split())
    
    # Parse the initial time
    hour, minute = map(int, time.split(":"))
    
    total_cost = 0
    
    # Process each query
    for _ in range(N):
        angle_needed = int(input().strip())
        
        # Calculate the current angle
        current_angle = compute_current_angle(hour, minute)
        
        # Find the angle differences
        internal_angle = abs(current_angle - angle_needed)
        if internal_angle > 180:
            internal_angle = 360 - internal_angle
        
        external_angle = 360 - internal_angle
        
        # We need to compute the cost to adjust to both angles
        # Move the hour and minute hand in opposite directions, we try both directions:
        
        best_cost = float('inf')
        
        # Move hour hand clockwise, minute hand counterclockwise
        for hour_direction in ["clockwise", "counterclockwise"]:
            for minute_direction in ["clockwise", "counterclockwise"]:
                cost_hour = cost_of_moving_hour_hand(internal_angle, hour_direction, P, Q)
                cost_minute = cost_of_moving_minute_hand(external_angle, minute_direction, X, Y)
                best_cost = min(best_cost, cost_hour + cost_minute)

        # Update the total cost
        total_cost += best_cost
        
        # Update the hands to the final position (calculate the final angle) based on the best_cost calculation here
        pass
        
    # Output the total minimum cost
    print(total_cost)

