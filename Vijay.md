#### Migration plan of electronic health record (EHR) system from private cloud into Azure 

Franciscan Health is worried about <ins>rising infrastructure costs</ins>, <ins>risk of high downtime on their current system</ins> and <ins>limited scalability</ins>. To address these problems the organization is planning to move their Epic systems from private cloud to Azure cloud. 

To understand more about their current infrastructure, I will ask questions about the current performance metrics and downtime on their private cloud. I will ask about their CapEx (Capital Expenditure) and OpEx (Operating Expenditure) for their private cloud.

**Charles Wagner** responsible for funding and ensure this migration activity align with business goal.
Program Manager is accountable for planning and coordinating and tracking the migration activity.
Azure experts fall under Consulted, because they ensure smooth migration into Azure cloud.
In this case study, Cost analyst teams, CIO, CTO of Franciscan Health comes under Informed category.

The best approach for this migration would be **Lift-and-Shift**. This is because
Franciscan Health moved existing Epic system to the M-series VM in 
Azure cloud with little or no changes to their architecture and aimed to establish a more scalable, resilient, and cost-effective foundation for delivering uninterrupted care. 

I believe the schedule for migration involves various phases.
Discover phase includes inventory of private cloud resources and identify workloads, metrics for their current system.
Access phase includes estimating cost, performance needs.
migrate phase includes executing actual move and testing workloads and performance.
optimize phase includes monitor performance and fix inefficiencies.

As mentioned by 
Charles Wagner, Chief Information Officer
> From an operations standpoint, since we migrated to Azure we can do a failover and be up in 30 minutes. This is something we would never be able to do in our previous environment

Jay Bhat, Chief Information Security Officer
> With our move to the Azure cloud, we spin up new environments within 30 minutes, and we’re working toward recovering within 72 hours

Chuck Christian, VP Technology & CTO
> We’re saving at least a third on infrastructure and support. We are saving hundreds of thousands of dollars a month with migration to Azure

Therefore, I believe the primary decision criteria for Franciscan Health will be System availability and disaster recovery speed, Scalability for future growth, Cost reduction and long-term return on investment. 
