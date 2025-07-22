IMAGE_NAME=jamschedule-frontend
CONTAINER_NAME=jamschedule-frontend
PORT=8080

.PHONY: build run stop clean

build:
	docker build -t $(IMAGE_NAME) .

run:
	docker run --rm -p $(PORT):8080 --name $(CONTAINER_NAME) $(IMAGE_NAME)

stop:
	docker stop $(CONTAINER_NAME) || true

clean: stop
	docker rmi $(IMAGE_NAME) || true 