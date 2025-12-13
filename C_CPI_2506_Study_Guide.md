# C_CPI_2506 Exam Preparation Guide
## Practice Questions and Answers by Topic

---

## Topic 1: SAP Integration Suite Overview (11-20% of exam)

### Question 1.1
**What are the core capabilities of SAP Integration Suite?**

**Answer:**
SAP Integration Suite comprises five major capabilities:
1. **Cloud Integration (CPI)** - Build and manage integration flows for enterprise-wide process integration
2. **API Management** - Discover, design, and govern APIs for API consumers
3. **Trading Partner Management (TPM)** - Design and operate B2B integration scenarios
4. **Open Connectors** - Connect to non-SAP cloud applications and extend connectivity
5. **Integration Advisor** - Design interfaces and mappings using crowdsourcing and machine learning

---

### Question 1.2
**What is the primary deployment platform for SAP Integration Suite?**

**Answer:**
SAP Integration Suite is deployed on **SAP Business Technology Platform (BTP)**. BTP provides a unified, intelligent, and secure platform for building enterprise applications and integration solutions. The services run on cloud infrastructure with options for different regions and deployment models.

---

### Question 1.3
**What is the difference between Trading Partner Management and Open Connectors?**

**Answer:**
- **Trading Partner Management (TPM)** - Specifically designed for B2B integration scenarios. It enables you to onboard trading partners, create profiles, manage agreements, and handle standard B2B protocols and formats. Used for B2B provider-consumer relationships.

- **Open Connectors** - A general-purpose connectivity solution that enables integration with non-SAP cloud applications (like Salesforce, ServiceNow, etc.). It provides pre-built connectors to accelerate integration with third-party cloud solutions and supports REST and other modern protocols.

---

### Question 1.4
**What is Integration Advisor and what are MIGs and MAGs?**

**Answer:**
**Integration Advisor** is a capability that helps design interfaces and mappings using crowdsourcing and machine learning.

- **MIGs (Message Implementation Guidelines)** - Define the structure and format of messages exchanged between trading partners. They specify which elements and segments from a standard (like EDI or EANCOM) are used in your integration scenario.

- **MAGs (Message Mapping Guidelines)** - Define how to map between different message formats or message implementation guidelines. They ensure semantic and structural alignment between sender and receiver messages.

---

### Question 1.5
**Which SAP Integration Suite capability would you use to implement microservices communication?**

**Answer:**
**SAP Event Mesh** is the primary capability for microservices communication in an event-driven architecture. It enables:
- Asynchronous, decoupled communication between services
- Publish-subscribe patterns for one-to-many messaging
- Support for various protocols (AMQP, MQTT, JMS, HTTP)
- Event-driven architecture implementation across both SAP and non-SAP systems

---

### Question 1.6
**Explain the concept of "aligned APIs" in SAP Integration Suite.**

**Answer:**
"Aligned APIs" refers to a scenario where sender and receiver systems use the same data format and structure, requiring no mediation or transformation. When APIs are aligned:
- No format conversion is necessary
- No message mapping or structural transformation is needed
- Direct communication is possible without middleware transformation
- This minimizes complexity but requires both systems to use compatible data models

Contrast this with scenarios requiring mediation through transformations, mappings, or format conversions.

---

### Question 1.7
**What are the use cases for SAP Event Mesh versus SAP Cloud Integration for asynchronous messaging?**

**Answer:**
**SAP Event Mesh is better for:**
- Event-driven architectures with multiple receivers (Pub/Sub patterns)
- High-volume messaging scenarios (IoT, real-time analytics)
- Applications that natively support AMQP, MQTT, or JMS
- Scenarios requiring replay capabilities
- Bandwidth-based licensing is cost-effective for high volumes

**SAP Cloud Integration is better for:**
- Complex transformations and message mappings required
- Request-response patterns with limited async requirements
- Scenarios using JMS queuing built into Cloud Integration
- Scenarios requiring extensive message processing logic

---

