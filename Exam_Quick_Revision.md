# PARALLEL & DISTRIBUTED SYSTEMS — EXAM READY NOTES

> **Exam:** 5 marks (numerical problem) + 10 MCQs + 15 marks (short + scenario)
>
> **How to use this file:** Read the OUTLINE first to see the full picture. Then go topic by topic — each one has a short "What is it" + an "Exam Answer" you can write almost word-for-word in your paper.

---

# OUTLINE — WHAT THIS COURSE COVERS

```
1. PARALLEL COMPUTING — shared memory, one machine, many cores
2. DISTRIBUTED COMPUTING — many machines, network, message passing
3. CLOUD COMPUTING — on-demand internet services, pay-as-you-go
4. CLOUD vs TRADITIONAL — ownership, cost, scaling, access differences
5. CLOUD HISTORY — mainframes → time-sharing → ARPANET → AWS/Azure
6. ADVANTAGES & DISADVANTAGES — cost, speed, scale vs. security, dependency
7. GEOGRAPHY & DATA SOVEREIGNTY — regions, availability zones, legal issues
8. NIST MODEL — 5 characteristics that define cloud computing
9. ENABLING TECHNOLOGIES — virtualization, SOA, web services, multitenancy
10. DEPLOYMENT MODELS — public, private, community, hybrid
11. SERVICE MODELS — IaaS, PaaS, SaaS, FaaS
12. SLI / SLO / SLA — measuring reliability, setting targets, legal agreements
13. SLA TYPES & CHECKLIST — service/customer/multi-level, 5 things to check
14. AVAILABILITY PROBLEMS — formula + step-by-step solutions from lectures
15. LAMP STACK ON AZURE — hands-on lab steps and commands
```

---

# 1. PARALLEL COMPUTING

**Exam Answer:**
Parallel computing involves multiple processors or cores working simultaneously on a **single machine** using **shared memory**. Processors read and write to common memory locations and coordinate through shared memory synchronization. It provides very high speed but has limited scalability since it depends on one machine's capacity. A failure in the machine affects the entire system. Example: GPU rendering an image uses thousands of cores on one graphics card simultaneously.

**Analogy:** One chef using many hands at the same time.

---

# 2. DISTRIBUTED COMPUTING

**Exam Answer:**
Distributed computing involves multiple independent computers (nodes) connected over a **network**, where each node has its **own local memory**. Nodes communicate by **passing messages** rather than sharing memory. It offers massive scalability because you can keep adding more machines, and if one node fails, others continue working. However, speed is moderate compared to parallel computing due to network overhead. Example: Hadoop processes large log files by distributing work across hundreds of servers.

**Analogy:** Many chefs working in different kitchens, coordinating via phone calls.

### Quick Comparison (write this table in exam)

| Aspect | Parallel | Distributed |
|---|---|---|
| Machines | One | Many |
| Memory | Shared | Local per node |
| Communication | Shared memory | Message passing via network |
| Speed | Very high | Moderate |
| Scalability | Limited | Massive |
| Failure impact | High | Low |

### Classify These (from Day 1 task — likely exam question)

| Scenario | Type |
|---|---|
| GPU image rendering | Parallel |
| Hadoop log processing | Distributed |
| Netflix video streaming | Cloud |
| Multi-core CPU program | Parallel |
| Google Drive | Cloud |

---

# 3. CLOUD COMPUTING — DEFINITION

**Exam Answer:**
Cloud computing is the delivery of computing services — including servers, storage, databases, networking, software, analytics, and intelligence — over the Internet ("the cloud") on a **pay-as-you-go** basis. Instead of buying and maintaining physical infrastructure, organizations rent resources from cloud providers and pay only for what they use, similar to how we pay for electricity. This eliminates heavy upfront costs and allows businesses to scale resources up or down instantly based on demand.

**Examples from lectures:** Gmail (email SaaS), Netflix on AWS (streaming), Google Drive (file storage), Ring camera (IoT + cloud processing).

---

# 4. CLOUD vs TRADITIONAL CLIENT-SERVER

**Exam Answer:**
The traditional client-server model requires organizations to own, install, and maintain their own servers in on-premises data centers, with high upfront capital costs and limited scalability. Cloud computing still uses client-server communication but adds three key improvements: **virtualization** (abstracting physical resources), **elastic scaling** (resources grow/shrink on demand), and **service models** (IaaS, PaaS, SaaS). In cloud, a third-party provider owns the infrastructure, users access it over the internet from anywhere, and costs shift from upfront capital expenditure to a pay-as-you-go subscription.

