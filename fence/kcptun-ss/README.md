

Topology of services inside docker-compose


```
                            ++
                            ||
                            ||
                            ||
 +-----------------+        ||        +-----------------+
 |                 |        ||        |                 |
 |  ss-server      |        ||        |  ss-client      |
 |                 <------------------+                 |                            --- (a)
 |                 |        ||        |                 |
 |          :30000 |        ||        |          :60000 |
 +--------^--------+        ||        +-----------------+
          |                 ||
          |                 ||
          |                 ||
          |                 ||
 +--------+--------+        ||        +-----------------+     +-----------------+
 |                 |        ||        |                 |     |                 |
 |  server (kcp)   |        ||        |  kcp-client     |     |  client (ss)    |
 |                 <------------------+                 <-----+                 |    --- (b)
 |                 |        ||        |                 |     |                 |
 |          :31000 |        ||        |          :61000 |     |          :60000 |
 +-----------------+        ||        +-----------------+     +-----------------+
                            ||
                            ||
                            ||
                            ++
```





## Step 0 - Config

> Do this on both remote and local

```bash
cp env.example .env
```

Open `.env` file (NOT the `env.example`) with you favorite editor, change:

- `PASSWORD` to new one
- `ENDPOINT` to your server's IP or domain





## Step 1 - Start Remote

> Do this on remote only

```bash
docker-compose up -d server
```





## Step 2 (b) - Start Local

> Do this on local only

```bash
docker-compose up -d client
```





## Step 2 (a) - Start Local w/o Kcptun

> Do this on local only

```bash
docker-compose up -d ss-client
```





## Step 3 - Test

```bash
curl -x socks5h://localhost:60000 -I https://www.google.com
```