## Topic 2: Managing APIs (21-30% of exam)

### Question 2.1
**What are the main steps in API lifecycle management in SAP API Management?**

**Answer:**
The API lifecycle consists of four main phases:

1. **Design** - Define API specifications (OpenAPI, Swagger), resources, endpoints, and expected request/response formats
2. **Development** - Implement API logic, backend connections, and policy configurations
3. **Testing** - Test APIs through developer portal sandbox or Postman collections
4. **Publishing** - Publish APIs to the API Developer Portal for consumption by developers
5. **Monitoring** - Track API usage, performance metrics, and troubleshoot issues

---

### Question 2.2
**What is an API Policy in SAP API Management and provide examples.**

**Answer:**
An **API Policy** is a set of rules and configurations that can be applied to APIs to handle cross-cutting concerns and control API behavior.

**Common Policy Types:**
- **Authentication Policies** - OAuth 2.0, API Key validation, JWT verification
- **Rate Limiting** - Throttle API requests to prevent abuse (quota policies)
- **Transformation Policies** - Convert message formats (JSON to XML, etc.)
- **Routing Policies** - Direct requests to different backend services based on conditions
- **Logging & Monitoring** - Log API calls, track performance metrics
- **CORS Policies** - Handle cross-origin resource sharing

Policies can be applied at different scopes: API level, operation level, or flow level.

---

### Question 2.3
**How does rate limiting work in SAP API Management and why is it important?**

**Answer:**
**Rate Limiting** controls the number of API requests a consumer can make within a specific time window.

**Implementation:**
- Define quotas (e.g., 1000 requests per hour)
- Set spike arrest limits for burst traffic protection
- Apply different limits to different API consumers based on subscription tiers

**Importance:**
- Prevents API abuse and DDoS attacks
- Ensures fair resource utilization among all consumers
- Protects backend systems from being overwhelmed
- Enables SLA enforcement for different service tiers
- Provides cost control for usage-based licensing models

---

### Question 2.4
**What is the API Developer Portal in SAP API Management?**

**Answer:**
The **API Developer Portal** is a self-service platform where:
- API providers publish and document APIs
- External and internal developers discover APIs
- Developers can subscribe to APIs and obtain API keys
- A sandbox environment is available for testing before production use
- API documentation, sample code, and Postman collections are accessible
- Analytics showing API usage by consumer are visible
- Developers can manage their credentials and subscriptions

It serves as the central hub for API discovery and consumption management.

---

### Question 2.5
**What are the key differences between OAuth 2.0 and API Key authentication?**

**Answer:**
| Feature | OAuth 2.0 | API Key |
|---------|----------|--------|
| **Security Level** | Higher - token-based with expiration | Lower - static key-based |
| **Token Lifespan** | Short-lived, can be refreshed | No expiration unless managed |
| **Delegation** | Allows delegated access | Direct access only |
| **Use Case** | Third-party integrations, user authorization | Service-to-service, internal APIs |
| **Complexity** | More complex to implement | Simple and straightforward |
| **Revocation** | Tokens expire; can be revoked immediately | Keys must be manually rotated |
| **Standards** | Industry standard for open systems | Custom implementation |

---

### Question 2.6
**How would you troubleshoot an API that is returning 401 Unauthorized errors?**

**Answer:**
Check these areas in order:

1. **Authentication Configuration**
   - Verify the API policy correctly implements the authentication scheme
   - Check OAuth token validity and expiration
   - Ensure API Key is properly configured

2. **Client-Side Issues**
   - Confirm the client is sending correct credentials in headers/body
   - Verify API Key or OAuth token is included in request
   - Check authorization header format (Bearer token, API Key header name, etc.)

3. **Backend Policy Issues**
   - Review policy execution order
   - Check conditional flows that might bypass authentication
   - Verify no policies are interfering with auth headers

4. **Monitoring & Logs**
   - Review API analytics and traffic logs
   - Check SAP API Management audit logs
   - Verify backend service is responding with proper auth validation

