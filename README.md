from kafka import KafkaConsumer
import json

consumer = KafkaConsumer(
    'video-jobs',
    bootstrap_servers='localhost:9092',
    auto_offset_reset='earliest',
    enable_auto_commit=True,
    value_deserializer=lambda m: json.loads(m.decode('utf-8'))
)

print("Esperando mensajes...")

for message in consumer:
    data = message.value
    print(f"Procesando video: {data['filename']}")
    # Aquí iría tu lógica de mejora de video con IA
