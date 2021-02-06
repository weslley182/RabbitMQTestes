# RabbitMQTestes

<n4>Instalação do Erlang (só next finish)</n4>
<p>https://www.erlang.org/downloads/23.2</p>

<h4>Instalação RabbitMQ</h4>
<p>https://www.rabbitmq.com/install-windows.html#installer</p>

<h4>Habilitar Plugin gerenciamento</h4>
<p>No RabbitMQ Command Prompt digite: rabbitmq-plugins enable rabbitmq_management</p>

<h4>Iniciar Servidor</h4>
<p>rabbitmq-server start</p>
<p>Acessar através do navegador localhost:15672 usuário e senha padrão guest e guest</p>

<h4>Instalação do Phyton, padrão</h4>
<p>https://www.python.org/downloads/release/python-387/</p>

<h4>Configurar Ambiente Phyton</h4>
<p>No prompt do Phyton: rodar o script phytonPath.py</p>
<p>Criar variável de ambiente</p>
<p>Na pasta onde esta o isntalador do Phyton execute o scrip get-pip.py</p>
<p>Instalar biblioteca do Rabbit: "python -m pip install -U pika"</p>

<h4>Queue</h4>
<p>python rabbitmqadmin declare queue --vhost=/ name=some_outgoing_queue durable=true</p>

<h4>Exchange</h4>
<p>python rabbitmqadmin declare exchange --vhost=/ name=some_exchange type=direct</p>

<h4>Binding</h4>
<p>python rabbitmqadmin --vhost=/ declare binding source="some_exchange" destination_type="queue" destination="some_outgoing_queue" routing_key="some_routing_key"</p>

<h4>Setup - Comandos</h4>
<h4>Primeiro servidor</h4>
<p>set RABBITMQ_NODENAME=rabbit1</p>
<p>set RABBITMQ_NODE_PORT=5672</p>
<p>set RABBITMQ_SERVER_START_ARGS=-rabbitmq_management listener [{port,15672}]</p>
<p>rabbitmq-server start</p>
<p>Segundo Servidor</p>
<p>set RABBITMQ_NODENAME=rabbit2</p>
<p>set RABBITMQ_NODE_PORT=5673</p>
<p>set RABBITMQ_SERVER_START_ARGS=-rabbitmq_management listener [{port,15673}]</p>
<p>rabbitmq-server start</p>

<h4>Juntar segundo servidor ao cluster do primeiro</h4>
<p>rabbitmqctl -n rabbit2 stop_app</p>
<p>rabbitmqctl -n rabbit2 join_cluster rabbit1</p>
<p>rabbitmqctl -n rabbit2 start_app</p>