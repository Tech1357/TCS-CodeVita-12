import math

def rotate_point(x, y, angle):
    """ Rotate a point (x, y) counterclockwise by the given angle in radians """
    cos_theta = math.cos(angle)
    sin_theta = math.sin(angle)
    return x * cos_theta - y * sin_theta, x * sin_theta + y * cos_theta

def bounding_box(vertices):
    """ Calculate the axis-aligned bounding box for a set of vertices """
    min_x = min(v[0] for v in vertices)
    max_x = max(v[0] for v in vertices)
    min_y = min(v[1] for v in vertices)
    max_y = max(v[1] for v in vertices)
    return (max_x - min_x, max_y - min_y)

def minimal_bounding_rectangle(vertices):
    """ Find the minimal bounding rectangle (MBR) of the convex polygon """
    n = len(vertices)
    min_area = float('inf')
    best_width, best_height = None, None
    
    # Try rotating the polygon by the angle of each edge
    for i in range(n):
        # Get the edge from vertex[i] to vertex[(i+1) % n]
        x1, y1 = vertices[i]
        x2, y2 = vertices[(i + 1) % n]
        
        # Calculate the angle of the edge with respect to the x-axis
        dx = x2 - x1
        dy = y2 - y1
        angle = math.atan2(dy, dx)  # Angle of the edge
        
        # Rotate all the points of the polygon by this angle
        rotated_vertices = [rotate_point(x, y, -angle) for x, y in vertices]
        
        # Calculate the bounding box of the rotated polygon
        width, height = bounding_box(rotated_vertices)
        
        # Check if this bounding box is the smallest we've encountered
        area = width * height
        if area < min_area:
            min_area = area
            best_width, best_height = width, height
    
    # Return the smallest width and height (sorted)
    return (min(best_width, best_height), max(best_width, best_height))

def solve():
    # Read input
    N = int(input())  # Number of vertices
    vertices = []
    
    # Read each vertex
    for _ in range(N):
        x, y = map(float, input().split())
        vertices.append((x, y))
    
    # Find the dimensions of the minimal bounding rectangle
    width, height = minimal_bounding_rectangle(vertices)
    
    # Output the result
    print(f"{int(width)} {int(height)}")

