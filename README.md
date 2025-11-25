#best first code 
graph = {
    'S': ['A', 'B'],
    'A': ['C', 'D'],
    'B': ['E'],
    'C': [],
    'D': [],
    'E': ['G'],
    'G': []
}

# Heuristic values (estimated cost to reach goal G)
heuristic = {
    'S': 7,
    'A': 6,
    'B': 4,
    'C': 5,
    'D': 2,
    'E': 3,
    'G': 0
}

def best_first_search(start, goal):
    pq = [(heuristic[start], start)]  # priority queue: (h(n), node)
    visited = set()

    while pq:
        h, node = heapq.heappop(pq)

        if node in visited:
            continue
        
        print(node, end=" ")
        visited.add(node)
        
        if node == goal:
            return
        
        for neigh in graph[node]:
            if neigh not in visited:
                heapq.heappush(pq, (heuristic[neigh], neigh))

# ---- User Input ----
start = input("Enter start node: ")
goal = input("Enter goal node: ")

print("\nBest-First Search Traversal:")
best_first_search(start, goal)
print()
# AI-code
