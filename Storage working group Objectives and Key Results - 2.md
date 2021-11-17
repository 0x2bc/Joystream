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

| Uptime, %          | Action                             |
| ------------------ | ---------------------------------- |
| >90% (27/30 days)  | salary*100%                        |
| <90%               | salary*50%                         |
| <50%               | storage provider can be replaced   |


| Downtime, %                                                    | Action                                 |
| ----------------------------------------------------------- | -------------------------------------- |
| When the node is down & URL is not set to empty < 12 hours  | salary*100%                            |
| When the node is down & URL is not set to empty > 12 hours  | salary*50%                             |
| When the node is down & URL is not set to empty > 48 hours  |  storage provider can be replaced.     |


## KR4 - Free storage

### Definition

Free storage space on Storage provider node that is instantly available for any purposes.

### Goal 

Maintain an extra storage capacity, in order to handle increased needs of the platform.
Storage Providers must maintain as much free space as has been uploaded during the last three months.

### Assessment criteria

| Criteria                                                                        | Action                                 |
| ------------------------------------------------------------------------------- | -------------------------------------- |
| Free storage > [storage size (now) - storage size (3 months ago) ]* 3           | salary*100%                            |
| Free storage < [storage size (now) - storage size (3 months ago) ]* 3 -         | salary*50%                             |
| Free storage < [storage size (now) ]   |  storage provider can be replaced.     |                                        |
 

## (NEW) OKR 10 - Data center Diversification

### Definition

A risk management strategy when Storage provider nodes are diversified among different data centers.

### Goal 

Maintain node's diversity. Diverse set of Storage provider nodes is crucial to the success of a well-formed blockchain network.


### Assessment criteria

| Criteria                                                                        | Action                                 |
| ------------------------------------------------------------------------------- | -------------------------------------- |
| If provides are in the AS with concentration of providers > 50%                 |The last one to join should change AS. If it’s not clear who is the last one, one SP will be chosen to change AS within 1 week time. If no change after 1 week, it will reduced in salaries all SPs can be reduced in on 50% After 2 weeks it can be replaced.  |

## Sacntions & Rewards

Sanctions are not compounded. If there are few, the most strict will be applied.
If there are 100% salary (in other words - no sanctions) for 6 months, storage provider can be rewarded with additional 1 salary.
