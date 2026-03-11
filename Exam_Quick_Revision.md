# PARALLEL & DISTRIBUTED SYSTEMS — COMPLETE EXAM REVISION

> **Exam pattern:** 5 marks (numerical problems from lectures) + 10 MCQs + 15 marks (short questions & scenario-based)
>
> **Strategy:** Core concepts first (60 min) → Tables & comparisons (40 min) → Numerical problems (40 min) → MCQ drill + short Q rehearsal (40 min)
>
> **Active recall:** After each section, cover the page and speak 3 bullet points from memory.

---

# PART A — CORE CONCEPTS (Lecture by Lecture)

---

## 1. Parallel vs Distributed Computing (Lec 1)

**Parallel Computing:**
- Multiple processors/cores working simultaneously on a single machine.
- Shared memory space — processors read/write same memory locations.
- Communication via shared memory synchronization.
- Example: GPU image rendering, multi-core CPU program.

**Distributed Computing:**
- Multiple independent nodes connected via a network.
- Each node has its own local memory — no shared memory.
- Communication via message passing over the network.
- Example: Hadoop log processing, Google Drive sync across devices.

**Analogy (from lecture):**
- Parallel = One chef using many hands.
- Distributed = Many chefs in different kitchens.

### Comparison Table (Lec 1, Slide 6 — memorize this exactly)

| Aspect | Parallel | Distributed |
|---|---|---|
| Machines | One | Many |
| Network | No | Yes |
| Failure impact | High | Low |
| Speed | Very high | Moderate |
| Scalability | Limited | Massive |

### Day 1 Classification Exercise (from lecture — likely exam question)

| Scenario | Parallel | Distributed | Cloud |
|---|---|---|---|
| GPU image rendering | ✓ | | |
| Hadoop log processing | | ✓ | |
| Netflix video streaming | | | ✓ |
| Multi-core CPU program | ✓ | | |
| Google Drive | | | ✓ |

### Day 1 Questions (asked in class)
- **Q: "Are multiple CPU cores active?"** → Yes, parallel computing uses multiple cores simultaneously.
- **Q: "Is memory shared among processes?"** → Yes, parallel processes share memory space.
- **Q: "Why does this represent parallel computing?"** → Because multiple cores on a single machine execute tasks simultaneously using shared memory.

---

## 2. Cloud Computing — Definition & History (Lec 1)

**Definition (memorize):**
Cloud computing is the delivery of computing services — servers, storage, databases, networking, software, analytics, and intelligence — over the Internet ("the cloud") on a **pay-as-you-go** basis.

### Cloud vs Traditional Client-Server (Lec 1, Slides 19-28)

| Aspect | Traditional Client-Server | Cloud Computing |
|---|---|---|
| Ownership | Organization owns servers (on-premises) | Third-party provider owns infrastructure |
| Scalability | Buy more hardware (slow, expensive) | On-demand elastic scaling |
| Cost | Upfront CapEx | Pay-as-you-go / subscription |
| Access | Local network / VPN | Internet — anywhere, any device |
| Maintenance | Organization handles updates, patching | Provider handles maintenance |

**What cloud adds over basic client-server:** hides physical servers, adds virtualization, adds elastic scaling, adds service models (IaaS, PaaS, SaaS).

### Cloud Examples from Lectures
- **Photo editing app:** phone sends image to cloud server for processing (heavy compute offloaded).
- **Smart home camera (Ring/Nest):** IoT device sends video to cloud for motion detection, facial recognition, storage.
- **Google Drive:** upload, edit, manage files in cloud; Google handles storage, processing, sync across devices.
- **Netflix:** uses AWS to scale infrastructure based on streaming demand worldwide.

### Cloud Computing History Timeline

| Year | Event |
|---|---|
| 1950s | Mainframe computers — huge and expensive |
| 1955 | John McCarthy creates time-sharing theory |
| 1961 | McCarthy proposes computing sold as utility (like water/electricity) |
| Mid-1960s | J.C.R. Licklider envisions interconnected computer system |
| 1969 | ARPANET — predecessor of the Internet |
| 1999 | Salesforce.com — first enterprise web-delivered app (CRM) |
| 2002 | Amazon starts AWS |
| 2006 | Amazon EC2 launched — truly commercial cloud compute |
| 2009 | Google Apps & Microsoft Azure launch |
| 2025 | Public cloud spending exceeds $720 billion |

---

## 3. Advantages & Disadvantages of Cloud (Lec 2)