---

### Question 2.7
**What is API versioning and how should it be handled in SAP API Management?**

**Answer:**
**API Versioning** allows you to maintain multiple versions of an API simultaneously to support backward compatibility and gradual migration of consumers.

**Versioning Strategies:**
1. **URL Path Versioning** - `/api/v1/products`, `/api/v2/products`
2. **Query Parameter** - `/api/products?version=2`
3. **Header-Based** - Custom header like `X-API-Version: 2`
4. **Content Negotiation** - Different media types for versions

**Best Practices:**
- Always version APIs before release
- Maintain at least one previous version for backward compatibility
- Clearly document breaking changes in release notes
- Set deprecation timelines for older versions
- Use SAP API Management to manage multiple versions with distinct endpoints
- Implement sunset headers to notify consumers of deprecation

---

## Topic 3: Implementing Cloud Integration (31-40% of exam)

### Question 3.1
**What is an Integration Flow (iFlow) and what are its main components?**

**Answer:**
An **Integration Flow (iFlow)** is the core artifact in SAP Cloud Integration that defines how data flows from a source system to a target system with transformations and processing logic applied.

**Main Components:**
1. **Start Event** - Trigger the flow (Timer, Receiver, etc.)
2. **Adapters** - Connect to external systems (HTTP, SOAP, SFTP, etc.)
3. **Mapping/Transformers** - Transform message format (XML to JSON, etc.)
4. **Enrichers** - Add external data to messages
5. **Routers** - Direct messages based on conditions
6. **Splitters** - Break single messages into multiple messages
7. **Aggregators** - Combine multiple messages into one
8. **Content Modifiers** - Enrich headers, properties, or body
9. **Error Handlers** - Handle exceptions and route failed messages
10. **End Event** - Send response or complete processing

---

### Question 3.2
**What is the Content Modifier and how is it used in integration flows?**

**Answer:**
The **Content Modifier** is a transformation component that modifies the content of messages during flow execution.

**What it can modify:**
1. **Message Headers** - Add, modify, or delete HTTP/protocol headers
2. **Message Body** - Completely replace or enrich the message payload
3. **Exchange Properties** - Set custom properties for use in subsequent steps

**Example Use Case:**
```
Input Message:
<product>
  <productId>HT-1051</productId>
  <productName>Laptop</productName>
</product>

Content Modifier adds:
- Message Body: Enriched with <orderTime>${property.timestamp}</orderTime>
- Message Header: X-Order-ID set to unique value

Output Message:
<order>
  <orderTime>2025-12-13 12:58:00</orderTime>
  <product>
    <productId>HT-1051</productId>
    <productName>Laptop</productName>
  </product>
</order>
```

**Configuration:**
- Use **Constant** type for static content
- Use **Expression** type for dynamic content with variables like `${in.body}`, `${property.timestamp}`

---

### Question 3.3
**Compare and contrast the HTTP, SOAP, and SFTP adapters in Cloud Integration.**

**Answer:**
| Feature | HTTP Adapter | SOAP Adapter | SFTP Adapter |
|---------|-------------|------------|------------|
| **Protocol** | HTTP/HTTPS REST | SOAP/Web Services | Secure File Transfer |
| **Message Format** | JSON, XML, plain text | XML (SOAP envelope) | Files (any format) |
| **Use Case** | REST APIs, cloud services | Legacy systems, SOAP services | File-based integrations |
| **Request-Response** | Yes (native) | Yes (synchronous) | No (file transfer) |
| **Authentication** | Basic, OAuth, API Key | WS-Security, SAML | SSH, password-based |
| **Payload Size** | No specific limits | SOAP envelope overhead | Large files supported |
| **Error Handling** | HTTP status codes | SOAP faults | Retry mechanisms, file archives |
| **Polling** | Receiver can poll | N/A | Sender can poll for files |

---

### Question 3.4
**What is a message mapping in Cloud Integration and how does it work?**

