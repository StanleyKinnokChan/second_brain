# Find Nearest

**Configuration:**

- **Two Input**
    - list of Point objects or poly-object (then centroid will be used)
    - T anchor: for each object in this, you are finding the closest place in the  U anchor
    - U anchor: the object close to your target

        [[Find Nearest/Untitled.png]]

- **How many nearest points to find? (let’s say N)**
    - for each object in T, return N nearest U object
- **Maximum distance:**
    - Objects won’t be returned if the distance out of this distance (like a filter)
    - the distance can be customized by double click the numbers
