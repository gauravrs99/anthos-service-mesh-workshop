# Copyright 2019 Google LLC
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

# Base image
FROM gcr.io/google.com/cloudsdktool/cloud-sdk:alpine

# Install required packages
RUN apk add --no-cache jq python3 openssl curl unzip

# Define versions
ENV TERRAFORM_VERSION=1.5.7
ENV KUBECTL_VERSION=1.27.0
ENV KUSTOMIZE_VERSION=5.0.0
ENV TF_PLUGIN_CACHE_DIR=/workspace/.terraform.d/plugin-cache

# Install Terraform
RUN wget --no-check-certificate https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_linux_amd64.zip && \
    unzip terraform_${TERRAFORM_VERSION}_linux_amd64.zip && \
    chmod +x terraform && mv terraform /usr/local/bin/ && \
    rm -rf terraform_${TERRAFORM_VERSION}_linux_amd64.zip

# Install kubectl
RUN wget --no-check-certificate https://dl.k8s.io/release/v${KUBECTL_VERSION}/bin/linux/amd64/kubectl && \
    chmod +x kubectl && mv kubectl /usr/local/bin/

# Install kustomize
RUN curl -LO https://github.com/kubernetes-sigs/kustomize/releases/download/kustomize/v${KUSTOMIZE_VERSION}/kustomize_v${KUSTOMIZE_VERSION}_linux_amd64.tar.gz && \
    tar -xzf kustomize_v${KUSTOMIZE_VERSION}_linux_amd64.tar.gz && \
    chmod +x kustomize && mv kustomize /usr/local/bin/ && \
    rm -rf kustomize_v${KUSTOMIZE_VERSION}_linux_amd64.tar.gz
