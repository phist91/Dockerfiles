# Jonas Becker's very own Docker container for testing purposes made for the
# project course "Geometriebasierte Entscheidungsunterstützung in der
# forensischen Chemometrie", winter semester 2019/20.

FROM agv-texlive:latest
LABEL maintainer="p.st@wwu.de"

# Installing JDK 11 and Maven
RUN apt-get update -y \
    && apt-get install -y openjdk-11-jdk maven

# Installing SSH server
RUN apt-get install -y openssh-server \
    && adduser becker --gecos "Becker Box,702,38411,38401" --disable-password \
	&& echo "becker:becker" | chpasswd \
    && mkdir /var/run/sshd \
    && sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd \
    && echo "export VISIBLE=now" >> /etc/profile \
	&& (crontab -l 2>/dev/null; echo "@reboot /usr/bin/sshd -D") | crontab -
EXPOSE 22
CMD gitlab-runner start && /usr/bin/sshd -D && bash
