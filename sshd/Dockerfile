FROM alpine:3.6

MAINTAINER Justin.h<justin@5nas.cc>

ENV ROOT_PASSWORD root

RUN apk --update add openssh \
		&& sed -i s/#PermitRootLogin.*/PermitRootLogin\ yes/ /etc/ssh/sshd_config \
		&& echo "root:${ROOT_PASSWORD}" | chpasswd \
		&& rm -rf /var/cache/apk/* /tmp/*

COPY entrypoint-sshd.sh /usr/local/bin/
RUN chmod +x /usr/local/bin/entrypoint-sshd.sh

EXPOSE 22

ENTRYPOINT ["entrypoint-sshd.sh"]