| Aspect | Traditional | Cloud |
|---|---|---|
| Ownership | You own servers | Provider owns infrastructure |
| Cost | Large upfront CapEx | Pay-as-you-go |
| Scaling | Buy more hardware (slow) | Instant elastic scaling |
| Access | Local/VPN only | Internet — any device, anywhere |
| Maintenance | You handle everything | Provider handles infrastructure |

---

# 5. CLOUD HISTORY (know key names and years)

**Exam Answer:**
Cloud computing traces back over 60 years. In 1955, **John McCarthy** proposed the **time-sharing theory** to share expensive computing resources. In 1961, he suggested computing could be sold like a utility (water/electricity). In the mid-1960s, **J.C.R. Licklider** envisioned an interconnected computer system, which led to **ARPANET** in 1969 — the predecessor of the Internet. The modern cloud era began with **Salesforce.com** in 1999 delivering enterprise apps via a website. **Amazon launched AWS** in 2002 and **EC2 in 2006**, making cloud computing commercially available. **Google Apps** and **Microsoft Azure** followed in 2009. Today, public cloud spending exceeds $720 billion.

---

# 6. ADVANTAGES & DISADVANTAGES OF CLOUD

### Advantages (memorize all 5)

**Exam Answer:**
Cloud computing offers five key advantages. **First, cost savings** — it eliminates capital expenses for hardware, data centers, and IT staff. **Second, speed** — resources can be provisioned in minutes with a few clicks. **Third, global scale** — cloud provides elastic scaling to deliver the right amount of resources from the right location at the right time. **Fourth, productivity** — it removes time-consuming tasks like hardware setup and software patching, letting IT focus on business goals. **Fifth, reliability** — cloud providers offer data backup, disaster recovery, and business continuity through mirrored redundant sites across their network.

### Disadvantages (memorize all 4)

**Exam Answer:**
Despite its benefits, cloud has notable drawbacks. **First**, it is not always cheaper long-term — for predictable workloads, owning infrastructure may be more economical, just as renting is not always cheaper than buying. **Second**, there are **security and privacy risks** — sensitive data on shared infrastructure may be vulnerable, and companies may be reluctant to host data alongside rivals. **Third**, cloud requires **internet connectivity** — without it, applications become inaccessible. **Fourth**, even the most advanced companies can be **hacked** — Tesla's AWS account was compromised for crypto mining, and the Capital One breach in 2019 exposed 100 million customers' data due to a misconfigured firewall, costing approximately $300 million.

### Key Breach Cases (for scenario questions)

- **Capital One 2019:** Misconfigured firewall on AWS → 100M+ customers exposed → cost ~$300M. Lesson: misconfigurations are the #1 threat.
- **Azure ChaosDB 2021:** Cosmos DB vulnerability → unauthorized cross-tenant access. Lesson: shared architecture carries inherent risks.
- **AWS S3 Outage 2017:** Widespread outage affected thousands of websites. Lesson: cloud outages have massive blast radius.
- **Tesla AWS hack:** Hackers used Tesla's cloud account to mine Monero cryptocurrency. Lesson: even tech giants are vulnerable.

---

# 7. GEOGRAPHY, REGIONS & AVAILABILITY ZONES

**Exam Answer:**
Cloud computing is affected by two geographic concerns. **First, latency** — if a data center is far from the user, performance will be sluggish. **Second, data sovereignty** — data stored digitally is subject to the laws of the country where it is located. For example, European companies worry that data stored in US data centers could be accessed by US law enforcement. To address these issues, cloud providers organize infrastructure into **regions** and **availability zones**. A **region** is a separate geographic area (e.g., EU London, US West Oregon). An **availability zone (AZ)** consists of one or more data centers within a region, far enough apart that a single disaster won't take both offline, but close enough for rapid failover. Each AZ has independent power and internet connections.

---

# 8. NIST CLOUD MODEL (5 Characteristics)

**Exam Answer:**
According to the National Institute of Standards and Technology (NIST), cloud computing is a model for enabling ubiquitous, convenient, on-demand network access to a shared pool of configurable computing resources that can be rapidly provisioned and released with minimal management effort. NIST defines five essential characteristics:

1. **Broad network access** — cloud services are accessible over the internet from any device including laptops, tablets, and smartphones.
2. **On-demand self-service** — users can provision resources like server time and storage automatically, without needing to contact the provider.
3. **Resource pooling** — the provider serves multiple customers from the same physical resources, with secure logical separation between tenants.
4. **Rapid elasticity** — resources are provisioned and released on-demand or automatically based on triggers, ensuring the application always has the capacity it needs.
5. **Measured service** — resource usage is monitored, measured, and billed transparently based on actual utilization — in short, pay per use.

---

# 9. ENABLING TECHNOLOGIES

### Virtualization

**Exam Answer:**
Virtualization is the process of converting a physical IT resource into a virtual one. It applies to servers (creating virtual machines), storage, and networks. Virtualization is a key enabler for cloud computing because it allows multiple virtual machines to run on a single physical server, enabling resource pooling, tenant isolation, elastic scaling, and efficient resource utilization.

### SOA (Service-Oriented Architecture)

**Exam Answer:**
SOA is a software design approach in which applications are built as a collection of loosely coupled, reusable services. Each service performs a specific business function and communicates with other services over a network using standardized interfaces such as SOAP or REST APIs. Its key features are: **loose coupling** (services are independent), **reusability** (same service used across multiple applications), **interoperability** (services communicate regardless of platform or language), and **standard interfaces** (well-defined contracts). For example, an Online Parking Ticket app may use Google Maps for navigation, an existing payment gateway for payments, and Facebook/Gmail for authentication — each is an independent, replaceable service.

### Web Services

**Exam Answer:**
A web service is a self-describing, self-contained software module available via a network that completes tasks on behalf of a user or application. "Self-describing" means it knows what functions it can perform and what inputs it requires. Web services are the primary technology for implementing SOA.

### Web Evolution

**Exam Answer:**
**Web 1.0** was the static web — simple HTML pages with little interactivity. **Web 2.0** brought dynamic, user-generated content and interactive experiences (YouTube, Facebook, Instagram), all heavily reliant on cloud infrastructure for scalability and storage. **Web 3.0** (the Semantic Web) envisions a decentralized, intelligent, user-centric internet integrating blockchain, AI, and decentralized applications (dApps).

### Multitenancy

**Exam Answer:**
Multitenancy is an architecture in which a single instance of a software application serves multiple tenants (users or user groups), with each tenant's data and configurations logically isolated despite sharing the same physical infrastructure. Think of it as an apartment building — each tenant has their own apartment (data), but they share common infrastructure like elevators and utilities (the application and hardware).

### Internet Architecture (ISP Tiers)

**Exam Answer:**
Cloud connectivity is enabled through a hierarchical ISP topology. **Tier 1** consists of large-scale international providers that oversee massive global networks. **Tier 2** consists of regional providers connected to Tier 1. **Tier 3** consists of local ISPs connected to Tier 2. Data flows from cloud consumers through Tier 3 → Tier 2 → Tier 1 backbone → cloud provider network and back.

---

# 10. DEPLOYMENT MODELS

### Public Cloud

**Exam Answer:**
A public cloud is available to the general public, with data stored on third-party servers managed by the service provider. Users don't need their own hardware — they pay per use or get free tiers. Benefits include **minimal investment**, **high scalability**, and **24/7 uptime**. Limitations include **lower data security** (accessible to all, vulnerable to attacks) and **reliability issues** (shared servers can cause outages, e.g., the 2016 Salesforce CRM disruption).

### Private Cloud

**Exam Answer:**
A private cloud is owned and used by a single organization, also called an internal or corporate cloud. It can be hosted on-premises or externally, but operates on a designated private network. Benefits include **high security, privacy, and reliability**, with full customization. The main limitation is **high cost** — it requires significant investment in hardware, software, and staff training, making it unsuitable for small companies.

### Community Cloud

**Exam Answer:**
A community cloud is shared by several organizations with similar backgrounds, security requirements, and performance needs. It resembles a private cloud but costs are **shared among members**, making it cheaper than private. Benefits include **lower investment than private** and **ease of collaboration**. Limitations include **higher cost than public**, **fixed bandwidth/storage capacity**, and **limited popularity** as it is a relatively new model.

### Hybrid Cloud

**Exam Answer:**
A hybrid cloud combines two or more deployment models (typically private and public). An organization can place mission-critical workloads on a secure private cloud while running less sensitive operations on a cheaper public cloud. This provides a **balance of security and cost-effectiveness** while maintaining strategic control over important assets.

