כמובן! הנה ה-`README.md` המעודכן ללא הגדרת `application.properties`:

```markdown
# Sentiment Analysis with Kafka and News Stream

This project integrates sentiment analysis, Kafka, and a News Stream processing pipeline. It uses the Stanford CoreNLP library for sentiment analysis, Kafka for message brokering, and Spring WebFlux to provide a reactive API.

## Features

- **Stanford Sentiment Analysis**: Analyze the sentiment of messages from the news stream.
- **News Stream**: Stream messages filtered by a specific keyword.
- **Kafka Integration**: Send and receive messages to/from Kafka topics.
- **Time-based Grouping**: Group messages by a defined time window and analyze their sentiment.
- **REST API**: Expose endpoints to interact with the application.

## Dependencies

The project uses the following main dependencies:

1. **Stanford CoreNLP** for sentiment analysis:
   ```xml
   <dependency>
       <groupId>edu.stanford.nlp</groupId>
       <artifactId>stanford-corenlp</artifactId>
       <version>3.8.0</version>
   </dependency>
   
   <dependency>
       <groupId>edu.stanford.nlp</groupId>
       <artifactId>stanford-corenlp</artifactId>
       <version>3.8.0</version>
       <classifier>models</classifier>
   </dependency>
   ```

2. **Spring WebFlux** for creating reactive endpoints.
3. **Kafka** for message streaming:
   ```xml
   <dependency>
       <groupId>io.projectreactor.kafka</groupId>
       <artifactId>reactor-kafka</artifactId>
       <version>1.3.10</version>
   </dependency>
   
   <dependency>
       <groupId>org.springframework.kafka</groupId>
       <artifactId>spring-kafka</artifactId>
   </dependency>
   ```

4. **News Stream API**: A reactive stream that filters and processes news messages based on a keyword.

## Setup

1. Clone this repository to your local machine.
2. Install Docker and Kafka. Make sure Kafka is running.
3. Configure Kafka settings in your `application.properties` file.

## Endpoints

1. **/startNewsStream**: Start the news stream with a filter for a keyword.
   - **GET**: `/startNewsStream?text={keyword}`
   
2. **/stopNewsStream**: Stop the news stream.
   - **GET**: `/stopNewsStream`

3. **/sendKafka**: Send a text to Kafka.
   - **GET**: `/sendKafka?text={message}`

4. **/getKafka**: Receive messages from Kafka.
   - **GET**: `/getKafka`

5. **/grouped**: Group messages from Kafka based on a time window and filter by a keyword.
   - **GET**: `/grouped?text={keyword}&timeWindowSec={timeWindow}`
   
6. **/sentiment**: Analyze sentiment of messages received from Kafka.
   - **GET**: `/sentiment?text={keyword}&timeWindowSec={timeWindow}`

## Example Usage

1. **Send a message to Kafka**:
   - Send a text message to Kafka with:  
     `http://localhost:8080/sendKafka?text=test1`

2. **Retrieve messages from Kafka**:
   - Retrieve the messages with:  
     `http://localhost:8080/getKafka`

3. **Analyze sentiment of messages**:
   - Get sentiment analysis with:  
     `http://localhost:8080/sentiment?text=obama&timeWindowSec=3`


