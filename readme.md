# Reflection
## What is amqp?
- AMQP (Advanced Message Queuing Protocol) adalah open standard application layer protocol yang dirancang sebagai communication protocol untuk mengirim pesan (message) antar service. AMQP memungkinkan sebuah aplikasi bertindak sebagai producer untuk mengirim pesan ke message broker, kemudian pesan tersebut diteruskan ke queue agar dapat diproses oleh aplikasi lain yang bertindak sebagai consumer. Mekanisme ini, umumnya diimplementasikan pada sistem berbasis microservices agar setiap service service tidak perlu saling terhubung secara langsung (loosely coupled architecture).

## What does guest:guest@localhost:5672 mean?
String tersebut adalah AMQP URI yang mendefinisikan string koneksi ke RabbitMQ message broker. "guest" pertama mendefinisikan username (default) dan "guest kedua" mendefinisikan passwordnya (default). Selanjutnya "localhost" adalah hostname yang menjelaskan RabbitMQ dijalankan di mana dan "5672" merupakan definisi port listener dari sistem RabbitMQ. Maka dari itu, "localhost:5672" memiliki arti bahwa RabbitMQ dijalankan di local machine di port 5672.

## Simulation slow subscriber
![Slow-RabbitMQ](screenshots/rabbit-4.png)
Adanya perlambatan dengan implementasi thread::sleep selama 1 detik memberikan dampak berupa pemrosesan pesan di subsciber hanya dapat berlangsung maksimum 1 pesan per detiknya. Alhasil, message queue saya melonjak menjadi 16 akibat dari ini. Angka 16 ini didapat dari 3 kali pengiriman pesan secara beruntun dari publisher.