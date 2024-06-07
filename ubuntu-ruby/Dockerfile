# ベースイメージとして最新のUbuntuを使用
FROM ubuntu:latest

# システムの更新と必要なパッケージのインストール
RUN apt update && \
    apt install -y \
    curl \
    git \
    build-essential \
    libssl-dev \
    libreadline-dev \
    zlib1g-dev \
    sudo

# ユーザーの作成
RUN useradd -m -s /bin/bash rbenvuser && echo "rbenvuser ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

# 新しいユーザーに切り替え
USER rbenvuser
WORKDIR /home/rbenvuser

# rbenvとruby-buildのインストール
RUN git clone https://github.com/rbenv/rbenv.git /home/rbenvuser/.rbenv && \
    git clone https://github.com/rbenv/ruby-build.git /home/rbenvuser/.rbenv/plugins/ruby-build

# 環境変数の設定
ENV PATH /home/rbenvuser/.rbenv/bin:/home/rbenvuser/.rbenv/shims:$PATH
RUN echo 'export PATH="/home/rbenvuser/.rbenv/bin:$PATH"' >> /home/rbenvuser/.bashrc && \
    echo 'eval "$(rbenv init -)"' >> /home/rbenvuser/.bashrc

# rbenvを使ってRubyをインストール
RUN /bin/bash -c "source /home/rbenvuser/.bashrc && CONFIGURE_OPTS=--disable-install-doc rbenv install 3.1.0 && rbenv global 3.1.0"

# Bundlerのインストール
RUN /bin/bash -c "source /home/rbenvuser/.bashrc && gem install bundler"

# 環境変数の設定
ENV PATH /home/rbenvuser/.rbenv/versions/3.1.0/bin:$PATH

# 作業ディレクトリの設定
WORKDIR /app

# ポートの公開
EXPOSE 3000

# Dockerコンテナの起動時に実行するコマンド
# CMD ["irb"]

