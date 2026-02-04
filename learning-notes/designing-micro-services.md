### Designing APIs for Microservices 

## The Monolith: 

- Monolith applications are one big self contained unit that contain all the logic of the application. 
- They are hard to scale, update and maintain and can prove to be problematic pretty soon. 

<img width="487" height="689" alt="Monolith Application" src="https://github.com/user-attachments/assets/efb2f102-33c2-45ba-89ba-df4d72e419c6" />

# Benefits 
- Easier to develop and deploy initially 
- Limited scaling 
- Tight coupling 

## Microservice architecture : 

Micro-services distribute the applications into key components  - each component or “micro  services” are responsible for a specific function of the larger application. 
- Small independently deployable services 
- Each service runs its own process. 
- Services communicate via lightweight mechanisms (APIs , messaging systems, etc. )
- Built around business capabilities and split around business functions they performs. 
- Design is as independent as possible - each service has its own code base, data storage and deployment pipelines. 
- Systems are easier to understand and change. 
- You cannot just split up a monolith application into small components - it requires careful design.

<img width="902" height="813" alt="Microservice" src="https://github.com/user-attachments/assets/c48dbee5-7315-427c-abe4-d0407649be2c" />

# Benefits:
    - Faster development 
    - Independent scaling 
    - Fault Isolation
    - Easier maintenance 
# Challenges 
    - Distributed Systems challenges 
        - Complex communication 
        - Data Consistency issues 
        - System Management overhead
    - Increased complexity 
    - Data Consistency issues 


## Factors influencing the choice of architecture 

1. Application size and complexity 
2. Team’s knowledge of micro services 
3. Scalability and flexibility needs 
4. Budget and timeline. 

## Demystifying Assumptions: 

1. One shared database in micro services 
    1. This introduces tight coupling 
    2. Potential bottlenecks on the database level
2. Infinitely scalable 
    1. Microservices are better at scaling than monoliths but they still have scaling limits 
    2. Bad design can still cause scaling issues.
    3. Management and orchestration complexity impacts scaling.  
3. Micros ervices eliminates single point of failure. 
    1. Failure in one service can impact others using it. A central service can create bottlenecks. 

Application of loose coupling, clear separation of concerns and well defined interfaces are keys to built robust application. 

	
## Key Micro services Design principles. 

# Single Responsibility Principle 
    1. Each Micros ervice should have a single , well defined responsibility 
    2. It should only handle one function and one type of data. 
    3. The service boundaries should align with business capabilities. 

# Loose Coupling 
    1. Each micro service should have and maintain it’s own data and they communicate through well defined APIs or messaging systems 
    2. Update to one system will not impact others as long as the API contract and messaging contract is stable. 
# Autonomy
    1. This ensures that each microservice is self contained 
    2. It has control over it’s own data 
    3. It can be deployed independently without affecting other systems. 
    4. This allows the team to iterate and release features without the need of coordination or wait for system wide deployments. 
<img width="1300" height="949" alt="Repository" src="https://github.com/user-attachments/assets/c1df2e4a-7cda-482b-9eab-7d1a3d2339ab" />

## Common Pitfalls in designing micro services. 

# Overly fine grained services 
    1. Increased complexity and communication overhead 
    2. Strive for balance between granularity and practicality 
# Using same tech stack for all services 
    1. Use the best technology for the needs of the system. 
    2. Embrace polygular programming and allow services to use the best tools for the functionality 
    3. Example: While user profile management can be a SQL database, the connections feature can use a No SQL or graph database instead 
# Underestimating the complexity of distributed systems. 
    
## The CAP Theorem:
 A Distributed System can provide only 2 out of 3 properties: 
 -  Consistency : All nodes in the system see the same data at the same time.
 -  Availability : Every request receives a response with out the guarantee that it contains the most recent data
 -  Partition Tolerance: The system continues to operate even when there are network partitions or failures
   In micro service architecture - partition tolerance is usually a must have. With services distributed across multiple nodes, network partitions and failures cannot be avoided,so we need to make a trade off between consistency and availability. 

Best Practices in Micro-service Architecture. 

