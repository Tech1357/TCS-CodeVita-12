def get_intersection(wire1, wire2):
    # This function checks if two wires intersect and returns the intersection point
    x1, y1, x2, y2 = wire1
    x3, y3, x4, y4 = wire2
    # Horizontal or vertical wire segments only, assuming that wires are either horizontal or vertical
    if x1 == x2 and x3 == x4:  # both are vertical
        if x1 == x3 and min(y1, y2) <= y3 <= max(y1, y2) and min(y3, y4) <= y1 <= max(y3, y4):
            return (x1, y1)  # intersect at vertical point
    elif y1 == y2 and y3 == y4:  # both are horizontal
        if y1 == y3 and min(x1, x2) <= x3 <= max(x1, x2) and min(x3, x4) <= x1 <= max(x3, x4):
            return (x1, y1)  # intersect at horizontal point
    return None

def calculate_voltage(wires):
    intersections = {}
    for i in range(len(wires)):
        for j in range(i + 1, len(wires)):
            intersection = get_intersection(wires[i], wires[j])
            if intersection:
                if intersection not in intersections:
                    intersections[intersection] = []
                intersections[intersection].append(i)
                intersections[intersection].append(j)
    
    total_voltage = 0
    for intersection, wire_indices in intersections.items():
        num_wires = len(set(wire_indices))  # Count unique wires intersecting at this point
        min_cells = min([abs(wires[i][1] - wires[i][3]) for i in wire_indices])  # Calculate minimum cells
        voltage_at_intersection = num_wires * min_cells
        total_voltage += voltage_at_intersection
    
    return total_voltage

def solve():
    # Read the input
    N = int(input())  # number of wires
    wires = []
    for _ in range(N):
        wires.append(list(map(int, input().split())))
    
    # Read the animal voltage resistance thresholds
    animals = input().split()
    animal_thresholds = {}
    for animal in animals:
        name, threshold = animal.split(":")
        animal_thresholds[name] = int(threshold)
    
    # Read the name of the animal that touched the fence
    animal_that_touched = input().strip()

    # Calculate total voltage
    total_voltage = calculate_voltage(wires)
    
    # Determine if the animal that touched the fence dies
    if animal_thresholds[animal_that_touched] < total_voltage:
        print("Yes")
    else:
        print("No")
    
    # Calculate the probability of animal death
    death_count = sum(1 for threshold in animal_thresholds.values() if threshold < total_voltage)
    total_animals = len(animal_thresholds)
    probability = death_count / total_animals
    print(f"{probability:.2f}")

