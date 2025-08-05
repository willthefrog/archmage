FROM archlinux/archlinux:base-devel

# Locale settings
RUN pacman -Syu --noconfirm vim openssh python && pacman -Scc --noconfirm && \
    echo 'en_US.UTF-8 UTF-8' > /etc/locale.gen; locale-gen
ENV LANG=en_US.UTF-8
ENV LANGUAGE=en_US:en
ENV LC_ALL=en_US.UTF-8
RUN useradd -u 1000 -m -p '$PASSWD_HASH$' -G adm,wheel $USER$
COPY wheel /etc/sudoers.d/wheel
RUN ssh-keygen -A
EXPOSE 22
CMD ["/usr/bin/sshd", "-D"]
