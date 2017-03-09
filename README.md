# docker-node-jekyll

A dockerize node, jekyll and netcat.

Build jekyll with http request.

## docker compose
Below are the default values for environment variables
```yaml
version: "3"

services:
	jekyll:
		environment:
			- LISTEN_PORT=8080
			- JEKYLL_DIR=/data
			- JEKYLL_BUILD=/usr/local/bin/build
		volumes:
			- ./your-own-build-instruction:/usr/local/bin/build
			- ./your-jekyll-directory:/data

```

## Build Script
The default build script builds jekyll in the `JEKYLL_DIR`
```bash
#!/bin/bash

jekyll build

# => The current folder will be generated into ./_site
```

To trigger build, you can request via http. where netcat is listening on `LISTEN_PORT`. Example:
```bash
curl http://jekyll-host:8080
```

## Specs
- debian jessie
- node.js 6.10
- ruby 2.4
- netcat
