FROM registry.cn-hangzhou.aliyuncs.com/strangerbell/node:22-bullseye-slim

# Set the working directory in the container
WORKDIR /app

# Copy package.json, yarn.lock and .npmrc
COPY package.json .npmrc /app/

# 设置 npm registry 为国内镜像并安装依赖
RUN npm config set registry https://registry.npmmirror.com && \
    npm install --verbose

# Copy the current directory contents into the container at /app
COPY ./ /app/

# Expose port 5173 to access the server
EXPOSE 5173

# Command to run the application
CMD ["yarn", "dev", "--host", "0.0.0.0"]
