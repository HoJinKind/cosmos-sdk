all: simd-env

simd-env:
	docker build \
		--volume $(shell git rev-parse --show-toplevel):/work
		--build-arg UID=$(shell id -u) \
		--build-arg GID=$(shell id -g) \
		--tag cosmossdk/simd-env simd-env

.PHONY: all simd-env
