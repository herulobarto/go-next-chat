postgresinit:
	docker run --name postgres15 \
	-p 5433:5432 \
	-e POSTGRES_USER=root \
	-e POSTGRES_PASSWORD=131113 \
	-d postgres:15-alpine

postgres:
	docker exec -it postgres15 psql -U root -d postgres

createdb:
	docker exec -it postgres15 createdb --username=root --owner=root go-chat

dropdb:
	docker exec -it postgres15 dropdb --username=root go-chat

migrateup:
	migrate -path db/migrations -database "postgresql://root:131113@localhost:5433/go-chat?sslmode=disable" -verbose up

migratedown:
	migrate -path db/migrations -database "postgresql://root:131113@localhost:5433/go-chat?sslmode=disable" -verbose down

.PHONY: postgresinit postgres createdb dropdb migrateup migratedown
