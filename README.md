Conectarse a la máquina virtual
Usuario: vboxuser
Password: bigdata

Instalar dependencias
pip install kafka-python

Iniciar servicios
sudo /opt/Kafka/bin/zookeeper-server-start.sh /opt/Kafka/config/zookeeper.properties &
sudo /opt/Kafka/bin/kafka-server-start.sh /opt/Kafka/config/server.properties &

Crear el topic en Kafka
/opt/Kafka/bin/kafka-topics.sh --create \
--bootstrap-server localhost:9092 \
--replication-factor 1 \
--partitions 1 \
--topic ecommerce_orders

Ejecutar el productor (poner el codigo)
python3 kafka_producer.py

Ejecutar el consumidor en otra terminal (poner el codigo)
spark-submit --packages org.apache.spark:spark-sql-kafka-0-10_2.12:3.5.3 spark_streaming_consumer.py

Visualizar resultados

Consola: muestra el conteo y total de ventas por categoría.

Interfaz web de Spark:

http://192.168.18.81:4040