### Comparison Table (draw this in exam)

| Aspect | Public | Private | Community | Hybrid |
|---|---|---|---|---|
| Setup | Easy | Needs IT skills | Needs IT skills | Needs IT skills |
| Security | Low | High | Comparatively high | High |
| Control | Little/none | High | Comparatively high | Comparatively high |
| Scalability | High | High | Fixed | High |
| Cost | Cheapest | Most expensive | Shared | Mid-range |

---

# 11. SERVICE MODELS

### IaaS (Infrastructure as a Service)

**Exam Answer:**
IaaS provides on-demand access to cloud-hosted computing infrastructure — servers, storage, and networking. The provider manages the physical hardware, while the customer configures and manages everything above it: operating system, middleware, runtime, applications, and data. Users can dynamically choose CPU, memory, and storage configurations via a dashboard or APIs. IaaS offers **maximum flexibility and control**. Examples: AWS EC2, Azure VMs, Google Compute Engine.

### PaaS (Platform as a Service)

**Exam Answer:**
PaaS provides a cloud-based platform for developing, running, and managing applications. The provider manages all infrastructure plus the development platform (OS, middleware, runtime), while the developer focuses purely on writing code and managing application data. Development teams collaborate through a GUI across the full application lifecycle — coding, testing, deployment, and feedback. PaaS is ideal for **reducing system administration overhead**. Examples: AWS Elastic Beanstalk, Google App Engine, Red Hat OpenShift.

### SaaS (Software as a Service)

**Exam Answer:**
SaaS provides ready-to-use application software that users access via a web browser, desktop client, or mobile app. The provider manages everything — servers, storage, networking, middleware, application software, and data. Users pay a monthly or annual subscription fee and get instant access without installation. SaaS offers the **easiest management but least control**. Examples: Gmail, Dropbox, OneDrive, Salesforce CRM.

### FaaS (Function as a Service) / Serverless

**Exam Answer:**
FaaS, also known as serverless computing, allows developers to deploy individual functions that run in response to events or triggers without managing any servers. The cloud provider automatically handles provisioning and scaling. It is highly efficient for event-driven tasks. For example, when a user uploads an image, an AWS Lambda function can automatically generate a thumbnail — no server setup or management required. Examples: AWS Lambda, Azure Functions, Google Cloud Functions.

### CRM Scenario (exam favorite — from lecture)

**Exam Answer:**
If a large organization wants to deliver a CRM application, it has three options. **With SaaS**, it picks a ready-made CRM solution (like Salesforce), offloading all management to the vendor but giving up control over features and data. **With PaaS**, it builds a custom CRM on a cloud platform, retaining control over application features while the provider manages infrastructure. **With IaaS**, it builds everything from scratch on cloud servers, gaining complete control over OS, platform, and application, but bearing the full burden of management and maintenance.

### Who Manages What (draw in exam)

| Layer | IaaS | PaaS | SaaS |
|---|---|---|---|
| Infrastructure (servers, storage, network) | Provider | Provider | Provider |
| OS + Middleware + Runtime | **You** | Provider | Provider |
| Application + Data | **You** | **You** | Provider |

**Memory trick:** SaaS = provider does everything. PaaS = you just code. IaaS = you manage everything except hardware.

---

# 12. SLI / SLO / SLA

### Definitions

**Exam Answer:**
**SLI (Service Level Indicator)** is the metric you are measuring — such as uptime percentage, request latency, error rate, or data durability. It tells you how the service is actually performing. **SLO (Service Level Objective)** is the target value for an SLI — for example, "99.95% uptime." It defines what level of performance is acceptable. **SLA (Service Level Agreement)** is a formal legal contract between the provider and customer that includes the SLO plus **consequences** (penalties, service credits) if the target is not met. In short: SLI = what you measure, SLO = how good it should be, SLA = SLO + penalties.

### The Nines Table (memorize)

| Nines | Uptime % | Downtime/month |
|---|---|---|
| 1 | 90% | 3 days |
| 2 | 99% | 7 hours |
| 3 | 99.9% | 43 minutes |
| 4 | 99.99% | 4 minutes |
| 5 | 99.999% | 25 seconds |

Each additional nine exponentially reduces allowed downtime and increases cost/complexity.