* Use API -first approach - design and documenting the API contract first before coding 
    * Ensures clear understanding of service interactions and data exchange. 
    * Allows to identify the issues earlier 
    * Make informed decisions about the structure of the API 
* using domain‑driven design to identify bounded context
    * DDD helps identify bounded context which 
*  ensuring Data Consistency through eventual consistency and event‑driven architectures
    * Data consistency is a challenge in a microservices architecture as each service typically has its own database. 
    * This can lead to situations where data might be temporarily out of sync across services. 
    * To mitigate this issue, you can employ eventual consistency and event‑driven architectures. For example, when a service updates its data, it can publish an event that other services can listen to and react accordingly. 
*  Handling cross‑cutting concerns using API gateways
    * When it comes to cross‑cutting concerns like security and logging, cannot be implemented individually as this can lead to duplication and inconsistency. 
    * It’s better to use a centralised approach with an API gateway. API gateways act as a single entry point for  micro services, handling tasks like authentication and rate limiting.
    *  While micro services aim for decentralisation and autonomy, centralising certain cross‑cutting concerns can provide a more consistent and manageable components. 
* Design for failure with circuit breakers and fallback strategies
    *  failures are inevitable due to network issues or latency spikes that can disrupt the communication between services. 
    * Implement retry mechanisms and fallback strategies helps handling such situations.
    *  For example, if a service is experiencing issues, the consuming service can implement a retry mechanism to attempt reconnecting. If the issue persists, it can switch to a fallback strategy, such as using cache data or providing a degraded experience.
    *  By designing for failure, you make your microservices more resilient and able to handle unexpected situations gracefully. 
*  Versioning APIs to introduce changes without breaking existing clients. 
    * New changes should be added to a new version so that existing clients can still operate on the current version. 
    * New clients can use the new version directly 
    * Existing clients can take time to move to new versions and the old version can be deprecated gradually 
    * In APIs , it’s best to use the API version in the number /api/v1 and api/v2 or use them in headers. 



## API Granularity 

- Fine grained APIs 
    - Exposes small and specific operations 
    - Benefits: 
        - high level of control and flexibility,
        - Access and manipulate specific resources
        - Perform precise operations.
    - Drawbacks : 
        - Increased network calls 
        - Higher volume of data transfer
        -  Complexity in managing and orchestrating interactions between services 
- Coarse grained APIs
    * Exposes larger, more complex operations
    * Benefits - 
        * Reduced network overhead 
        * Simplified service interaction 
        * Larger chunks of functionality 
    * Drawbacks 
        * Tight coupling between services 
        * Reduces Flexibility in client interactions. 

### Using Bounded Context from DDD. 

* A bounded context defines the limits of a specific domain, including its entities, behaviours, and rules.
* It helps organise the development of micro-services by clearly separating different domains of the application.
* A single bounced context can contain one or more micro services. 
* They guide granularity of the APIs. 
* A bounded context should have its own API to encapsulate functionalities and data.
* The granularity of the API should be determined by the cohesion within the context and the desire of loose coupling between contexts.  
* If a piece of information is not directly needed , keep it internal. Abstract it within API boundary 

<img width="3437" height="2486" alt="Pasted Graphic 3" src="https://github.com/user-attachments/assets/3a54ddcf-8fd6-4047-9125-baa4aa72a8c9" />


￼
###  Choosing the correct level of granularity
 Too many microservices = 
- increased operational complexity,
-  more network overhead
-  more potential points of failure. 
- 
  Overly coarse‑grained APIs =  
- can create mini monolith
-  Harder to understand, change, and maintain over time
-  can lead to tighter coupling between services. 
  
  The key is to find the right level of granularity for your specific context and requirements, considering factors such as the 
- team structure
-  rate of change of different parts of the system
-  performance requirements
-  Overall domain complexity
  
  
- “Designing for change” from the beginning is important, creating APIs and service boundaries that are as stable as possible even if the internal implementation details change. 
- When adjusting bounded contexts, merging them is generally easier than splitting them apart.
- Splitting a context requires careful planning and coordination, possibly using a facade or a gateway to present a consistent interface to clients during the transition.

