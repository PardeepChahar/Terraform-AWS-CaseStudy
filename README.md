# Terraform AWS CaseStudy

### What is AWS SQS?
Amazon Simple Queue Service (SQS) is a fully managed message queuing service that enables you to decouple and scale microservices, distributed systems, and serverless applications. SQS eliminates the complexity and overhead associated with managing and operating message-oriented middleware and empowers developers to focus on differentiating work. Using SQS, you can send, store, and receive messages between software components at any volume, without losing messages or requiring other services to be available.

### How does SQS work?
SQS provides an API endpoint to submit messages and another endpoint to read messages from a queue. Each message can only be retrieved once, and you can have many clients submitting messages to and reading messages from a queue at the same time.

![image](https://user-images.githubusercontent.com/75135128/128227066-56708e1e-f3b1-4f2a-8a84-c92689c9c6b2.png)

The messages that SQS handles can be unformatted strings, XML or JSON. Because SQS guarantees “exactly once” delivery, and because you can concurrently submit messages to and read messages from a given queue, SQS is a good option for integrating multiple independent systems.

You might well be asking: why use SQS if you can have an internal HTTP API for each service? While HTTP APIs are an accessible way to expose software systems to external users, it’s not the most efficient mechanism when it comes to integrating purely internal systems. A messaging queue is more lightweight. In particular, SQS also handles things like automated retries, preserving queue state across multiple availability zones in AWS, and keeping track of expiration timeouts on all messages.

### Benefits of using SQS:
For Serverless developers, using SQS generally provides a wealth of benefits, which are given below:

1.Scalability: Your SQS queues scale to the volume of messages you’re writing and reading. You don’t need to scale the queues; all the scaling and performance-at-scale aspects are taken care of by AWS.

2. Pay for what you use: When using SQS, you only get charged for the messages you read and write (see the details in the Pricing section). There aren’t any recurring or base fees.

3. Ease of setup: Since SQS is a managed service, so you don’t need to set up any infrastructure to start using SQS. You can simply use the API to read and write messages, or use the SQS <-> Lambda integration.

4. Options for Standard and FIFO queues: When creating an SQS queue, you can choose between a standard queue and a FIFO queue out of the box. Both of these queue types can be useful for different purposes.

5. Automatic deduplication for FIFO queues: Deduplication is important when using queues, and for FIFO queues SQS will do the work to remove any duplicate messages for you. This makes FIFO queues on SQS suitable for tasks where it’s critical to have each task done exactly once.

### Use cases of SQS :
![image](https://user-images.githubusercontent.com/75135128/128227161-48cded02-abde-408a-b89a-8e0f672e7608.png)

The most common ways to use SQS, and of course other messaging systems, in cloud applications are:

1.Decoupling microservices: In a microservice architecture, messages represent one of the easiest ways to set up communication between different parts of the system. If your microservices run in AWS, and especially if those are Serverless services, SQS is a great choice for that aspect of the communication.

2. Sending tasks between different parts of your system: You don’t have to be running a microservices-oriented application to take advantage of SQS. You can also use it in any kind of application that needs to communicate tasks to other systems.

3. Distributing workloads from a central node to worker nodes: You can frequently find messaging systems in the flows of distributed large workloads like map-reduce operations. For these kinds of operations, it’s essential to be able to maintain a queue of all the tasks that need to be processed, efficiently distribute the tasks between the machines or functions doing the work, and guarantee that every part of the work is only done once.

4. Scheduling batch jobs: SQS is a great option for scheduling batch jobs for two reasons. First, it maintains a durable queue of all the scheduled jobs, which means you don’t need to keep track of the job status — you can rely on SQS to pass the jobs through and to handle any retries, should an execution fail and your batch system returns the message to the queue. Second, it integrates with AWS Lambda; if you’re using AWS Lambda to process the batch jobs, SQS automatically launches your Lambda functions once the data is available for them to process.

### RedBus: Case Study
![image](https://user-images.githubusercontent.com/75135128/128227220-6c5aefe8-940b-4b4d-898d-1ae45f0cc94d.png)

redBus is an Indian travel agency that specializes in bus travel throughout India by selling bus tickets throughout the country. Tickets are purchased through the company’s Website or through the Web services of its agents and partners. The company also offers software, on a Software as a Service (SaaS) basis, which gives bus operators the option of handling their own ticketing and managing their own inventories. To date, the company says they have sold over 30 million bus tickets and has more than 1750 bus operators using the software to manage their operations.

“With the time savings that the IT and development staffs obtain from the AWS solution, AWS gives us an overall cost benefit of about 30-40%.” - Charan Padmaraju, Chief Technology Officer, redBus

The Challenge
The company previously ran its operations from a traditional data center by purchasing and renting its systems and infrastructure. In addition to the expense, several logistical problems evolved from this arrangement. The biggest problem was that the infrastructure could not effectively handle processing fluctuations, which had a negative impact on productivity. Additionally, the procurement of servers or upgrading the server configuration was an extremely time-consuming endeavor. Over time, redBus realized that a better solution was imperative—a solution that offered scalability to handle the company’s processing fluctuations. redBus looked to Amazon Web Services (AWS) for a solution.

Why Amazon Web Services
After testing the AWS solution on a small application for several months, the travel agency determined that it was very workable and convenient. Although redBus was quite enthusiastic about the on-demand instances and variety of instance types, several other features cemented the company’s decision to migrate completely to AWS. These features included the ability to easily manage access to servers through security groups, the easy-to-use, self-service management console, the concept of Elastic IPs, and superior support.

The company has incorporated many of the AWS products into its solution, including Amazon Elastic Compute Cloud (Amazon EC2), Elastic Load Balancing, Amazon Relational Database Service (Amazon RDS), Amazon Simple Storage Service (Amazon S3), Amazon Elastic Block Store (Amazon EBS), and Amazon CloudWatch.

![image](https://user-images.githubusercontent.com/75135128/128227591-08f7470f-634f-4f12-8ca5-294a2a9b44c0.png)


### The Benefits
Since migrating to AWS, redBus has seen measurable improvements in the bottom line. Padmaraju says, “By scaling up and down dynamically based on the load, we maintain performance as well as minimize cost. With the time savings that the IT and development staffs obtain from the AWS solution, AWS gives us an overall cost benefit of about 30-40%.” He adds, “By hosting at [the AWS Asia Pacific (Singapore) region], redBus.in gained significantly in terms of website performance by way of reduced latency (about 4x). This is a great advantage when the customers are from India.”

Of the many excellent characteristics of AWS, perhaps the most significant to redBus is the ability to “instantly replicate the whole setup on demand for testing by creating and destroying instances on demand for experimentation, thereby reducing the time to market.” Less time to market translates to increased profitability and success.

Since joining forces with AWS, redBus has gained the freedom to experiment on new solutions and applications at minimal cost, increased the efficiency of its operations, and improved its profitability.
