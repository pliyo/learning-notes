# Monolith to microservices, by Sam Newman

#

# Chapter 1

- `Microservices`: independently deployable services modeled around a business domain. They communicate with each other via networks. They are technology agnostic. They expose the business capabilities that they encapsulate via one or more network endpoints. They encapsulate data storage and retrieval, exposing data, via well-defined interfaces. So databases are hidden inside the service boundary.

- We want to think of our services as end-to-end slices of business functionality, that where appropriate encapsulate the UI, application logic, and data storage.

- Microservices buy you options, they have a cost, and you have to decide if the cost is worth the options you want to take up.

- `Size` of a microservice is highly contextual. The goal is to have "as small an interface as possible". More important is: How many microservices can you handle? How do you define microservices boundaries to get the most out of them, without everything becoming a horribly coupled mess?

- `Coupling`: how changing one thing requires a change in another.

- `Cohesion`: How we group related code. "A structure is stable if cohesion is high, and coupling is low".

- `Independent deployability`: We would like to be able to make a change to our service and deploy that service into production without having to change anything else. For this to work, we need stability of the services we consume, and we need to provide a stable contract to those services that consume us.

- `Microservice architecture`: modules that communicate via networks that can be deployed independently.

- `Information hiding`: The core idea with information hiding is to separate the parts of the code that change frequently from the ones that are static

- `Encapsulation`: bundling together of one or more things into a container.

- `Outside-in`: drive the service interface by thinking of things from the point of the service consumers first.

- `Aggregate`: It's a representation of a real domain concept - think of something like an Order, Invoice, Stock Item, etc. Aggregates typically have a life cycle around them, which opens them up to being implemented as a state machine. A single microservice will handle the life cycle and data storage of one or more different types of aggregates.

- A `bounded context` typically represent a largar organizational boundary inside an organization. Within the scope of that boundary, explicit responsibilities need to be carried out.

- The `aggregate` is a self-contained state machine that focuses on a single domain concept in our system, with `the bounded context` representing a collection of associated aggregates, again with an explicit interface to the wider world. Both can work well as service boundaries. When starting out, you should reduce the number of services you work with, targetting services that encompass entire bounded contexts. As you find your feet, try to split them around aggregate boundaries.

# Chapter 2

- `Why might you choose microservices?` Improved team autonomy. Reduce time to market (Think of all the steps involved when shipping software, from PO to be in Prod, maybe the bottleneck is somewhere else). Scale Cost-Effectively for Load. Improve robustness (decrease overlal system downtime). Bring new programming language.

- `Resilience`: To have a system that is able to react to expected variations. Having an organisation capable of adapting to things that haven't been thought of, ex: creating a culture of chaos engineering. Bringing a load balancer in because a machine will die is an example of robutness, resilience is the process of an organisation preparing itself for the fact that it cannot anticipate all potential problems.

- Adding more people will only continue to improve how quickly you can deliver, if the work itself can be partitioned into separate pieces of work with limited interactions between them. Ex: harvesting crops in a field.

- Fundamentally, reuse is not a direct outcome people want. You might end up doing things that slow you down.

- When are microservices a bad idea? Unclear domain (Getting service boundaries wrong might be expensive). Customer-Installed and managed software.

- When you migrate to a microservice architecture, you push a lot of complexity into the operational domain.

- Changing organisations (Kottler's eight-step process): Establishing a sense of urgency -> Creating the guiding coalition -> Developing a vision and strategy -> Communicating the change vision -> Empowering employees for broad-based action -> Generating short-term wins -> Consolidating gains and producing more change -> Anchoring new approaches in the culture -> Establishing a sense of urgency

- The `vision` is about the goal (what it is you're aiming for). The `strategy` is about the how.

- One of the most common problems is that people are too busy doing what they do now to have the bandwith to change.

- "Some decisions are consequential and irreversible or nearly irreversible—one-way doors—and these decisions must be made methodically, carefully, slowly, with great deliberation and consultation. If you walk through and don’t like what you see on the other side, you can’t get back to where you were before. We can call these Type 1 decisions. But most decisions aren’t like that—they are changeable, reversible—they’re two-way doors. If you’ve made a suboptimal Type 2 decision, you don’t have to live with the consequences for that long. You can reopen the door and go back through. Type 2 decisions can and should be made quickly by high judgment individuals or small groups" (Jeff Bezos). People who don't make decisions often may fall into the trap of treating Type 2 decisions like Type 1 decisions.

# Where to Start?

- `Event Storming` (by Alberto Brandolini) is a collaborative exercise involving technical and nontechnical stakeholders who together define a shared domain model. It focuses on understanding what (logical) events occur in the system.

- Whenever a system has no in-bound dependencies.

- `Sunk cost fallacy` occurs when people become so invested in a previous approach to doing something that even if evidence shows the approach isn't working, they'll still proceed anyway.

# Chapter 3
