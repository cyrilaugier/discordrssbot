FROM docker.io/alpine@sha256:0a4eaa0eecf5f8c050e5bba433f58c052be7587ee8af3e8b3910ef9ab5fbe9f5

ARG USERNAME=vscode

RUN mkdir /etc/skell
COPY bashrc /etc/skell/.bashrc
COPY profile /etc/skell/.profile

RUN apk add git --no-cache
RUN apk add bash bash-completion

RUN apk add shadow sudo --no-cache \
    && useradd -m -s /bin/bash -k /etc/skell "$USERNAME" \
    && echo $USERNAME "ALL=(root) NOPASSWD:ALL" > "/etc/sudoers.d/$USERNAME" \
    && chmod 0440 "/etc/sudoers.d/$USERNAME" \
    && visudo -c "/etc/sudoers.d/$USERNAME"

RUN echo "devcontainer" > /etc/alpine_chroot

USER "$USERNAME"
