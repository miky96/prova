# Base image
FROM continuumio/anaconda3

# Comandes que s'executaran dins de la imatge com instalar un Debian, llibreries i jupyter via el pip...

RUN apt-get update && apt-get install -y libgtk2.0-dev && \
    rm -rf /var/lib/apt/lists/* && \
    /opt/conda/bin/conda install jupyter -y && \
    /opt/conda/bin/conda install numpy pandas scikit-learn pydot matplotlib seaborn pyyaml h5py keras -y && \
    /opt/conda/bin/conda upgrade dask && \
    pip install tensorflow imutils

RUN mkdir /Engine_AI
RUN mkdir /tmp/tflearn_logs

COPY jupyter_notebook_config.py /root/.jupyter/
COPY run_jupyter.sh /

# Jupyter and Tensorboard ports
EXPOSE 8888 6006

# Store notebooks in this mounted directory
VOLUME ["/Engine_AI", "/tmp/tflearn_logs"]

CMD ["/run_jupyter.sh"]
