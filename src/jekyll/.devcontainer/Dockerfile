# [Choice] Debian OS version (use 2.7-bullseye on local arm64/Apple Silicon): 2.7-bullseye, 2.7-buster
ARG VARIANT=2.7-bullseye
FROM mcr.microsoft.com/devcontainers/ruby:${VARIANT}

USER root

# ENV Variables required by Jekyll
ENV LANG=en_US.UTF-8 \
    LANGUAGE=en_US:en \
    TZ=Etc/UTC \
    LC_ALL=en_US.UTF-8 \
    LANG=en_US.UTF-8 \
    LANGUAGE=en_US

# Install bundler, latest jekyll, and github-pages for older jekyll
RUN gem update --system
RUN gem install bundler jekyll github-pages

RUN chown -R "vscode:rvm" "/usr/local/rvm/" \
    && chmod -R g+r+w "/usr/local/rvm/" \
    && find "/usr/local/rvm/" -type d | xargs -n 1 chmod g+s

COPY post-create.sh /usr/local/post-create.sh

# [Optional] Uncomment this section to install additional OS packages.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>

# [Optional] Uncomment this line to install global node packages.
# RUN su vscode -c "source /usr/local/share/nvm/nvm.sh && npm install -g <your-package-here>" 2>&1
