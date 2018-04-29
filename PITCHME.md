# Mocking Database 

#### By Andres Felipe Rincon

---
# Agenda

- Basics
- Mocking a database
- Approaches
    - Living database. 
     - Embedded
     - Local


---

# Basics

---
## Common Problems
![Figure1](assets/image/TraditionalManualTestingProblems.jpg)

Note:
The most frequent problems when we are testing a system are the external dependencies, so the tests turn fragile since there are many moving parts.
---
## Solution

---
### Service Virtualization
![Figure2](assets/image/ManualTestingSolutionWithServiceV.jpg)

---

- Create a testing system before integration testing 
- Using **virtual services** or **stubs** instead of the real ones  

Note: 
One way of solving the issues of too many dependencies and too many moving parts is by doing system testing before integration testing with external backend systems (Figure 2). Using virtual services or stubs, allow you to decouple the testing from the real backend systems. The problems mentioned above, either disappear or lose priority. People are happy for a while. 

---
## Concepts

---
### Stubs

Minimal implementation of an interface that normally return hardcoded data

---

### Mock 

Programmable interface observer, that verifies the outputs against expectations defined by the test.

---
### Virtual Services

**Test double** often provided as SaaS, it's always called remotely.  

A virtual service is often created by recording traffic using one of the service virtualization platforms instead of building the interaction pattern from scratch based on interface or API documentation.

---
### Test Double

Generic term for any kind of pretend object used in place of a real object for testing purposes.

---

Common categories of test double used by developers:

- dummy object (a string “Mike”)
- stub (a StubUserRepository class that always returns user object representing a male named John, age 32, living in US)
- spy (a SpyHttpResponse class that records all invocations of the onPost method)
- fake (a FakeDatabase class which persists to an in memory H2 database instead of the DB2 production ­system)
- mock (a dynamic proxy implementation of OrderObserver interface, implemented by Mockito and used in a unit test)

---
Common categories of a test double used for testing and quality assurance:

- stub (a servlet in a WAR file created using SoapUI and deployed to a remote Jetty instance at http://testEnv.mycompany.com/getWeatherService)
- virtual service (an artifact created with a service virtualization tool and deployed to a remote shared virtual service environment at http://vsenv.mycompany.com:9034/getWeatherService)

---
## What should we use?

|   |data source| created by | used by|
|---|-----------|------------|--------| 
| Stub | Hardcoded data | DEVs sometimes testers| DEVs sometimes testers|
| Mock | Data set up by the test | DEVS | DEVs |
| Virtual Service | Recorded data | Mostly testers | Mostly testers |