Cloud VM providers (Azure, EC2, GCE) typically promise **99.95%** uptime (~22 min downtime/month).

### Reading an SLA — ask 3 things:
1. **Sampling frequency** — how often is the system checked?
2. **Domain of responsibility** — what counts as "up"?
3. **Measurement interval** — over what time period is uptime measured?

### SLA: Contract or Marketing?

**Exam Answer:**
Few people read an SLA in detail until a failure has already happened. In competitive markets, losing a customer is worse than an SLA violation, so providers are motivated to exceed their SLAs. However, the refund credits offered in SLAs usually will not cover the customer's actual business losses. This means SLAs are partly a marketing tool and partly a legal safety net.

### Setting Your SLO

**Exam Answer:**
SLO is not the same as SLA — it is an internal target. Start conservative and increase gradually as you gain experience. Your SLO must be greater than your team's reaction time (no point promising 99.99% if you can't respond in 4 minutes). Know the SLA of your dependencies. If you consistently exceed your SLO by a large margin, schedule a planned outage to avoid setting an implicit (unrealistic) SLA in customers' minds.

---

# 13. SLA TYPES & CHECKLIST

### Three Types of SLA

**Exam Answer:**
**Service-Level SLA** applies the same terms to all customers for a particular service — for example, a provider guarantees 99.9% uptime for all VMs. **Customer-Level SLA** is tailored to a specific customer — for example, resolving high-priority issues within 4 hours for a corporate client. **Multi-Level SLA** is a hierarchical structure addressing corporate, customer, and service levels within one organization.

**Beverages analogy from lecture:** A customized tea/coffee/juice schedule for one customer = Customer-based SLA (personalized, premium). A fixed-price juice stand for everyone = Service-based SLA (standardized).

### 5 Things to Check in Cloud SLA (memorize)

**Exam Answer:**
Before signing a cloud SLA, check five things. **First, availability** — what uptime percentage is promised, and what is the plan for unexpected downtime and alerts. **Second, data ownership** — who owns your data; ideally, all ownership rights remain with the customer. **Third, cloud hardware and software** — what servers and devices the services rely on, so you understand the environment. **Fourth, disaster recovery and backup** — whether the provider offers automatic backups, snapshots, and a detailed disaster recovery plan. **Fifth, customer responsibilities** — what you are liable for, since an SLA is a two-way contract.

### How Often Revise SLAs?

**Exam Answer:**
SLAs should include built-in review intervals since businesses change in size and needs over time. Some vendors build notification workflows that trigger when an SLA is close to being breached, allowing renegotiation. Reviews can cover uptime levels, usage changes, or upgrades to new service tiers.

---

# 14. AVAILABILITY PROBLEMS (5-Mark Section)

### Formula

$$
\text{Availability (\%)} = \left(1 - \frac{\text{Total Downtime}}{\text{Total Agreed Service Time}}\right) \times 100
$$

### Problem 1 — FROM LECTURE (Lec 5, Slide 16)

> **Cloud guarantees 99% availability. App runs 12 hours/day. After one month: 10.75 hours of outage. Is the guarantee violated?**

**Write this in exam:**

Total agreed service time = 12 × 30 = 360 hours
Total downtime = 10.75 hours
Availability = (1 − 10.75/360) × 100 = (1 − 0.02986) × 100 = **97.01%**
Since 97.01% < 99% → **Yes, the provider violated the guarantee.**

---

### Problem 2 — FROM LECTURE (Lec 5, Slide 17)

> **SLA: 99.95% availability, 30 days, 12 hours/day, $50/day.**
> **Credits: <99.95% → 10%, <99% → 25%.**
> **Outages: 5h, 30min, 1h30min, 15min, 2h25min. Find effective cost.**

**Write this in exam:**

**Step 1 — Total downtime:**
5 + 0.5 + 1.5 + 0.25 + 2.4167 = **9.6667 hours**

**Step 2 — Total agreed time:**
30 × 12 = **360 hours**

**Step 3 — Availability:**
(1 − 9.6667/360) × 100 = **97.31%**

**Step 4 — Credit slab:**
97.31% < 99% → **25% credit applies**

**Step 5 — Effective cost:**
Base = 30 × $50 = $1,500
Credit = 25% × $1,500 = $375
**Effective cost = $1,500 − $375 = $1,125**

---

### Practice Problem 3

> **SLA: 99.9%, service runs 24h/day, 30 days. Downtime: 2h 10min. Violated?**

