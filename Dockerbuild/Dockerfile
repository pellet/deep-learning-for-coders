FROM rocm/pytorch:latest
LABEL Ben Pettit <ben.pettit@digimulti.com>

RUN apt-get update -y

COPY fastsetup/setup-conda.sh /tmp

RUN /tmp/setup-conda.sh

COPY requirements.txt /tmp

RUN /root/mambaforge/bin/conda install -c fastchan fastai
RUN python3 -m pip install --upgrade pip \
    && python3 -m pip install --upgrade --force-reinstall -r /tmp/requirements.txt

WORKDIR /files

CMD ["jupyter", "notebook", "--allow-root", "--port=1337", "--ip=0.0.0.0"]
