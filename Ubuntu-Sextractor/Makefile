include .env


all: build test deploy clean

build: clean
	DOCKER_BUILDKIT=1 docker build \
		--no-cache --network=host -f Dockerfile

test: clean
	docker-compose -f test.yml up --exit-code-from test

deploy: clean

clean:
	docker container prune -f
	docker image prune -f
