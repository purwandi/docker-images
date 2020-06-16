FROM bitnami/rabbitmq:3.8-debian-10

RUN cd /opt/bitnami/rabbitmq/plugins/ && \
  wget https://github.com/rabbitmq/rabbitmq-delayed-message-exchange/releases/download/v3.8.0/rabbitmq_delayed_message_exchange-3.8.0.ez
  
RUN rabbitmq-plugins enable --offline rabbitmq_delayed_message_exchange
