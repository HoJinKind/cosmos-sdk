all: simd-env

simd-env:
	docker build \
		--build-arg UID=$(shell id -u) \
		--build-arg GID=$(shell id -g) \
		--build-arg COMMIT=$(COMMIT) \
		--build-arg TMVERSION=$(TMVERSION) \
		--build-arg VERSION=$(VERSION) \
		--tag cosmossdk/simd-env \
		-f simd-env/Dockerfile \
		$(shell git rev-parse --show-toplevel)

.PHONY: all simd-env
