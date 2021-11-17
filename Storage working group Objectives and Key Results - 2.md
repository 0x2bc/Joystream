# Storage working group Objectives and Key Results

### Notes 

Main quality criteria for Storage Providers:
- Speed
- Capacity
- Reliability
- Geographic Location
- Resilience

General idea of OKRs for Storage Providers was proposed [here](https://github.com/Joystream/community-repo/blob/master/governance/Storage_WG_OKR.md).

Based on that, a new OKR system with “quantitative” criteria was developed. 

# OKRs

## KR6 - Uptime

### Definition

Uptime is percentage of time when server is available.

### Goal 

Any downtime should be avoided as much as possible.

### Assessment criteria

| Condition          | Action<sup>*</sup>                            |
| ------------------ | --------------------------------------------- |
| Uptime > 90% (27/30 days)  | No impact on salary                     |
| Uptime < 90%               | Salary should be decreased by 50%       |
| Uptime < 50%               | Storage provider can be replaced        |


| Condition                                                   | Salary impact<sup>*</sup>              |
| ----------------------------------------------------------- | -------------------------------------- |
| When the node is down & URL is not set to empty < 12 hours  | No impact on salary                    |
| When the node is down & URL is not set to empty > 12 hours  | Salary should be decreased by 50%      |
| When the node is down & URL is not set to empty > 48 hours  | Storage provider can be replaced     |

<sup>*</sup> Sanctions (salary impacts) are not compounded. If there are few sanctions, the most strict will be applied.

## KR4 - Free storage

### Definition

Free storage space on Storage provider node that is instantly available for any purposes.

### Goal 

Maintain an extra storage capacity, in order to handle increased needs of the platform.
Storage Providers must maintain as much free space as has been uploaded during the last three months.

### Assessment criteria

| Condition                                                                        | Salary impact<sup>*</sup>              |
| ------------------------------------------------------------------------------- | -------------------------------------- |
| Free storage > [storage size (now) - storage size (3 months ago) ]* 3           | No impact on salary                    |
| Free storage < [storage size (now) - storage size (3 months ago) ]* 3 -         | Salary should be decreased by 50%      |
| Free storage < [storage size (now) ]   |  Storage provider can be replaced     |                                        |
 

## OKR 10 - Data center Diversification 

### Definition

A risk management strategy when Storage providers' nodes are diversified among different data centers.

### Goal 

Maintain node's diversity. Diverse set of Storage provider nodes is crucial to the success of a well-formed blockchain network.


### Assessment criteria

If storage provides are in the AS<sup>**</sup> with concentration of providers > 50%. Provider the last one to join should change AS. If that's not clear who is the last one, WG Lead will choose the provider who should change AS within 1 week. If no change after 1 week, the chosen provider will be reduced in salaries by 50%. After 2 weeks the storage provider can be replaced.  

<sup>**</sup>AS = autonomous system

# Bonus

If any Storavge provider works with no sanctions straight for 6 months, an additional 1 salary can be rewarded.