### Advantages (5 points — memorize all)
1. **Cost** — eliminates capital expense of buying hardware, setting up data centers.
2. **Speed** — vast resources provisioned in minutes with few clicks.
3. **Global scale** — elastic scaling: right amount of resources, right time, right location.
4. **Productivity** — removes "racking and stacking" chores; IT focuses on business goals.
5. **Reliability** — data backup, disaster recovery, business continuity via mirrored redundant sites.

### Disadvantages (4 points)
1. **Not always cheaper** long-term — "renting is not always cheaper than buying."
2. **Security concerns** — sensitive data on shared infrastructure; rival companies on same service.
3. **Internet dependency** — no internet = no access to applications.
4. **Vulnerability to breaches** — even advanced companies get hacked.

### Real-World Breach/Outage Cases (from lectures — exam scenario material)

| Incident | What Happened | Key Lesson |
|---|---|---|
| **Tesla AWS hack** | Hackers broke into Tesla's Amazon cloud account to mine cryptocurrency (Monero) | Even tech giants are vulnerable |
| **Capital One 2019** | Former AWS employee exploited misconfigured firewall → 100M+ customers exposed. Cost: ~$300M | Misconfiguration and insider threats are critical risks |
| **Azure ChaosDB 2021** | Vulnerability in Cosmos DB allowed unauthorized access to other users' databases | Shared architecture creates cross-tenant risk |
| **AWS S3 Outage 2017** | Widespread S3 outage affected massive number of websites/services | Proper configuration and monitoring essential |
| **Azure Outage 2020** | Significant outage disrupted various Azure services | Cloud service interruptions have wide blast radius |
| **Salesforce 2016** | CRM disruption caused storage collapse | Public cloud reliability is not guaranteed |

---

## 4. Geography, Regions & Availability Zones (Lec 2)

**Data Sovereignty:** Information stored digitally is subject to the laws of the country where it is located. European companies worry about US-stored data being accessed by US law enforcement → vendors build regional data center networks.

**Two geographic issues:**
1. **Latency** — data center far away = sluggish performance.
2. **Data sovereignty** — legal compliance based on where data is stored.

**Region:** A separate geographic area (e.g., EU London, US West Oregon).

**Availability Zone (AZ):** One or more data centers within a region.
- Far enough apart that one disaster won't take both offline.
- Close enough for rapid failover.
- Each AZ has multiple internet + power connections.

---

## 5. NIST Cloud Model (Lec 2 — Very High Exam Weight)

**NIST Definition (memorize):** Cloud computing is a model for enabling ubiquitous, convenient, on-demand network access to a shared pool of configurable computing resources (networks, servers, storage, applications, services) that can be rapidly provisioned and released with minimal management effort or service provider interaction.

### 5 Essential Characteristics

| # | Characteristic | One-Line Meaning |
|---|---|---|
| 1 | **Broad network access** | Accessible over internet from any device (laptop, tablet, phone) |
| 2 | **On-demand self-service** | Users provision resources automatically without human interaction with provider |
| 3 | **Resource pooling** | Multiple customers served from same physical resources, logically isolated |
| 4 | **Rapid elasticity** | Resources scale up/down on demand or via automation |
| 5 | **Measured service** | Usage monitored, measured, reported, billed transparently (pay per use) |

---

## 6. Cloud Enabling Technologies (Lec 2)

### a) Broadband Networks & Internet Architecture
- Cloud resources require network connectivity → dependency on internetworking.
- ISP hierarchy: **Tier 1** (international backbone) → **Tier 2** (regional) → **Tier 3** (local).
- Cloud consumers → ISP (cloud carrier) → backbone ISP → cloud provider network.

**Data flow:** Consumer request → consumer network → ISP cloud carrier → backbone ISP → cloud provider network → response back same path in reverse.

### b) Virtualization
- Converting a **physical** IT resource into a **virtual** one.
- Applies to: servers (VMs), storage, networks.
- Key enabler for cloud resource pooling and elasticity.

### c) SOA (Service-Oriented Architecture)
- Applications built as **loosely coupled, reusable services**.
- Each service performs a specific business function.
- Communication via **standardized interfaces** (SOAP, REST APIs).

**Key features:** Loose coupling, Reusability, Interoperability, Standard interfaces.

**Case Study from lecture:** Online Parking Ticket app uses:
- Google Maps (maps service)
- Existing payment gateway (payments)
- Facebook/Gmail (authentication)
- Services are reusable and replaceable without affecting others.

### d) Web Services
- **Self-describing, self-contained** software modules available via network.
- They know what functions they can perform and what inputs they need.

### e) Web Evolution
- **Web 1.0:** Static HTML pages, little interactivity.
- **Web 2.0:** Dynamic content, user-generated content (YouTube, Facebook, Instagram rely on cloud).
- **Web 3.0:** Semantic web — decentralized, AI-powered, blockchain, dApps.

