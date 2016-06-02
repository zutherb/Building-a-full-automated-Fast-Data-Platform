
### SMACK

<!-- .slide: data-background="img/background-orange-orig.jpg" -->

- S park <!-- .element: class="fragment" --> 
- M esos <!-- .element: class="fragment" --> 
- A kka <!-- .element: class="fragment" --> 
- C assandra <!-- .element: class="fragment" --> 
- K afka <!-- .element: class="fragment" --> 

---

<!-- .slide: data-background="img/background-green-orig.jpg" -->

### Spark
#### Swiss Army Knife for Data

- ETL Jobs <!-- .element: class="fragment" --> 
- μ-Batching on Streams <!-- .element: class="fragment" --> 
- SQL and Joins on non-RDBMS <!-- .element: class="fragment" --> 
- Graph Operations on non-Graphs <!-- .element: class="fragment" --> 
- Map/Reduce in super fast <!-- .element: class="fragment" --> 

---

<!-- .slide: data-background="img/background-green-orig.jpg" -->

###What about λ-Architectures? <!-- .element: class="fragment" --> 
####Spark Operations can be run unaltered in either batch or stream mode - <br />it is always an Resilient Distributed Dataset (RDD)! <!-- .element: class="fragment" --> 

---

<!-- .slide: data-background="img/background-green-orig.jpg" -->

### Mesos
#### Distributed Kernel for the Cloud

- Links machines to a logical instance <!-- .element: class="fragment" --> 
- Static deployment of Mesos <!-- .element: class="fragment" --> 
- Dynamic deployment of the workload <!-- .element: class="fragment" --> 
- Good integration with Hadoop, Kafka, Spark, and Akka <!-- .element: class="fragment" --> 
- Lots and lots of machines <!-- .element: class="fragment" --> 

---

<!-- .slide: data-background="img/background-green-orig.jpg" -->

### Akka
#### Framework for reactive applications

- Highly performant - 50 million messages per machine and second <!-- .element: class="fragment" --> 
- Simple concurrency via asynchronous processing <!-- .element: class="fragment" --> 
- elastic and without single point of failure <!-- .element: class="fragment" --> 
- resilient <!-- .element: class="fragment" --> 
 
---

<!-- .slide: data-background="img/background-green-orig.jpg" -->

### Cassandra
#### Performant and Always-Up NoSQL Database

- Linear scaling - approx. 10'000 requests per machine and second <!-- .element: class="fragment" --> 
- No Downtime <!-- .element: class="fragment" --> 
- Comfort of a column index with append-only performance Data-Safety over multiple data-centers <!-- .element: class="fragment" --> 
- Strong in denormalized models <!-- .element: class="fragment" --> 

---

<!-- .slide: data-background="img/background-green-orig.jpg" -->

### Kafka
#### Messaging for Big Data
     
- Fast - Delivers hundreds of MegaBytes per second to 1000s of clients <!-- .element: class="fragment" --> 
- Scales - Partitions data to manageable volumes <!-- .element: class="fragment" --> 
- Data-Safety - Append Only allows buffering of TBs without a performance impact <!-- .element: class="fragment" --> 
- Distributed - from the ground up <!-- .element: class="fragment" --> 

---

<!-- .slide: data-background="img/background-green-orig.jpg" -->

### Fast Data in the Microservice World

<img src="./img/microservice.svg" />

---

<!-- .slide: data-background="img/background-green-orig.jpg" -->

### Kafka as a Multiplexer-Demultiplexer

<img src="./img/kafka_multiplexer_demultiplexer.png" style="background-color:white;" />

---

<!-- .slide: data-background="img/background-green-orig.jpg" -->

### Backpressure

During Peak Times, the amount of incoming data may massively exceed the capacity - just think of IoT. The back-pressure in the processing pipelines needs to be actively managed, otherwise data is lost. 

---

### Emerging Architecture 

<!-- .slide: data-background="img/background-green-orig.jpg" -->

<img src="./img/fast-data-architecture.png" style="height:600px" />

