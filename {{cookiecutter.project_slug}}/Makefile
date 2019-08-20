{% if cookiecutter.operating_system == 'Linux' %}

VENV_DIR = venv
BIN_DIR = $(VENV_DIR)/bin

IMAGE = jupyter-project
CONTAINER = jupyter


help:
	@grep -E '^[a-zA-Z_-]+:.*?## .*$$' $(MAKEFILE_LIST) | awk 'BEGIN {FS = ":.*?## "}; {printf "\033[36m%-30s\033[0m %s\n", $$1, $$2}'


venv:
	virtualenv -p python3 venv
	$(BIN_DIR)/pip install -r requirements.txt
	$(BIN_DIR)/ipython kernel install --user --name=$(VENV_DIR)
	$(BIN_DIR)/jupyter nbextension install https://github.com/drillan/jupyter-black/archive/master.zip --user
	$(BIN_DIR)/jupyter nbextension enable jupyter-black-master/jupyter-black

launch-local: ## Launch jupyter locally
	if [ ! -d $(VENV_DIR) ]; then make venv; fi;
	$(BIN_DIR)/jupyter notebook

launch-docker: ## Launch jupyter with Docker
	docker build -t $(IMAGE) .
	docker run --rm -d --name $(CONTAINER) -p 8888:8888 -v $(shell pwd):/home $(IMAGE)
	sleep 1.5
	xdg-open http://localhost:8888/tree

clean-docker: ## Clean the list of containers in Docker
	docker stop $(CONTAINER)
	docker rm $(CONTAINER)

update-tree: ## Update your file structure.txt
	tree --dirsfirst -C -I $(VENV_DIR) > structure.txt


{% elif cookiecutter.operating_system == 'Windows' %}

IMAGE = jupyter-project
CONTAINER = jupyter

VENV_DIR = venv
BIN_DIR = .\$(VENV_DIR)\Scripts


venv:
	python -m venv ./venv
	$(BIN_DIR)\pip.exe install -r requirements.txt
	$(BIN_DIR)\ipython.exe kernel install --user --name=$(VENV_DIR)
	$(BIN_DIR)\jupyter-nbextension.exe install https://github.com/drillan/jupyter-black/archive/master.zip --user
	$(BIN_DIR)\jupyter-nbextension.exe enable jupyter-black-master/jupyter-black

launch-local: venv
	$(BIN_DIR)\jupyter-notebook.exe


launch-docker:
	docker build -t $(IMAGE) .
	docker run --rm -d --name $(CONTAINER) -p 8888:8888 -v ${CURDIR}:/home $(IMAGE)
	@echo -------------------------------------------------------------------------------------------------
	@echo You can now navigate to http://localhost:8888/tree to access Jupyter
	@echo -------------------------------------------------------------------------------------------------

clean-docker:
	docker stop $(CONTAINER)

{% endif %}