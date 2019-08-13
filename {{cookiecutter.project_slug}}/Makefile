VENV_DIR = venv
BIN_DIR = $(VENV_DIR)/bin

IMAGE = jupyter-project
CONTAINER = jupyter


help:
	@grep -E '^[a-zA-Z_-]+:.*?## .*$$' $(MAKEFILE_LIST) | awk 'BEGIN {FS = ":.*?## "}; {printf "\033[36m%-30s\033[0m %s\n", $$1, $$2}'

venv:
	virtualenv -p python3 venv
	$(BIN_DIR)/pip install -r requirements.txt
	$(BIN_DIR)/jupyter nbextension install https://github.com/drillan/jupyter-black/archive/master.zip --user
	$(BIN_DIR)/jupyter nbextension enable jupyter-black-master/jupyter-black

launch-local: ## Launch jupyter locally
	if [ ! -d $(VENV_DIR) ]; then make venv; fi;
	$(BIN_DIR)/jupyter notebook

launch-docker: ## Launch jupyter with Docker
	docker build -t $(IMAGE) .
	docker run --rm -d -it --name $(CONTAINER) -p 8888:8888 -v $(shell pwd):/home $(IMAGE)
	sleep 1.5
	xdg-open http://localhost:8888/tree

clean-docker: ## Clean the list of containers in Docker
	docker stop $(CONTAINER)
	docker rm $(CONTAINER)

update-tree: ## Update your file structure.txt
	tree --dirsfirst -C -I $(VENV_DIR) > structure.txt