**Answer:**
**Message Mapping** transforms a message from one format/structure to another, typically between source and target system requirements.

**Types of Mappings:**

1. **Graphical Mapping** - Drag-and-drop mapping using mapping editor
   - Simple field-to-field transformations
   - Built-in functions for conversions
   - Visual representation of data flow

2. **XSLT Mapping** - XML Stylesheet Language Transformations
   - More complex transformations
   - Requires XSLT knowledge
   - Powerful for conditional logic

3. **Custom Mapping** - Using Java/Groovy scripts
   - Most flexibility for complex logic
   - Can implement custom algorithms
   - Higher development effort

**Example:**
```
Source Format (JSON):
{
  "firstName": "John",
  "lastName": "Doe"
}

Mapping Logic: Concatenate firstName and lastName

Target Format (XML):
<Person>
  <FullName>John Doe</FullName>
</Person>
```

---

### Question 3.5
**What are routing and splitting mechanisms in Cloud Integration?**

**Answer:**
**Routing** and **Splitting** handle complex message processing scenarios:

**Routing (Router Shape):**
- Directs messages to different paths based on conditions
- Evaluates message content, properties, or headers
- Routes to different target systems based on business logic
- Example: Route customers to different backends based on customer type

**Splitting:**
- Breaks a single message into multiple messages
- Used when one input message contains multiple entities
- Example: Order with 5 line items → Create 5 separate line item messages

**Aggregation (Opposite of splitting):**
- Combines multiple messages into a single message
- Waits for multiple messages and merges them
- Example: Collect responses from multiple backend systems into one final response

**Example Scenario:**
```
1. Receive: Order with 10 line items
2. Split: Create 10 separate line item messages
3. Route: Route to different fulfillment centers based on warehouse location
4. Process: Each fulfillment center processes its items
5. Aggregate: Combine all fulfillment confirmations into single order confirmation
```

---

### Question 3.6
**What is the purpose of error handling in Cloud Integration iFlows?**

**Answer:**
**Error Handling** ensures reliable integration by managing failures gracefully and preventing complete system failure.

**Error Handling Mechanisms:**

1. **Try-Catch Blocks** - Capture and handle specific errors
2. **Dead Letter Routes** - Send failed messages to error queue for later analysis
3. **Retry Logic** - Automatically retry failed requests with configurable attempts
4. **Fallback Routes** - Execute alternative paths when primary path fails
5. **Error Notifications** - Alert stakeholders of failures via email/alerts
6. **Message Archiving** - Store failed messages for audit and reprocessing

**Best Practices:**
- Always include error handling in production flows
- Log errors with sufficient detail for debugging
- Implement exponential backoff for retries to avoid overwhelming systems
- Archive failed messages for audit compliance
- Monitor failed message queues actively
- Set up alerts for critical failures

---

### Question 3.7
**How would you design an iFlow to poll files from an SFTP server, transform them, and send to an HTTP endpoint?**

**Answer:**
**iFlow Design:**

1. **Start Event** - Timer trigger (e.g., every hour)

2. **SFTP Adapter (Sender)**
   - Connect to SFTP server with credentials
   - Configure polling interval (e.g., 1 hour)
   - Specify file name pattern (e.g., `*.csv`)
   - Configure post-processing (delete/archive after reading)

3. **Content Modifier**
   - Add headers with file metadata
   - Add timestamp and processing ID

4. **Message Mapping**
   - Transform CSV/File format to required target format
   - Handle data type conversions
   - Map field names appropriately

5. **HTTP Adapter (Receiver)**
   - Configure target endpoint URL
   - Set authentication (Basic/OAuth)
   - Configure request method (POST/PUT)
   - Handle response and errors

6. **Error Handler**
   - Route failed messages to error queue
   - Retry on specific HTTP errors (5xx)
   - Archive original files if processing fails

**Configuration Considerations:**
- Set appropriate polling frequency to avoid resource overload
- Implement idempotency key to prevent duplicate processing
- Archive processed files for audit trail
- Monitor SFTP connection health

