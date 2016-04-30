### Big Data

<!-- .slide: data-background="img/background-orange-orig.jpg" -->

- Hadoop and NoSQL <!-- .element: class="fragment" --> 
- batch-mode <!-- .element: class="fragment" --> 
- offline processing <!-- .element: class="fragment" --> 

Note:
- Big Data starts in early 2000s when the largest Internet companies were forced to invent new ways to manage data 
  of unprecedented volumes
- most people think of Hadoop or NoSQL databases when they think of Big Data
- At the other end of the processing spectrum is real-time event processing, where individual events are processed as 
  soon as they arrive with tight time constraints, often microseconds to milliseconds
- Between these two extremes are more general stream processing models with less stringent responsiveness guarantees. 
- A popular example is the mini-batch model, where data is captured in short time intervals and then processed as small 
  batches, usually within time frames of seconds to minutes.

---

<!-- .slide: data-background="img/background-title-orig.jpg" -->

Stream processing is being used for:
- Updating machine learning models as new information arrives.
- Detecting anomalies, faults, performance problems, etc. and taking timely action.
- Aggregating and processing data on arrival for downstream storage and analytics.  
  
---

<!-- .slide: data-background="img/background-title-orig.jpg" -->

### λ-Architecture

<img src="./img/lambda-architecture.svg" style="background-color:white" />

Note:
- All data entering the system is dispatched to both the batch layer and the speed layer for processing.
- The batch layer has two functions: (i) managing the master dataset (an immutable, append-only set of raw data), and 
  (ii) to pre-compute the batch views.
- The serving layer indexes the batch views so that they can be queried in low-latency, ad-hoc way.
- The speed layer compensates for the high latency of updates to the serving layer and deals with recent data only.
- Any incoming query can be answered by merging results from batch views and real-time views.

---

### Fast Data 

<!-- .slide: data-background="img/background-title-orig.jpg" -->
 
> Fast Data captures a range of new systems and approaches, which balance various 
> tradeoffs to deliver timely, cost-efficient data processing, as well as higher developer productivity. 

Note:

---

### Requirements for a Fast Data Architecture 

<!-- .slide: data-background="img/background-title-orig.jpg" -->
 
  - Reliable data ingestion.
  - Flexible storage and query options.
  - Sophisticated analytics tools

Note:

