$(shell echo UID=$(shell id -u) > .env)

build:
	docker-compose build app

run-dev:
	docker-compose up app

shell:
	docker-compose exec app bash