### f) Multitenancy
- Single instance of software serves **multiple tenants** with data/config isolation.
- **Analogy:** Apartment building — each tenant has own apartment (data) but shares elevators, hallways (hardware/app).

---

## 7. Cloud Deployment Models (Lec 3)

### Public Cloud
- Available to general public, third-party servers.
- Provider manages everything — no user hardware needed.
- Pay-per-use or free.
- **Benefits:** Minimal investment, high scalability, 24/7 uptime.
- **Limitations:** Data security/privacy concerns, reliability issues (shared servers).

### Private Cloud
- Owned by one specific company ("internal" or "corporate" model).
- Can be hosted on-premises or externally, but on a designated private network.
- **Benefits:** High security, privacy, reliability; customizable.
- **Limitations:** Very expensive (hardware, software, training); not for small companies.

### Community Cloud
- Shared by several organizations with similar backgrounds/requirements.
- Like private cloud but multi-organization.
- **Benefits:** Cheaper than private, easy collaboration, shared costs.
- **Limitations:** Higher cost than public, fixed bandwidth/storage, not widely popular yet.

### Hybrid Cloud
- Combination of two or more models (e.g., private + public).
- Mission-critical on private, less sensitive on public.
- **Benefits:** Balance of security and cost-effectiveness.

### Master Comparison Table (Lec 3, Slide 19 — memorize)

| Aspect | Public | Private | Community | Hybrid |
|---|---|---|---|---|
| Ease of setup | Easy | Needs IT expertise | Needs IT expertise | Needs IT expertise |
| Security/Privacy | Low | High | Comparatively high | High |
| Data control | Little to none | High | Comparatively high | Comparatively high |
| Reliability | Low | High | Comparatively high | High |
| Scalability | High | High | Fixed capacity | High |
| Cost | Cheapest | Most expensive | Shared cost | Mid-range |
| In-house hardware | No | Depends | Depends | Depends |

---

## 8. Cloud Service Models (Lec 3)

### "As a service" — the key difference from traditional IT
- Traditional IT: buy, install, manage, maintain everything yourself.
- Cloud: provider owns/manages/maintains; customer consumes via internet, pays subscription or pay-as-you-go.

### IaaS (Infrastructure as a Service)
- On-demand access to servers, storage, networking.
- Customer configures/manages OS, runtime, apps.
- Access via dashboard or APIs; dynamically choose CPU, memory, storage.
- **Examples:** AWS EC2, Azure VMs, Google Compute Engine.
- **Best for:** Maximum flexibility, custom-built apps, data storage.

### PaaS (Platform as a Service)
- Cloud-based platform for developing, running, managing applications.
- Provider handles infrastructure + platform software.
- Developer focuses on code; collaborates via GUI across full app lifecycle.
- **Examples:** AWS Elastic Beanstalk, Google App Engine, Azure, Red Hat OpenShift.
- **Best for:** Reducing system admin overhead, focusing on app development.

### SaaS (Software as a Service)
- Ready-to-use application software; pay monthly/annual fee.
- Provider manages everything (servers, storage, networking, middleware, app, data).
- **Examples:** Gmail, Dropbox, OneDrive, Salesforce.
- **Best for:** Out-of-the-box business solutions (email, CRM, file storage).

### FaaS (Function as a Service) / Serverless
- Deploy individual functions that run in response to events/triggers.
- Abstracts away all server management.
- Highly efficient for event-driven tasks.
- **Examples:** AWS Lambda, Azure Functions, Google Cloud Functions.
- **Lecture scenario:** Image upload → Lambda auto-generates thumbnails — no server setup needed.

### CRM Scenario from Lecture (Exam-ready)
A large org wants a CRM for its sales team. Three options:
1. **SaaS CRM** → offload all management, give up control over features/data/security.
2. **PaaS** → build custom CRM; offload infrastructure management; retain control over app features but manage app + data.
3. **IaaS** → build own platform + app on cloud infrastructure; complete control over OS and servers but maximum management burden.

### Who Manages What?

| Component | On-Premises | IaaS | PaaS | SaaS |
|---|---|---|---|---|
| Networking | You | Provider | Provider | Provider |
| Storage | You | Provider | Provider | Provider |
| Servers | You | Provider | Provider | Provider |
| Virtualization | You | Provider | Provider | Provider |
| OS | You | **You** | Provider | Provider |
| Middleware | You | **You** | Provider | Provider |
| Runtime | You | **You** | Provider | Provider |
| Data | You | **You** | **You** | Provider |
| Applications | You | **You** | **You** | Provider |

