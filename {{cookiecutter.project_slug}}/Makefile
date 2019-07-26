SHELL := /bin/bash

install requirements:
	pip3 install -r requirements.txt

createvenv:
	virtualenv -p python3 venv

#activatevenv:
#	source venv/bin/activate

launchdocker:
	docker build -t jupyter-project .
	docker run -d -it --name jupyter -p 8888:8888 -v $(shell pwd):/home jupyter-project
	sleep 1
	xdg-open http://localhost:8888/tree

stopdocker:
	docker stop jupyter
	docker rm jupyter
