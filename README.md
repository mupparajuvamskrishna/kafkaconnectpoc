https://www.tutorialkart.com/apache-kafka/kafka-connector-mysql-jdbc/
https://docs.confluent.io/current/connect/kafka-connect-jdbc/source-connector/index.html
https://www.supergloo.com/fieldnotes/kafka-connect-mysql-example/

CREATE TABLE accounts(id INT NOT NULL AUTO_INCREMENT PRIMARY KEY, name VARCHAR(255));
INSERT INTO accounts(name) VALUES('alice');


name=test-source-mysql-jdbc-autoincrement
connector.class=io.confluent.connect.jdbc.JdbcSourceConnector
tasks.max=1
connection.url=jdbc:mysql://127.0.0.1:3306/accountsdb?user=root&password=Chak#436
mode=incrementing
incrementing.column.name=id
topic.prefix=test-mysql-jdbc-
/opt/confluent-5.1.0
/opt/confluent-5.1.0/bin/connect-standalone /opt/confluent-5.1.0/etc/schema-registry/connect-avro-standalone.properties /opt/confluent-5.1.0/etc/kafka-connect-jdbc/source-quickstart-mysql.properties

./bin/kafka-avro-console-consumer --bootstrap-server localhost:9092 --topic test-mysql-jdbc-accounts --from-beginning


/opt/confluent-5.1.0/share/java/kafka-connect-jdbc
export CLASSPATH=/opt/confluent-5.1.0/share/java/kafka-connect-jdbc/mysql-connector-java-5.1.6.jar

https://stackoverflow.com/questions/51835825/kafka-connect-failed-to-add-mysqlconnector
