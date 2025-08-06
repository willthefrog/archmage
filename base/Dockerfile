FROM archlinux/archlinux:base-devel

RUN pacman -Syu --noconfirm git openssh ripgrep tmux tree vim wget which \
    ipython python-uv && pacman -Scc --noconfirm \
    && echo 'en_US.UTF-8 UTF-8' > /etc/locale.gen; locale-gen
ENV LANG=en_US.UTF-8
ENV LANGUAGE=en_US:en
ENV LC_ALL=en_US.UTF-8
RUN useradd -u 1000 -m -p '$PASSWD_HASH$' -G adm,wheel $USER$
COPY wheel /etc/sudoers.d/wheel
RUN ssh-keygen -A
EXPOSE 22
RUN echo "ClientAliveInterval 10" >> /etc/ssh/sshd_config && \
    echo "ClientAliveCountMax 6" >> /etc/ssh/sshd_config
CMD ["/usr/bin/sshd", "-D"]