### Market Share (2023, from lecture)
- SaaS: ~55.8% market share (dominant).
- IaaS: $150.3B spending (31% YoY growth).
- PaaS: $139B spending (24% YoY growth).

---

## 9. SLI, SLO, SLA (Lec 5 & 6 — Problem Section Worth 5 Marks)

### Definitions (memorize exactly)

| Term | Full Form | Meaning | Key Question |
|---|---|---|---|
| **SLI** | Service Level Indicator | What you are measuring | What metric? |
| **SLO** | Service Level Objective | How good should it be? | What target? |
| **SLA** | Service Level Agreement | SLO + consequences (legal contract) | What happens if breached? |

### SLI Examples
- Availability/Uptime of service.
- Number of successful transactions/requests.
- Consistency and durability of data.

### SLO Examples
- Durability of disks: 99.9%.
- Availability of service: 99.95%.
- Successful requests: 99.999%.
- Start conservative, gradually increase. SLO ≠ SLA.

### SLA Examples
- Penalty: partial refund of subscription fee.
- Penalty: additional subscription time for free.
- Provider must clearly define **domain of responsibility** (what failures they're accountable for).

### The "Nines" Table (Lec 5, Slide 6 — memorize)

| Nines | Uptime | Downtime/month |
|---|---|---|
| 1 nine | 90% | 3 days |
| 2 nines | 99% | 7 hours |
| 3 nines | 99.9% | 43 minutes |
| 4 nines | 99.99% | 4 minutes |
| 5 nines | 99.999% | 25 seconds (~5 min/year) |

> Each additional nine exponentially reduces allowable downtime, increasing complexity and cost.

### Reading an SLA — 3 things to ask:
1. **Sampling frequency** — how often is system checked?
2. **Domain of responsibility** — what does "up" mean?
3. **Measurement interval** — over what time period?

### Cloud VM Providers (from lecture)
- Azure, EC2, GCE promise **99.95% uptime** (~22 min downtime/month).
- 1-minute sampling frequency.
- GCE doesn't count outages <5 minutes.

### SLA Implications
**For provider:** hardware/software rarely fails, or they can fix quickly.
**For you (customer):** need multiple VMs, multiple failure domains, monitoring, tolerance of planned outages, automatic provisioning.

### "SLA: contract, or marketing?"
- Few people read SLA until failure happens.
- Customer loss is worse than SLA violation.
- Credits likely won't cover YOUR actual losses.

### Setting Your SLO (from lecture)
- SLO ≠ SLA.
- Know your application requirements.
- Be conservative at first, gain experience.
- SLO must be > reaction time.
- Know SLA of your dependencies.
- Should you exceed SLO? Yes — gives operational headroom. But don't set implicit SLA. If exceeding too much, schedule an outage!

### Types of SLA (Lec 6)

| Type | Description | Example |
|---|---|---|
| **Service-Level SLA** | Same for all customers for a particular service | Cloud provider guarantees 99.9% uptime for all VMs |
| **Customer-Level SLA** | Tailored to specific customer | IT provider commits to resolving high-priority issues within 4 hours for corporate client |
| **Multi-Level SLA** | Hierarchical — corporate + customer + service levels | Different tiers within one organization |

**Beverages analogy from lecture:**
- Customer A gets custom tea/coffee/juice schedule = **Customer-based SLA** (personalized, premium price).
- Stand offering juices at fixed prices to everyone = **Service-based SLA** (standardized terms for all).

### 5 Things to Check in Cloud SLA (Lec 6 — memorize all 5)
1. **Availability** — uptime promise, planned downtime policy, alert procedures.
2. **Data ownership** — who owns your data; ideally ownership stays with user.
3. **Cloud hardware/software** — what servers/devices; helps understand environment.
4. **Disaster recovery & backup** — provider's DR plan; auto backups; who activates them.
5. **Customer responsibilities** — what YOU are liable for.

### How often revise SLAs?
- SLAs should have review intervals built in.
- Some vendors trigger notifications when close to breach for renegotiation.
- Covers changes in scale, uptime levels, service tier upgrades.

### Availability Formula

$$
\text{Availability}(\%) = \left(1 - \frac{\text{Total Downtime}}{\text{Total Agreed Service Time}}\right) \times 100
$$

- **Agreed service time** = expected hours service should be operational.
- **Downtime** = time during agreed hours when service was unavailable.

---

# PART B — SOLVED NUMERICAL PROBLEMS (From Lectures — 5 Marks Section)

---

## Problem 1 (Lec 5, Slide 16 — EXACT lecture problem)

> **A cloud guarantees service availability of 99% of time. A third-party application runs in the cloud for 12 hours/day. At the end of one month, there was an outage of 10.75 hours. Has the provider violated the initial availability guarantee?**

**Solution:**

**Step 1:** Total agreed service time = 12 hours/day × 30 days = **360 hours**

**Step 2:** Total downtime = **10.75 hours**

**Step 3:** Availability = $(1 - \frac{10.75}{360}) \times 100 = (1 - 0.02986) \times 100 = 97.01\%$

**Step 4:** Compare: 97.01% < 99%

**Answer: Yes, the provider has violated the guarantee.** Actual availability is 97.01%, which is below the guaranteed 99%.

---

## Problem 2 (Lec 5, Slide 17 — EXACT lecture problem with service credits)

> **Company X uses cloud service from provider P with these terms:**
> - Availability guarantee: 99.95%
> - Service period: 30 days
> - Max service hours/day: 12 hours
> - Cost: $50/day
> - Credit policy: <99.95% → 10% credit; <99% → 25% credit
> - Actual outages: 5 hrs, 30 mins, 1 hr 30 mins, 15 mins, 2 hrs 25 mins
>
> **Compute the effective cost payable.**

**Solution:**

**Step 1: Total downtime**

| Outage | Hours |
|---|---|
| 5 hours | 5.0000 |
| 30 minutes | 0.5000 |
| 1 hour 30 minutes | 1.5000 |
| 15 minutes | 0.2500 |
| 2 hours 25 minutes | 2.4167 |
| **Total** | **9.6667** |

**Step 2: Total agreed service time**
= 30 days × 12 hours/day = **360 hours**

**Step 3: Actual availability**
= $(1 - \frac{9.6667}{360}) \times 100 = (1 - 0.02685) \times 100 = 97.31\%$

**Step 4: Determine credit slab**
- 97.31% < 99% → **25% service credit applies**

**Step 5: Compute effective cost**
- Base cost = 30 × $50 = **$1,500**
- Credit = 25% × $1,500 = **$375**
- **Effective cost payable = $1,500 − $375 = $1,125**

---

## Practice Problem 3 (Likely exam variant)

> **A cloud SLA guarantees 99.9% availability. Service runs 24 hours/day for 30 days. Actual downtime recorded: 2 hours 10 minutes. Is the SLA violated?**

**Solution:**

- Total agreed time = 24 × 30 = **720 hours**
- Downtime = 2h 10m = **2.1667 hours**
- Availability = $(1 - \frac{2.1667}{720}) \times 100 = 99.699\%$
- 99.9% allowed downtime = 720 × 0.001 = **0.72 hours (43.2 minutes)**
- 2.1667 > 0.72 → **Yes, SLA is violated.** Actual availability (99.70%) < guaranteed (99.9%).

---

## Practice Problem 4 (Another credit calculation variant)

> **SLA: 99.95% uptime, 8 hours/day, 30 days, $100/day. Outages: 3h, 45min, 1h15min. Credit: <99.95% → 15%, <99% → 30%. Find effective cost.**

**Solution:**

- Total agreed time = 8 × 30 = **240 hours**
- Downtime = 3 + 0.75 + 1.25 = **5 hours**
- Availability = $(1 - \frac{5}{240}) \times 100 = 97.92\%$
- 97.92% < 99% → **30% credit**
- Base cost = 30 × $100 = $3,000
- Credit = 30% × $3,000 = $900
- **Effective cost = $3,000 − $900 = $2,100**

---

# PART C — MCQs (10 Marks Section)

---

### 30 MCQs Covering All Lectures

**Lec 1 — Parallel, Distributed, Cloud Basics**

**1.** In parallel computing, processors communicate via:
- A) Network messages
- B) Shared memory
- C) REST APIs
- D) Email notifications

