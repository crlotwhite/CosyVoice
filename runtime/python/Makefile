PROJECT_NAME=cosyvoice
VERSION=v1.0
MODEL_DIR=iic/CosyVoice2-0.5B
MODE=zero_shot
SERVICE=grpc
PORT=50000
MAX_CONC=4

.PHONY: all build run

all: build run

build:
	docker build -t cosyvoice:$(VERSION) .

run:
	docker run -d --runtime=nvidia \
	           -p $(PORT):$(PORT) \
	           cosyvoice:$(VERSION) \
	           /bin/bash -c "cd /opt/$(PROJECT_NAME)/$(PROJECT_NAME)/runtime/python/$(SERVICE) && python3 server.py --port $(PORT) --max_conc $(MAX_CONC) --model_dir $(MODEL_DIR) && sleep infinity"
