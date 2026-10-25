# Field notes: Relay

**Dijkstra search, augmented state and path reconstruction**

## State changes the shortest-path question

Dijkstra’s algorithm finds minimum-cost paths when edge costs are nonnegative. A programming puzzle may add rules that ordinary node-only visitation cannot represent. If a route must visit checkpoints and has a limited number of shuttle rides, those facts become part of the search state.

Represent a state as `(node, checkpoint_mask, shuttle_count)`. Traversing an edge updates the node, possibly sets a checkpoint bit, and increments the shuttle count when appropriate. Reject states that exceed the ride limit. A priority queue explores states by accumulated cost. Keep predecessor information to reconstruct the ordered edge IDs once the destination is reached with all required checkpoints.

Hash the route identifiers exactly as documented. The unique optimum is important: if two paths tie, the final decryption key would be ambiguous. Positive edge costs ensure a shortest route never needs a pointless cycle.

Learning reference: [Python heap queue documentation](https://docs.python.org/3/library/heapq.html).

---
*AIRANGE Learning Lab · Medium · Use authorized challenge files only.*
