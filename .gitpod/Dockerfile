FROM gitpod/workspace-full
USER root

RUN npm install -g @bazel/bazelisk
RUN npm install -g @bazel/ibazel

RUN mkdir $HOME/bin
RUN npm install -g @bazel/bazelisk
RUN npm install -g @bazel/ibazel

ENV PATH=$PATH:/usr/local/bin/pulumi

ARG CONFTEST_URL="https://github.com/open-policy-agent/conftest/releases/download/v0.32.0/conftest_0.32.0_linux_amd64.deb"
RUN curl -sSL "${CONFTEST_URL}" -o conftest.deb \
    && dpkg -i conftest.deb \
    && rm conftest.deb

ARG AWS_CLI_V2_URL='https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip'
RUN curl "${AWS_CLI_V2_URL}" -o "awscliv2.zip" && \
    unzip awscliv2.zip && \
    ./aws/install

ARG KUBECTL_URL='https://amazon-eks.s3.us-west-2.amazonaws.com/1.20.4/2021-04-12/bin/linux/amd64/kubectl'
RUN curl -o kubectl "${KUBECTL_URL}" && \
    chmod +x kubectl && \
    mv kubectl /usr/local/bin

ARG PULUMI_URL='https://get.pulumi.com/releases/sdk/pulumi-v3.33.2-linux-x64.tar.gz'
RUN curl -o pulumi.tar.gz "${PULUMI_URL}" && \
    mkdir -p /usr/local/bin/pulumi && \
    tar -xf pulumi.tar.gz -C /usr/local/bin/ && \
    rm pulumi.tar.gz && \
    chmod +x /usr/local/bin/pulumi/pulumi

ARG TERRAFORM_URL='https://releases.hashicorp.com/terraform/1.1.6/terraform_1.1.6_linux_amd64.zip'
RUN curl -o terraform.zip "${TERRAFORM_URL}" && \
    unzip terraform.zip && \
    rm terraform.zip && \
    chmod +x terraform && \
    mv terraform /usr/local/bin

ARG YQ_URL='https://github.com/mikefarah/yq/releases/download/v4.18.1/yq_linux_amd64'
RUN curl -o yq "${KUBECTL_URL}" && \
    chmod +x yq && \
    mv yq /usr/local/bin

USER gitpod