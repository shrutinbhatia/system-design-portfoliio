### Designing APIs for Microservices 

## The Monolith: 

- Monolith applications are one big self contained unit that contain all the logic of the application. 
- They are hard to scale, update and maintain and can prove to be problematic pretty soon. 
￼
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

## Best Practices in Micro-service Architecture. 

* Use API-first approach
	* design and documenting the API contract first before coding 
    * Ensures clear understanding of service interactions and data exchange. 
    * Allows to identify the issues earlier 
    * Make informed decisions about the structure of the API 
* using domain‑driven design (DDD)
	*  DDD helps you identify bounded contexts, which are areas of your domain that have their own unique language and business rules.
 	*  By aligning your microservices with these bounded contexts, you ensure that each service has a clear responsibility and avoids unnecessary coupling.
*  ensuring Data Consistency through eventual consistency and event‑driven architectures
*  handling cross‑coding concerns using API gateways
* Design for failure with circuit breakers and fallback strategies
*  versioning APIs to introduce changes without breaking existing clients. 
* Centralise cross-cutting concerns 
