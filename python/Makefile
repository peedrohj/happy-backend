$(shell echo UID=$(shell id -u) > .env)

# build containers
build:
	docker-compose -f docker-compose.yml build

# Run development containers
run-dev:
	docker-compose -f docker-compose.yml up db app

# Run all containers in detached mode
run-dev-d:
	docker-compose -f docker-compose.yml up -d db app

# Run database in detached mode
run-db:
	docker-compose -f docker-compose.yml up -d db

# Stop all containers
stop-all:
	docker-compose -f docker-compose.yml stop

# Removes all containers
remove-all:
	docker rm db app-django

# Removes db and db's data
remove-db:
	docker rm db && docker volume rm python-boilerplate_db_data