Total time = 24 × 30 = 720 hours
Downtime = 2.1667 hours
Availability = (1 − 2.1667/720) × 100 = **99.70%**
99.70% < 99.9% → **Yes, violated.**

---

### Practice Problem 4

> **SLA: 99.95%, 8h/day, 30 days, $100/day. Outages: 3h, 45min, 1h15min. Credits: <99.95% → 15%, <99% → 30%. Find cost.**

Total time = 8 × 30 = 240 hours
Downtime = 3 + 0.75 + 1.25 = 5 hours
Availability = (1 − 5/240) × 100 = **97.92%**
97.92% < 99% → **30% credit**
Base = $3,000. Credit = $900. **Effective = $2,100.**

---

# 15. LAMP STACK ON AZURE (Lab)

**Exam Answer (if asked about the hands-on):**
LAMP stands for **Linux, Apache, MySQL, PHP** — a complete web hosting stack. In the lab, we deployed it on an Azure Linux VM (Ubuntu 20.04 LTS). We configured Network Security Groups to allow SSH (port 22), HTTP (port 80), and optionally HTTPS (port 443). After connecting via SSH, we updated the system, installed Apache as the web server, MySQL for database management (secured with `mysql_secure_installation`), and PHP for dynamic content. We verified the setup by creating a PHP info page and accessing it via the VM's public IP. This demonstrates deploying cloud-based Linux infrastructure, configuring LAMP components, hosting dynamic PHP applications, and securing the server through firewall rules.

---

# MCQs — 30 QUESTIONS

**1.** Parallel computing processors communicate via →
A) Network B) **Shared memory** C) REST APIs D) Email — **B**

**2.** ARPANET was predecessor of →
A) Salesforce B) **The Internet** C) EC2 D) Drive — **B**

**3.** Time-sharing theory (1955) proposed by →
A) Licklider B) Musk C) **John McCarthy** D) Bezos — **C**

**4.** First enterprise web-delivered app (1999) →
A) Amazon B) Google C) Microsoft D) **Salesforce.com** — **D**

**5.** Amazon EC2 launched in →
A) 1999 B) 2002 C) **2006** D) 2009 — **C**

**6.** NOT a distributed computing trait →
A) Many machines B) **Shared single memory** C) Network D) Low failure impact — **B**

**7.** NOT a cloud advantage →
A) Cost B) Scale C) **Zero breaches** D) Reliability — **C**

**8.** Data sovereignty means data subject to →
A) **Laws of country where data is located** B) Provider HQ laws C) Maritime law D) None — **A**

**9.** Availability Zone is →
A) Billing plan B) **DCs close enough for failover, far enough for disaster isolation** C) Language D) VM type — **B**

**10.** NIST essential characteristics count → **C) 5**

**11.** Measured service means →
A) Free B) **Usage monitored and billed per use** C) Self-measure D) No charges — **B**

**12.** Resources scale up/down automatically →
A) Broad access B) Pooling C) **Rapid elasticity** D) Measured — **C**

**13.** Multitenancy → **B) Single app instance serves multiple tenants with isolation**

**14.** Apartment building analogy refers to → **C) Multitenancy**

**15.** SOA stands for → **B) Service Oriented Architecture**

**16.** ISP hierarchy top-down → **B) Tier 1 → Tier 2 → Tier 3**

**17.** Virtualization is → **B) Converting physical IT resource into virtual one**

**18.** Available to general public → **C) Public cloud**

**19.** Private cloud also called → **B) Internal or corporate cloud**

**20.** Most expensive deployment model → **C) Private**

**21.** Mission-critical workloads in hybrid go on → **B) Private cloud**

**22.** SaaS provides → **C) Ready-to-use software**

**23.** PaaS best for → **B) Developers building applications**

**24.** FaaS also known as → **B) Serverless computing**

**25.** AWS Lambda is → **D) FaaS**

**26.** SLI stands for → **B) Service Level Indicator**

**27.** SLA differs from SLO because SLA includes → **B) Legal/financial consequences**

**28.** 99.99% uptime ≈ downtime/month → **C) 4 minutes**

**29.** NOT in "5 things to check in SLA" → **D) Provider's employee salaries**

**30.** Service-based SLA offers → **B) Same terms for all customers**

---

# SHORT QUESTIONS — EXAM-READY ANSWERS