**Answer: B**

**2.** ARPANET was the predecessor of:
- A) Salesforce
- B) The Internet
- C) Amazon EC2
- D) Google Drive

**Answer: B**

**3.** Who proposed the theory of time-sharing in 1955?
- A) J.C.R. Licklider
- B) Elon Musk
- C) John McCarthy
- D) Jeff Bezos

**Answer: C**

**4.** Which company first delivered enterprise applications via a website in 1999?
- A) Amazon
- B) Google
- C) Microsoft
- D) Salesforce.com

**Answer: D**

**5.** Amazon EC2 launched as a commercial cloud service in:
- A) 1999
- B) 2002
- C) 2006
- D) 2009

**Answer: C**

**6.** Which is NOT a characteristic of distributed computing?
- A) Many machines
- B) Shared single memory
- C) Network communication
- D) Low failure impact per node

**Answer: B**

**Lec 2 — Cloud Advantages, NIST, Enabling Tech**

**7.** Which is NOT an advantage of cloud computing?
- A) Cost reduction
- B) Global scale
- C) Guaranteed zero security breaches
- D) Reliability

**Answer: C**

**8.** Data sovereignty means data is subject to:
- A) The laws of the country where it is located
- B) The laws of the cloud provider's headquarters
- C) International maritime law
- D) No legal jurisdiction

