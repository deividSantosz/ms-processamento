# 🛠️ Microserviço de Processamento (Consumer)

Este projeto é um microserviço responsável por **consumir mensagens de uma fila RabbitMQ**. Ele ouve mensagens publicadas na fila pelo microserviço `pedido` e executa uma lógica de processamento (atualmente apenas imprime a descrição do pedido no console).

---

## 📦 Tecnologias Utilizadas

- Java 17+
- Spring Boot
- Spring AMQP (RabbitMQ)


---

## 📫 Funcionamento

Este serviço está escutando a fila definida em:

```properties
broker.queue.processamento.name=fila.processamento
```

```java
@RabbitListener(queues = "${broker.queue.processamento.name}")
public void listenerProcessamentoQueue(@Payload String descricao) {
    System.out.println(descricao);
}
```

🔗 Serviço Producer (Envio de Mensagens)
Este serviço depende do microserviço pedido que envia as mensagens para a fila do RabbitMQ.

📤 Acesse o repositório do Producer:
👉 https://github.com/deividSantosz/ms-pedido