*Each answer below is 4-6 lines — exactly what you need to write in exam for full marks.*

---

### Q: Differentiate parallel and distributed computing.
Parallel computing uses multiple processors on a single machine with shared memory. Processors coordinate by reading and writing to common memory locations, providing very high speed (e.g., GPU rendering). Distributed computing uses many independent machines connected via a network, each with its own local memory, communicating through message passing (e.g., Hadoop). Parallel is faster but less scalable; distributed is massively scalable but moderate in speed.

### Q: Define cloud computing and explain pay-as-you-go.
Cloud computing is the delivery of computing services — servers, storage, databases, networking, and software — over the Internet on demand. Pay-as-you-go means customers pay only for resources they actually consume, similar to an electricity bill, without large upfront investment. This shifts costs from capital expenditure to operational expenditure and allows businesses to scale resources based on changing needs.

### Q: What are the 5 NIST characteristics of cloud?
(1) **Broad network access** — accessible from any device via internet. (2) **On-demand self-service** — users provision resources automatically without contacting the provider. (3) **Resource pooling** — multiple customers share physical resources with logical isolation. (4) **Rapid elasticity** — resources scale up/down automatically based on demand. (5) **Measured service** — usage is monitored and billed transparently per actual use.

### Q: Compare public, private, community, and hybrid cloud.
**Public cloud** is open to everyone, cheapest, but has the lowest security. **Private cloud** is owned by one organization, offers the highest security and customization, but is the most expensive. **Community cloud** is shared by organizations with similar requirements, balancing cost and security. **Hybrid cloud** combines two or more models — placing sensitive workloads on private and less critical ones on public, achieving a cost-security balance.

### Q: Explain IaaS, PaaS, SaaS with examples.
**IaaS** provides raw infrastructure (servers, storage, networking) — the customer manages OS and applications. Example: AWS EC2. **PaaS** provides a development platform — the provider manages infrastructure while the developer focuses on code. Example: Google App Engine. **SaaS** provides ready-to-use software — the provider manages everything. Example: Gmail, Dropbox. Going from IaaS to SaaS, management ease increases but control decreases.

### Q: What is FaaS? Give an example scenario.
FaaS (Function as a Service), also called serverless computing, allows developers to deploy individual functions that execute in response to events without managing any servers. The cloud provider handles all provisioning and scaling automatically. For example, when a user uploads an image to a web application, an AWS Lambda function automatically generates a thumbnail — no server setup or maintenance is needed.

### Q: What is virtualization and why is it important?
Virtualization is the process of converting physical IT resources (servers, storage, networks) into virtual ones. It is critical for cloud computing because it enables running multiple virtual machines on a single physical server, allowing resource pooling across customers, isolation between tenants, elastic scaling of capacity, and efficient hardware utilization.

### Q: Define SOA and list its key features.
SOA (Service-Oriented Architecture) is a software design approach where applications are built as collections of loosely coupled, reusable services that communicate over a network using standardized interfaces like SOAP or REST APIs. Key features: **loose coupling** (services are independent), **reusability** (one service used in multiple apps), **interoperability** (works across platforms/languages), and **standard interfaces** (well-defined contracts).

### Q: Explain region and availability zone.
A **region** is a geographic area where cloud infrastructure is deployed (e.g., EU London, US West Oregon). An **availability zone (AZ)** consists of one or more data centers within a region that are physically separated enough for disaster isolation but close enough for rapid failover. Each AZ has independent power supplies and internet connections to ensure redundancy.

### Q: What is multitenancy?
Multitenancy is a cloud architecture where a single instance of a software application serves multiple tenants (users or organizations). Each tenant's data and configurations are logically isolated even though they share the same physical infrastructure. It is like an apartment building where each tenant has their own apartment (data) but shares the building's elevators and utilities (hardware and application).

### Q: What is data sovereignty and why does it matter?
Data sovereignty is the concept that data stored digitally is subject to the laws of the country where it is physically located. It matters because companies, especially in Europe, must ensure their data complies with local regulations. If customer data is stored in a US data center, it could be accessed by US law enforcement, creating legal risks. This has driven cloud providers to build regional data centers so organizations can keep data in their own jurisdiction.

