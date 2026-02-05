# Cloud Migration Assessment – Digital Estate & Planning

## 1) Digital Estate Understanding

### What is a Digital Estate
A digital estate refers to all the IT assets an organization currently owns and manages. This includes servers, applications, databases, operating systems, storage, networking components, and identity services.  

In this scenario, the digital estate consists of the on-premises VMware servers:
- WEB-01
- APP-01
- DB-01
- DC-01
- FILE-01

---

### Why Digital Estate Understanding Matters Before Migration
Understanding the digital estate is important because it gives a clear picture of what needs to be migrated to Azure. It helps identify workloads, dependencies, system requirements, and potential issues. Without understanding the current environment, migration planning becomes risky and unreliable.

---

### Risks of Migrating Without Discovery and Assessment
1. **Unexpected outages** – Applications may fail if dependent servers are migrated separately.  
2. **Incorrect sizing and high costs** – Resources may be over- or under-provisioned in Azure.  
3. **Security and compatibility issues** – Unsupported operating systems or configurations may block migration.

---

## 2) Discovery & Assessment Approach (Azure Migrate)

### Type of Discovery
Azure Migrate uses a lightweight appliance that performs **agentless discovery**. The appliance connects to the on-premises VMware environment and continuously collects information without installing agents on individual servers.

---

### Data Collected
Azure Migrate collects:
- Server configuration details (CPU, memory, disks, NICs)
- Operating system information
- Installed applications and roles
- Performance data (CPU, memory usage, disk IOPS)
- Application and workload metadata

---

### Workloads Discovered in This Environment
Azure Migrate would discover:
- **WEB-01** – IIS web server  
- **APP-01** – Application server  
- **DB-01** – SQL Server database  
- **DC-01** – Active Directory domain controller  
- **FILE-01** – File server with legacy OS  

---

## 3) Dependency Analysis

### Identified Dependencies
- **WEB-01 → APP-01** (web server relies on application server)  
- **APP-01 → DB-01** (application depends on database)  
- **All servers → DC-01** (authentication and identity services)  
- **Users → FILE-01** (file access services)

---

### Why Dependency Analysis Prevents Outages
Dependency analysis ensures that interconnected servers are migrated together or in the correct order. This prevents application failures, authentication issues, and data access problems during migration.

---

### Proposed Migration Group
A logical migration group would be:
- **WEB-01**
- **APP-01**
- **DB-01**

These servers work together to deliver the core application and should be migrated as a unit.

---

## 4) Azure Readiness & Suitability

| Server  | Azure Readiness        | Justification |
|-------|------------------------|---------------|
| WEB-01 | Ready                  | Runs on Windows Server 2019 and can be migrated as-is |
| APP-01 | Conditionally Ready    | Requires testing for application compatibility |
| DB-01  | Conditionally Ready    | Mission-critical database requires downtime planning and validation |
| DC-01  | Conditionally Ready    | Needs careful migration to maintain identity services |
| FILE-01| Not Ready              | Runs on unsupported Windows Server 2012 R2 |

---

### Remediation Actions
- **APP-01 / DB-01**: Validate application and database compatibility  
- **DC-01**: Plan migration with minimal downtime or deploy additional domain controllers  
- **FILE-01**: Upgrade the operating system or migrate data to Azure Files  

---

## 5) Sizing & Cost Considerations

### How Azure Migrate Supports Sizing and Cost
Azure Migrate provides VM sizing recommendations and cost estimates by analyzing performance data or existing server specifications. It helps organizations choose the appropriate Azure VM SKU and estimate monthly costs.

---

### Performance-Based Sizing
- Uses historical CPU, memory, and disk usage  
- Optimizes resources and reduces costs  
- Recommended for production workloads  

---

### As-Is Sizing
- Uses current on-premises server configuration  
- Faster but less optimized  
- Useful when performance data is unavailable  

---

## 6) Migration Prioritization & Plan

### Workload to Migrate First
**WEB-01** should be migrated first because it is public-facing, lower risk, and easier to test.

---

### Considerations
- **DB-01** is mission-critical and requires minimal downtime  
- **DC-01** must remain stable to support authentication  
- **FILE-01** has higher risk due to legacy operating system  

---

### Proposed High-Level Migration Order
1. **WEB-01** – low risk, public-facing  
2. **APP-01 and DB-01** – migrated together due to dependency  
3. **DC-01** – carefully planned migration  
4. **FILE-01** – after remediation or modernization  