**Answer: A**

**9.** An Availability Zone is:
- A) A billing plan
- B) One or more data centers that are close enough for failover but far enough for disaster isolation
- C) A programming language
- D) A type of virtual machine

**Answer: B**

**10.** According to NIST, how many essential characteristics does cloud computing have?
- A) 3
- B) 4
- C) 5
- D) 7

**Answer: C**

**11.** "Measured service" means:
- A) Services are free
- B) Usage is monitored, measured, and billed based on utilization
- C) Users measure their own hardware
- D) Cloud providers don't charge anything

**Answer: B**

**12.** Which NIST characteristic means resources scale up/down automatically?
- A) Broad network access
- B) Resource pooling
- C) Rapid elasticity
- D) Measured service

**Answer: C**

**13.** Multitenancy is best described as:
- A) One application instance per customer
- B) Single app instance serves multiple tenants with logical isolation
- C) Each customer gets their own physical server
- D) No data isolation between customers

**Answer: B**

**14.** The apartment building analogy in lectures refers to:
- A) IaaS
- B) Virtualization
- C) Multitenancy
- D) Hybrid Cloud

**Answer: C**

**15.** SOA stands for:
- A) Software Oriented Application
- B) Service Oriented Architecture
- C) System Of Automation
- D) Server Operating Architecture

**Answer: B**

**16.** The ISP hierarchy from top to bottom is:
- A) Tier 3 → Tier 2 → Tier 1
- B) Tier 1 → Tier 2 → Tier 3
- C) All tiers are equal
- D) Tier 2 → Tier 1 → Tier 3

**Answer: B**

**17.** Virtualization is the process of:
- A) Deleting files
- B) Converting a physical IT resource into a virtual one
- C) Buying new hardware
- D) Writing web applications

**Answer: B**

**Lec 3 — Deployment & Service Models**

**18.** Which deployment model is available to the general public?
- A) Private
- B) Community
- C) Public
- D) Hybrid

**Answer: C**

**19.** A private cloud is also called:
- A) Community cloud
- B) Internal or corporate cloud
- C) Public cloud
- D) Serverless cloud

**Answer: B**

**20.** Which deployment model is most expensive?
- A) Public
- B) Community
- C) Private
- D) Hybrid

**Answer: C**

**21.** In a hybrid cloud, mission-critical workloads are typically placed on:
- A) Public cloud
- B) Private cloud
- C) Community cloud
- D) None

**Answer: B**

**22.** SaaS provides:
- A) Raw computing infrastructure
- B) Development platform
- C) Ready-to-use application software
- D) Only networking

**Answer: C**

**23.** PaaS is best suited for:
- A) End users
- B) Developers building applications
- C) Hardware manufacturers
- D) Network engineers

**Answer: B**

**24.** FaaS is also known as:
- A) Full-stack computing
- B) Serverless computing
- C) Mainframe computing
- D) Personal computing

**Answer: B**

**25.** AWS Lambda is an example of:
- A) IaaS
- B) PaaS
- C) SaaS
- D) FaaS

**Answer: D**

**Lec 5 & 6 — SLI, SLO, SLA**

**26.** SLI stands for:
- A) Service Level Integration
- B) Service Level Indicator
- C) System Level Interface
- D) Software Level Instruction

**Answer: B**

**27.** SLA differs from SLO primarily because SLA includes:
- A) Just a target number
- B) Legal/financial consequences for violation
- C) Only monitoring tools
- D) Software licenses

**Answer: B**

**28.** 99.99% uptime means approximately how much downtime per month?
- A) 7 hours
- B) 43 minutes
- C) 4 minutes
- D) 25 seconds

**Answer: C**

**29.** Which is NOT one of the 5 things to check in a cloud SLA?
- A) Data ownership
- B) Disaster recovery
- C) Customer responsibilities
- D) Provider's employee salaries

**Answer: D**

**30.** A service-based SLA offers:
- A) Different terms per customer
- B) Standardized service with same terms for all customers
- C) No written agreement
- D) Hardware only

**Answer: B**

---

# PART D — SHORT QUESTIONS & SCENARIO ANSWERS (15 Marks Section)

---

