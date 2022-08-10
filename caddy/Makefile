
build:
	docker build -t ptrdin/caddy:latest .

push:
	docker push ptrdin/caddy:latest

run:
	#docker network create caddy_proxy
	docker run --rm -it \
		--name caddy_proxy \
		-p 443:443 -p 80:80 -p 2019:2019 \
		-e DOMAIN=loc.alho.st \
		-v /run/docker.sock:/run/docker.sock \
		--network caddy_proxy \
		-v $(pwd)/data:/data \
		ptrdin/caddy:latest

echo:
	docker run --rm -it --net caddy_proxy \
		--name echo \
		--label virtual.port=80 \
		svendowideit/echo