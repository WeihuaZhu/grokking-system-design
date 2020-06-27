# grokking-system-design
repo for reviewing and learning system design concepts and applications
based on course https://www.educative.io/courses/grokking-the-system-design-interview

## system design basics
- what are different architectural pieces that can be used?
- how do the pieces work together?
- what are the right trade-offs?

## Load Balancing (LB)
we can add LBs in 3 places:
- between user and web server
- between web servers and an internal platform layer (application servers/cache servers)
- between internal platform layer and db

### smart clients
take a pool of service hosts and do LB across them, also detects dead hosts, recovered hosts and deal with adding new hosts.  
It is easy to implement and manage when the system is not large, but as system grows, LBs need to be evolved into standalone servers.

### hardware LB
The most expensive and with very high performance, non-trivial to configure. So companies would avoid using dedicated hardware for all their LB needs.

### software LB
Hybrid approach. e.g. HAProxy, nginx. For most systems, we should start with a software LB and move to smart client or HW LB as need arises.

## Caching
- Cache takes advantage of the locality of refrence principle: recently requested data is likely to be requested again.
- Caching can exist at all levels in architecture but are often found at the level nearest to the frontend, where they are implemented to return data quickly without taxing downstream levels.

### Application server cache
