

Topology of services inside docker-compose


```
                            ++
                            ||
                            ||
                            ||
                            ||
                            ||
 +-----------------+        ||        +-----------------+
 |                 |        ||        |                 |
 |  ss-server      |        ||        |  ss-client      |
 |                 <------------------+                 |
 |                 |        ||        |                 |
 |                 |        ||        |                 |
 +--------^--------+        ||        +-----------------+
          |                 ||
          |                 ||
          |                 ||
          |                 ||
 +--------+--------+        ||        +-----------------+     +-----------------+
 |                 |        ||        |                 |     |                 |
 |  server (kcp)   |        ||        |  kcp-client     |     |  client (ss)    |
 |                 <------------------+                 <-----+                 |
 |                 |        ||        |                 |     |                 |
 |                 |        ||        |                 |     |                 |
 +-----------------+        ||        +-----------------+     +-----------------+
                            ||
                            ||
                            ||
                            ||
                            ||
                            ++
```