## Questions from Lecture Slides (Lec 6, Slide 16 — "Questions to Ponder")
*These are DIRECTLY from the slides — very high chance of appearing.*

### Q1: How does an SLI help measure system performance?
SLIs are measurable parameters (like uptime, successful requests, data durability) that quantify system health over predefined intervals. By tracking SLIs, teams identify when performance degrades below acceptable levels and can take corrective action.

### Q2: How do SLIs relate to SLOs?
SLIs are the actual measured values; SLOs are the targets set for those SLIs. For example, if the SLI is "uptime percentage" and the measured value is 99.97%, the SLO would be the target like "99.95% uptime." SLOs give meaning to SLIs by defining what is "good enough."

### Q3: How does an SLA differ from an SLO?
An SLO is an internal target for a metric (e.g., 99.95% uptime). An SLA is a formal legal contract that includes the SLO plus consequences (penalties, credits) if the SLO is not met. SLA = SLO + consequences.

### Q4: What happens if an SLA is breached?
The service provider must pay penalties as defined in the agreement — typically service credits (partial refund of subscription or free additional subscription time). However, credits usually won't cover the customer's actual losses.

### Q5: Can an SLO exist without an SLA? Why or why not?
Yes. SLOs are internal objectives that teams set for themselves to maintain quality, even without any external contract. A team may set an SLO of 99.9% uptime for internal services without any formal SLA. SLOs guide engineering decisions; SLAs are business/legal agreements.

### Q6: What are some common SLIs in a web service?
- Availability/uptime percentage
- Request latency (response time)
- Error rate (% of failed requests)
- Throughput (requests per second)
- Data durability and consistency

### Q7: How do you calculate an SLI for system uptime?
Availability = $(1 - \frac{\text{Total Downtime}}{\text{Total Agreed Service Time}}) \times 100$. Example: Service runs 720 hours/month with 36 minutes downtime → Availability = $(1 - \frac{0.6}{720}) \times 100 = 99.917\%$.

### Q8: Why is it important to set realistic SLOs?
Unrealistic SLOs (e.g., 100% uptime) are impossible to achieve, cause unnecessary spending, and create false expectations. Start conservative, gain experience, then gradually increase. Also, SLO must be greater than your team's reaction time.

### Q9: Who defines the terms of an SLA?
Both the service provider and customer negotiate SLA terms together before initiating business. The provider proposes standard terms, and customers may negotiate specific clauses (availability, credits, support levels).

### Q10: What role do SLIs play in monitoring system health?
SLIs serve as real-time health indicators. Monitoring dashboards track SLIs continuously. When SLIs drop below SLO thresholds, alerts trigger, enabling teams to respond before SLA breaches occur.

### Q11: How can SLAs impact customer satisfaction?
If SLAs are met, customers trust the provider. If breached repeatedly, customers lose confidence and switch providers. Credit refunds rarely compensate for actual business losses, so maintaining SLAs is critical for retention.

---

## Other High-Probability Short Answer Questions

### Q12: Differentiate parallel and distributed computing with example.
Parallel computing uses multiple processors on ONE machine with SHARED memory (e.g., GPU rendering an image). Distributed computing uses MANY machines over a NETWORK, each with LOCAL memory, communicating via message passing (e.g., Hadoop processing logs across a cluster). Parallel is fast but limited in scalability; distributed is massively scalable but moderate in speed.

### Q13: Define cloud computing and explain pay-as-you-go model.
Cloud computing is the delivery of computing services (servers, storage, databases, software) over the Internet on demand. Pay-as-you-go means customers only pay for resources they actually consume, similar to an electricity bill — no large upfront investment, just usage-based billing.

### Q14: Explain 5 NIST cloud characteristics.
1. **Broad network access:** Services accessible over internet from any device.
2. **On-demand self-service:** Users provision resources automatically without contacting provider.
3. **Resource pooling:** Provider serves multiple customers from shared physical resources with logical separation.
4. **Rapid elasticity:** Resources scale up/down automatically based on demand.
5. **Measured service:** Usage is metered, monitored, and billed transparently.

### Q15: Compare public, private, community, and hybrid cloud.
**Public:** Open to everyone, cheapest, lowest security. **Private:** One organization, most expensive, highest security. **Community:** Shared by similar organizations, shared cost, moderate security. **Hybrid:** Mix of models — sensitive work on private, rest on public; balanced cost and security.

### Q16: Explain IaaS vs PaaS vs SaaS with one example each.
**IaaS** provides infrastructure (servers, storage, network) — customer manages OS and apps. Example: AWS EC2.
**PaaS** provides a platform for building/deploying apps — provider manages infrastructure. Example: Google App Engine.
**SaaS** provides ready-to-use software — provider manages everything. Example: Gmail, Dropbox.

