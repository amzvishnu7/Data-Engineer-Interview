## Visa Skill Test - Python 

#### Q1. Server Selection
Some developers want to deploy their application on different servers with a load balancer in the front. 
There are n servers to choose from where the number of requests that can be handled by the ith server is server[i].
The number of requests served by any server is a power of 2 i.e. 1, 2, 4, 8, 16,...etc.

Given the array server and an integer expected_load, find the minimum number of servers that must be chosen such that the
total sum of requests served by all the chosen servers is exactly equal to the expected_load. 
If there is no combination of servers that can serve exactly expected load requests, report -1 as the answer.

**Example**

Suppose n = 4, servers = [1, 1, 2, 4], and expected_load = 3.

It is optimal to choose the first and the third or the second and the third servers serving a total of 1 + 2 = expected_load = 3 requests. 
Return the minimum number of servers needed, 2.

**Function Description:**

Complete the function getMinServers in the editor below.
The function getMinServers has the following parameter: 
int expected_load: the number of requests to be served int server[n]: the number of requests the servers can serve

Return
int: the minimum number of servers such that the sum of the total requests they can serve is exactly expected_load

```python
def getMinServers(expected_load, server):
    server.sort(reverse=True) 
    servers_selected = 0 
    total_capacity = 0 
    for i in range(len(server)):
        if expected_load == 0: 
            return servers_selected
        if server[i] > expected_load: 
            continue
        while server[i] <= expected_load: 
            expected_load -= server[i]
            total_capacity += server[i]
            servers_selected += 1
            if expected_load == 0:
                return servers_selected
    return -1 

