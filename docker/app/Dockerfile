FROM node:current-slim
WORKDIR /usr/src/app
ENV WORK_DIR /usr/src/app

# 各種パッケージをインストール
RUN apt-get update && apt-get install -y curl zip unzip vim git gh mariadb-client

# MailHog でメールを受信できるように設定
RUN curl -sSL https://github.com/mailhog/mhsendmail/releases/download/v0.2.0/mhsendmail_linux_amd64 -o mhsendmail \
    && chmod +x mhsendmail \
    && mv mhsendmail /usr/local/bin/mhsendmail

# Git 設定
RUN git config --global user.email "temporary_user@example.com" && git config --global user.name "Temporary User"

# 日本語入力できるように設定
ENV LANG C.UTF-8
ENV LANGUAGE en_US:

# www ディレクトリの中身をクリアするコマンドをコンテナにコピー
COPY clear-data /usr/local/bin/
RUN chmod 755 /usr/local/bin/clear-data

# pnpm をインストール
RUN npm install -g pnpm@latest