### Q17: What is virtualization and why is it important in cloud?
Virtualization converts physical IT resources (servers, storage, networks) into virtual ones. It is critical for cloud because it enables resource pooling (multiple VMs on one physical server), isolation between tenants, elastic scaling, and efficient resource utilization.

### Q18: Define SOA and list key features.
SOA (Service-Oriented Architecture) is a software design approach where applications are built as collections of loosely coupled, reusable services communicating via standardized interfaces (SOAP, REST). Key features: loose coupling, reusability, interoperability, standard interfaces.

### Q19: Explain region and availability zone.
A **region** is a geographic area where cloud infrastructure is deployed (e.g., US East, EU London). An **availability zone** is one or more data centers within a region — physically separated enough for disaster isolation but close enough for rapid failover, each with independent power and network connections.

### Q20: Discuss one cloud breach/outage and lesson learned.
**Capital One Data Breach (2019):** A former AWS employee exploited a misconfigured web application firewall to access data of 100M+ customers stored on AWS. Cost was ~$300 million. Lesson: Cloud security is a shared responsibility; misconfigurations in customer-managed components (not the provider's fault) can cause massive breaches. Proper configuration, monitoring, and access controls are essential.

---

## Scenario-Based Answer Template (Use in Exam)

When given a scenario, structure your answer:

1. **Identify** the model/type (deployment model, service model, SLA type).
2. **State 2-3 benefits** relevant to the scenario.
3. **State 2 risks/limitations** that apply.
4. **Suggest mitigation** (e.g., multi-AZ deployment, monitoring, strong IAM, backups).
5. **If numerical:** Write formula → compute total service time → compute downtime → calculate availability % → compare with guarantee → determine credit slab → compute effective cost.

---

# PART E — LAMP Stack on Azure (Hands-On Lab)

**LAMP = Linux + Apache + MySQL + PHP**

### Steps from Activity

| Step | Command/Action |
|---|---|
| 1. Provision VM | Azure Portal → Ubuntu 20.04 LTS, ≥2 vCPUs, 2GB RAM |
| 2. Configure NSG | Allow Port 22 (SSH), Port 80 (HTTP), Port 443 (HTTPS optional) |
| 3. SSH Connect | `ssh <username>@<public_ip>` |
| 4. Update system | `sudo apt update && sudo apt upgrade -y` |
| 5. Install Apache | `sudo apt install apache2 -y` then `sudo systemctl enable --now apache2` |
| 6. Install MySQL | `sudo apt install mysql-server -y` then `sudo mysql_secure_installation` |
| 7. Install PHP | `sudo apt install php libapache2-mod-php php-mysql -y` then `sudo systemctl restart apache2` |
| 8. Test PHP | `echo "<?php phpinfo(); ?>" \| sudo tee /var/www/html/info.php` → access `http://<IP>/info.php` |

### Learning Outcomes
- Deploy cloud-based Linux infrastructure for web hosting.
- Install, configure, and secure LAMP stack components.
- Host and verify dynamic PHP-based applications.
- Ensure security through firewall rules and NSG configurations.

---

# PART F — LINUX RDP SETUP (Lec 6 Bonus)

```bash
# Method 1
sudo apt-get update
sudo apt-get install xfce4
sudo apt-get install xrdp
echo xfce4-session > ~/.xsession
sudo service xrdp restart

# Method 2
sudo apt install ubuntu-desktop -y
sudo apt-get -y install xrdp
sudo systemctl enable xrdp
```

---

# FINAL 15-MINUTE SPEED CHECKLIST

- [ ] I can define Parallel, Distributed, Cloud in one sentence each
- [ ] I can classify GPU rendering / Hadoop / Netflix / Google Drive correctly
- [ ] I can list all 5 NIST characteristics without looking
- [ ] I can name 4 deployment models with one benefit and one limitation each
- [ ] I can compare IaaS / PaaS / SaaS in terms of who manages what
- [ ] I can explain FaaS with the image thumbnail example
- [ ] I can write the availability formula from memory
- [ ] I can solve a service credit problem in under 3 minutes
- [ ] I can define SLI vs SLO vs SLA and give one example each
- [ ] I can list 5 things to check in a cloud SLA
- [ ] I can name 3 types of SLA (service, customer, multi-level)
- [ ] I recall the nines table (90%, 99%, 99.9%, 99.99%, 99.999%)
- [ ] I can explain one real breach (Capital One) with lesson learned
- [ ] I can explain SOA + multitenancy + virtualization briefly