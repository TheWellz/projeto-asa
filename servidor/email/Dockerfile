FROM ubuntu:latest

RUN apt-get update -y && apt-get upgrade -y && apt-get update

RUN apt install -y postfix
RUN apt install -y postfix dovecot-imapd dovecot-pop3d

RUN apt-get update -y && apt-get upgrade -y && apt-get update

RUN apt install -q -y syslog-ng

RUN useradd -m wellton && echo "wellton:test123" | chpasswd && \
    mkdir -p /home/wellton/Maildir && chown -R wellton:wellton /home/wellton/Maildir

RUN useradd -m gabriel && echo "gabriel:test123" | chpasswd && \
    mkdir -p /home/gabriel/Maildir && chown -R gabriel:gabriel /home/gabriel/Maildir

COPY main.cf /etc/postfix/main.cf
COPY 10-auth.conf /etc/dovecot/conf.d/10-auth.conf
COPY dovecot.conf /etc/dovecot/dovecot.conf

CMD ["sh", "-c", "service syslog-ng start ; service postfix start ; service dovecot start; tail -F /var/log/mail.log"]