### Q: Discuss a cloud security breach and its lesson.
In 2019, a former AWS employee exploited a **misconfigured web application firewall** at Capital One to access sensitive data stored on AWS, affecting over 100 million customers and costing approximately $300 million. Although AWS itself wasn't at fault, the breach demonstrated that cloud security is a **shared responsibility** — the provider secures the infrastructure, but the customer must properly configure firewalls, access controls, and monitoring to prevent unauthorized access.

### Q: What are SLI, SLO, SLA? How do they relate?
**SLI** (Service Level Indicator) is the actual metric measured, such as uptime percentage or error rate. **SLO** (Service Level Objective) is the target for that metric, like 99.95% uptime. **SLA** (Service Level Agreement) is a formal contract that includes the SLO plus legal consequences (penalties/credits) if the target is not met. SLIs feed into SLOs, and SLOs are formalized into SLAs. A team can have internal SLOs without an SLA, but every SLA has an SLO backed by SLIs.

### Q: What happens if an SLA is breached?
When an SLA is breached, the service provider must pay penalties as defined in the agreement — typically **service credits** such as a partial refund of the subscription fee or free additional subscription time. However, these credits usually will not cover the customer's actual business losses. The reputational damage of repeated breaches often causes customer churn, which is more costly to the provider than the credits themselves.

### Q: What are the 3 types of SLA?
**Service-Level SLA** applies the same terms to all customers for a specific service (e.g., 99.9% uptime for all VMs). **Customer-Level SLA** is tailored to a specific customer (e.g., 4-hour issue resolution for a corporate client). **Multi-Level SLA** is hierarchical, with different terms at corporate, customer, and service levels within one organization.

### Q: What 5 things should you check in a cloud SLA?
(1) **Availability** — what uptime is guaranteed and the plan for unexpected downtime. (2) **Data ownership** — who owns your data; ideally the customer retains ownership. (3) **Hardware/software specs** — what infrastructure the service runs on. (4) **Disaster recovery & backup** — provider's DR plan and whether backups are automatic. (5) **Customer responsibilities** — what you are liable for under the contract.

### Q: How is availability calculated?
Availability = (1 − Total Downtime / Total Agreed Service Time) × 100. For example, if a service runs 12 hours/day for 30 days (360 hours total) and experiences 3.6 hours of downtime, availability is (1 − 3.6/360) × 100 = 99%. If the SLA guarantees 99.5%, this would be a violation.

### Q: Why set realistic SLOs?
Unrealistic SLOs like 100% uptime are impossible to achieve and lead to unnecessary spending and false customer expectations. It is best to start conservative and gradually increase SLOs with experience. The SLO must also be greater than your team's reaction time — there is no point promising four-nines (4 min/month downtime) if your team cannot respond that quickly.

### Q: Can an SLO exist without an SLA?
Yes. SLOs are internal objectives that engineering teams set to maintain service quality, even without any external contract. For example, a team may target 99.9% uptime for an internal tool without any formal SLA. SLOs guide engineering decisions and resource allocation, while SLAs are legal agreements with external customers.

---

# SCENARIO ANSWER TEMPLATE (for 15-mark section)

When you get a scenario question, structure your answer like this:

1. **Identify** what type it is (deployment model? service model? SLA type?)
2. **Define** it in 2 sentences
3. **List 2-3 benefits** that apply to the scenario
4. **List 2 risks/limitations**
5. **Suggest a mitigation** (multi-AZ, monitoring, backup, proper IAM configuration)
6. **If numerical:** Formula → total service time → total downtime → availability % → compare with guarantee → check credit slab → compute effective cost

---

# LAMP STACK COMMANDS (if asked for steps)

```
1. SSH:          ssh username@public_ip
2. Update:       sudo apt update && sudo apt upgrade -y
3. Apache:       sudo apt install apache2 -y && sudo systemctl enable --now apache2
4. MySQL:        sudo apt install mysql-server -y && sudo mysql_secure_installation
5. PHP:          sudo apt install php libapache2-mod-php php-mysql -y
6. Restart:      sudo systemctl restart apache2
7. Test:         echo "<?php phpinfo(); ?>" | sudo tee /var/www/html/info.php
8. NSG Ports:    22 (SSH), 80 (HTTP), 443 (HTTPS)
```

---

# LINUX RDP SETUP (bonus from Lec 6)

```
sudo apt-get update
sudo apt-get install xfce4
sudo apt-get install xrdp
echo xfce4-session > ~/.xsession
sudo service xrdp restart
```
- [ ] I can explain SOA + multitenancy + virtualization briefly