---

### Question 3.8
**What are the differences between Synchronous and Asynchronous processing in Cloud Integration?**

**Answer:**
| Aspect | Synchronous | Asynchronous |
|--------|-------------|------------|
| **Processing Model** | Request-Response | Fire-and-Forget |
| **Wait for Response** | Yes, caller waits | No, caller continues |
| **Latency** | Depends on processing time | Decoupled from processing |
| **Failure Handling** | Immediate error feedback | Errors handled separately |
| **Use Cases** | Real-time queries, APIs | Batch processing, events |
| **Coupling** | Tightly coupled | Loosely coupled |
| **Scalability** | Limited by wait times | Highly scalable |
| **Example** | HTTP GET request | File polling, Event Mesh |

---

## Topic 4: SAP Event Mesh (21-30% of exam)

### Question 4.1
**What is SAP Event Mesh and what problems does it solve?**

**Answer:**
**SAP Event Mesh** is a message broker service on SAP BTP that enables event-driven architectures through asynchronous, decoupled communication.

**Problems it solves:**

1. **Runtime Decoupling** - Sender and receiver don't need to run simultaneously
   - Sender publishes events regardless of receiver availability
   - Receiver processes events asynchronously

2. **Scalability** - Efficiently handles high-volume event streams
   - Separate messaging from application processing
   - Different scaling strategies for publishers and subscribers

3. **Reliability** - Guarantees message delivery
   - Messages persist until consumed (dead letter queues)
   - Replay capabilities for reprocessing

4. **Flexibility** - Multiple protocols and patterns supported
   - AMQP, MQTT, JMS, HTTP/REST
   - Publish-Subscribe pattern for one-to-many scenarios

**Use Cases:**
- Event-driven microservices
- IoT data ingestion
- Real-time analytics
- Asynchronous order processing

---

### Question 4.2
**What are Topics, Queues, and Topic Endpoints in SAP Event Mesh?**

**Answer:**
**Topics:**
- Represent event channels in a publish-subscribe model
- One publisher can send events to a topic
- Multiple subscribers can listen to the same topic
- Events are broadcast to all active subscribers
- No persistent storage of events (unless configured)

**Queues:**
- Point-to-point messaging model
- Messages are delivered to a single consumer
- Messages remain in queue until consumed and acknowledged
- Supports competing consumers pattern
- Guarantees FIFO (First-In-First-Out) processing

**Topic Endpoints (Durable Subscriptions):**
- Hybrid approach combining topics and queues
- Creates a durable subscription to a topic
- Messages are queued for the subscriber even if temporarily offline
- Consumer can replay messages from the topic endpoint
- Enables message persistence with topic-based delivery

**Selection Criteria:**
- Use **Topics** when multiple independent systems need the same event
- Use **Queues** for point-to-point, reliable processing
- Use **Topic Endpoints** when you need persistence with pub-sub pattern

---

### Question 4.3
**Explain asynchronous communication and how it differs from synchronous communication.**

**Answer:**
**Synchronous Communication:**
- Sender waits for immediate response
- Blocks until receiver processes request
- Tight coupling between systems
- Example: HTTP REST API call

**Asynchronous Communication:**
- Sender doesn't wait for response
- Message is placed in queue/topic
- Receiver processes independently
- Loose coupling between systems
- Example: Publishing event to SAP Event Mesh

**Advantages of Asynchronous:**
- Improved resilience - system failures don't cascade
- Better scalability - can handle traffic spikes
- Flexibility in processing timing
- Reduced latency perception - quick acknowledgment
- Independent system scaling

**Disadvantages:**
- Added complexity in error handling
- Delayed processing requires tracking
- Harder to debug and troubleshoot
- Potential for message ordering issues

---

### Question 4.4
**What does "application decoupling" mean and why is it important?**

**Answer:**
**Application Decoupling** means reducing dependencies between systems so they can operate independently.

