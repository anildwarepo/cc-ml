FROM mcr.microsoft.com/azureml/openmpi4.1.0-ubuntu20.04
 
ENV AZUREML_CONDA_ENVIRONMENT_PATH /azureml-envs/azureml-automl
ENV PATH $AZUREML_CONDA_ENVIRONMENT_PATH/bin:$PATH
 
COPY --from=mcr.microsoft.com/azureml/mlflow-ubuntu20.04-py38-cpu-inference:20230306.v3 /var/mlflow_resources/mlflow_score_script.py /var/mlflow_resources/mlflow_score_script.py

WORKDIR /app
COPY requirements.txt /app/

ENV MLFLOW_MODEL_FOLDER="mlflow-model"
# ENV AML_APP_ROOT="/var/mlflow_resources"
# ENV AZUREML_ENTRY_SCRIPT="mlflow_score_script.py"
 
ENV ENABLE_METADATA=true
 
# begin conda create
# Create conda environment
RUN conda create -p $AZUREML_CONDA_ENVIRONMENT_PATH \
    python=3.10 \
    pip=24.0 \
#    numpy \
#    tensorflow=2.16.1 \
#    pandas \
#    joblib=1.4.2 \
    -c conda-forge -y && \
    conda clean -a -y

# end conda create
 
# Install pip dependencies
#RUN pip install  \
#                # begin pypi dependencies
#                'azureml-inference-server-http' 
#RUN pip install Flask==2.1.2 Werkzeug==2.0.3
                
                # end pypi dependencies
# end pip install
RUN pip install -r requirements.txt