# FastChat Helm Chart

This Helm chart allows for a straightforward deployment of the FastChat platform on your Kubernetes Cluster. Designed for those aiming to train, serve, and evaluate large language model-based chatbots with ease, this Helm chart is your one-stop solution.

**Prerequisites:** Your Kubernetes Cluster should be compatible with GPU nodes.

## Quick Links:

- [FastChat GitHub Repository](https://github.com/lm-sys/FastChat)
- [Default Docker Image](https://hub.docker.com/repository/docker/gmougeolle/fastchat/)

## Quickstart

1. **Clone the Repository**

    Start by cloning the repository to your local machine:

    ```bash
    git clone https://github.com/gmougeolle/fastchat-helm
    cd <repository-dir>
    ```

    Replace `<repository-dir>` with the name of the directory.

2. **Configure Your Deployment**

    Modify the `values.yaml` file to suit your deployment. This file contains configuration parameters like enabling the webserver, API, controller, and model worker, among others. 

    - Set up the web server, API, and controller:
        - Enable or disable with the `enabled` field.
        - Adjust `replicas` to specify the number of pod replicas.
        - Use `extraParams` to pass any additional parameters.

    - For the model worker:
        - Specify the GPU brand with `gpuBrand`.
        - Define GPU limits using `gpuLimit`.
        - Determine the model path with `modelPath`.

    - Set up the persistent volume claim (PVC) for models with `storageRequest`.

3. **Deploy FastChat**

    With the Helm chart and values configured, deploy FastChat:

    ```bash
    helm install fastchat-helm ./ -f values.yaml
    ```

4. **Access the Deployment**

    If ingress is enabled in the `values.yaml` file, you can access the deployment using the specified hostname.

## Values Overview:

- **Webserver**: Configure the FastChat webserver settings.
- **API**: Set up the FastChat API parameters.
- **Controller**: Define the FastChat controller parameters.
- **ModelWorker**: Specify the FastChat model worker settings, including GPU configurations.
- **PVC**: Adjust the storage request for the models PVC.

## Versioning:

- **Chart Version**: 0.1.0
- **App Version**: 0.1.0

Make sure to refer to the official [FastChat GitHub Repository](https://github.com/lm-sys/FastChat) for any additional information or updates.

**Note**: Ensure that you have the necessary privileges to deploy on your Kubernetes Cluster and always test in a staging environment before deploying to production.