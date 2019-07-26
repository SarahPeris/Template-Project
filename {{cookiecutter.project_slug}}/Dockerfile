FROM python:3

ADD requirements.txt .
RUN pip install -r requirements.txt
WORKDIR /home

ENTRYPOINT ["bash", "-c", "source /etc/bash.bashrc && jupyter notebook --ip 0.0.0.0 --no-browser --allow-root --NotebookApp.token='' --NotebookApp.password=''"]