**Types of Decoupling:**

1. **Runtime Decoupling** - Systems don't need to run simultaneously
   - System A publishes event and continues
   - System B processes event later when available
   - Network outages don't immediately block System A

2. **Data Format Decoupling** - Different systems use different formats
   - System A sends JSON
   - System B expects XML
   - Middleware handles transformation

3. **Data Structure Decoupling** - Different field names/structures
   - System A has "firstName"/"lastName"
   - System B has "FullName"
   - Mapping handles conversion

**Importance:**
- **Resilience** - One system failure doesn't cascade
- **Scalability** - Systems scale independently
- **Agility** - Can modify systems without affecting others
- **Reusability** - Services can be consumed by multiple systems
- **Maintainability** - Clear boundaries and ownership

**Example:**
Without decoupling: Order System → (waits) → Billing System → (waits) → Shipping System
- If Billing is slow, entire flow blocks

With Event Mesh: Order System → Event Mesh ← Billing System (async) ← Shipping System (async)
- Order system completes immediately
- Billing and Shipping process independently

---

### Question 4.5
**What are the key protocols supported by SAP Event Mesh?**

**Answer:**
**AMQP (Advanced Message Queuing Protocol)**
- Industry-standard protocol for message-oriented middleware
- Supports both point-to-point and pub-sub patterns
- Reliable message delivery guarantees
- Used by most enterprise messaging systems

**MQTT (Message Queuing Telemetry Transport)**
- Lightweight protocol for IoT and mobile applications
- Minimal bandwidth and battery consumption
- Publish-subscribe model only
- Three QoS levels (0, 1, 2) for delivery guarantees

**JMS (Java Message Service)**
- Java-based API for messaging
- Supported through JMS bridging
- Queues and Topics support
- Standard Java enterprise messaging

**HTTP/REST**
- Browser-friendly protocol
- Easy integration with web applications
- Request-response pattern
- Less efficient for high-volume messaging

**Selection by Use Case:**
- **AMQP** - Enterprise integration, guaranteed delivery
- **MQTT** - IoT sensors, mobile devices
- **JMS** - Java applications, legacy systems
- **HTTP** - Web applications, REST APIs

---

### Question 4.6
**How would you integrate SAP S/4HANA events with external systems using Event Mesh?**

**Answer:**
**Architecture:**

1. **Event Emission from S/4HANA**
   - S/4HANA publishes events (e.g., Order Created, Invoice Posted) to Event Mesh
   - Events are available in SAP API Business Hub
   - S/4HANA connects to Event Mesh via AMQP

2. **Event Mesh as Central Hub**
   - Receives events from S/4HANA
   - Stores events in topics for subscribers
   - Enables multiple external systems to consume same event

3. **External System Consumption**
   - Billing System subscribes to Invoice Posted event
   - Shipping System subscribes to Order Created event
   - Analytics System subscribes to all events for data warehouse

4. **Example Flow:**
   ```
   S/4HANA (Order Created Event)
      ↓
   Event Mesh (Topic: "Orders/Created")
      ↙        ↓        ↘
   Billing   Shipping   Analytics
   ```

**Benefits:**
- S/4HANA doesn't need to know about external systems
- Multiple systems can consume same event
- Systems can be added/removed without changing S/4HANA
- Clear event schema in API Business Hub

**Configuration:**
- Define event namespace and topic structure
- Map S/4HANA event types to Event Mesh topics
- Configure subscriber authentication and authorization
- Set up monitoring and alerting for event flow

---

### Question 4.7
**What is the Publish-Subscribe pattern and when should it be used?**

**Answer:**
**Publish-Subscribe Pattern:**

**Concept:**
- Publishers emit events to a topic
- Multiple independent subscribers listen to the topic
- Each subscriber receives copy of the event
- Publishers and subscribers are loosely coupled

**Diagram:**
```
Publisher 1 ─┐
Publisher 2 ─┼─ Topic ─┬─ Subscriber 1
Publisher 3 ─┘         ├─ Subscriber 2
                        └─ Subscriber 3
```

