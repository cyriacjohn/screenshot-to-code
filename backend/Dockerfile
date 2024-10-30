FROM registry.cn-hangzhou.aliyuncs.com/strangerbell/python:3.12.3-slim-bullseye

ENV POETRY_VERSION 1.4.1

# 使用阿里云镜像源安装 Poetry 包管理工具
RUN pip install -i https://mirrors.aliyun.com/pypi/simple/ poetry

# Set work directory
WORKDIR /app

# 复制项目依赖文件到容器中的 /app 目录
COPY ./poetry.lock ./pyproject.toml /app/

# 配置 Poetry 源并重新生成 lock 文件
RUN poetry config virtualenvs.create false && \
    poetry source add --priority=primary aliyun https://mirrors.aliyun.com/pypi/simple/ && \
    poetry lock --no-update

# 安装依赖
RUN poetry install --no-interaction --no-ansi --no-cache

# Copy the current directory contents into the container at /app
COPY ./ /app/