**When to Use:**
- Multiple independent systems need the same event
- Event should trigger different actions in different systems
- Scalability across many subscribers
- Decoupled event distribution

**When NOT to Use:**
- Only one system needs the event (use Point-to-Point)
- Need guaranteed ordered processing by single consumer
- Require acknowledgment from all subscribers

**Example Scenario:**
```
Event: "Customer Created" (published to SAP Event Mesh)

Subscribers:
- CRM System: Create customer record
- Marketing System: Add to email list
- Analytics: Update customer count
- Billing System: Set up billing account

Each system independently processes the same event
```

**Implementation in Event Mesh:**
- Create Topic named "Customers/Created"
- Each system subscribes to the topic
- Event Mesh delivers event to all subscribers
- Each subscriber processes independently

---

### Question 4.8
**How does message persistence and replay work in SAP Event Mesh?**

**Answer:**
**Message Persistence:**

SAP Event Mesh stores messages in topics based on configuration:

**Retention Policies:**
- **Time-based** - Keep messages for X hours/days
- **Size-based** - Keep most recent X MB of messages
- **Combined** - Whichever limit is reached first

**Persistence Benefits:**
- Allows subscribers that were offline to catch up
- Enables replay scenarios
- Provides audit trail of events
- Supports multiple subscribers joining later

**Replay Capability:**

**Use Cases:**
1. New subscriber joins and wants historical data
2. Process failed and needs to reprocess old events
3. Audit requirements require historical event review
4. Data warehouse initial load from event stream

**Replay Process:**
```
1. Define replay start point (timestamp or message offset)
2. Subscriber receives: Old messages (from start point)
3. Then receives: New messages (real-time)
4. Processes all messages in order
```

**Important Considerations:**
- Idempotency is crucial - ensure messages can be replayed without duplicate effects
- Track processing checkpoints to avoid reprocessing
- Test replay scenarios thoroughly
- Monitor message volume during replay

**Example:**
```
Topic "Orders" retention: 30 days

Day 1: Orders A, B, C published
Day 15: New Billing system subscribes
  - Receives Orders A, B, C (historical)
  - Receives new orders in real-time

Day 20: Billing system crashed, needs to recover
  - Restart from checkpoint (Day 15)
  - Replay orders from Day 15-20
  - Resume real-time processing
```

---

## Summary Table: Topic Weightings and Focus Areas

| Topic | Exam Weight | Key Focus Areas |
|-------|-------------|-----------------|
| **SAP Integration Suite Overview** | 11-20% | Components, capabilities, use cases, architecture |
| **Managing APIs** | 21-30% | Lifecycle, policies, authentication, rate limiting, Developer Portal |
| **Implementing Cloud Integration** | 31-40% | iFlows, adapters, mapping, routing, error handling |
| **SAP Event Mesh** | 21-30% | Topics, queues, pub-sub, decoupling, protocols, replay |

---

## Study Tips for Exam Success

1. **Hands-On Practice** - Build actual iFlows and configure APIs in a sandbox environment
2. **Scenario Analysis** - Practice designing solutions for business scenarios
3. **Architecture Thinking** - Focus on when to use each component (CPI vs Event Mesh vs API Management)
4. **Real-World Applications** - Understand practical use cases for each capability
5. **Error Handling** - Always consider failure scenarios and error handling strategies
6. **Performance Considerations** - Think about scalability, throughput, and latency
7. **Integration Patterns** - Study common patterns (Request-Reply, Pub-Sub, Polling, etc.)
8. **Documentation** - Review SAP help portal for official documentation on each component

---

## Exam Preparation Resources

- **Official SAP Training**: SAP Learning Hub
- **Hands-on Environment**: SAP BTP Free Trial
- **API Documentation**: SAP API Business Hub
- **Community Support**: SAP Community Network (SCN)
- **Practice Tests**: Look for official SAP certification exam simulators