# Storage working group Objectives and Key Results - Part 2

Main quality criteria for Storage Providers:
- Speed
- Capacity
- Reliability
- Geographic Location
- Resilience

Detailed quality criteria for Storage Providers were outlined [here](https://github.com/Joystream/community-repo/blob/master/governance/Storage_WG_OKR.md).

Based on that, a new OKR system with “quantitative” criteria was developed. 

In the event that a Storage Provider has violated our new OKRs, some sanctions will be assigned. The goal of assigning sanctions is to help Storage Providers understand the impact their actions have on Storage WG functioning and Atlas' users experience, prevent future violations, and repair any harm caused. Sanctions are not meant to punish, but to provide growth and development so better choices can be made in the future.

The following guidelines are not absolute, but provide an outline for potential sanctions based on the specific violation. This allows for greater consistency across our Storage standards. Sanctions are assigned to be effective and appropriate based on the circumstances of the individual Storage provider and incident, including aggravating or mitigating factors, and the Storage providers' previous record within Storage WG history.

OKRs are applicable to every Storage provider from the Strorage WG.

## OKRs

### KR6 - Uptime

#### Definition

Uptime is the percentage of time when the server is available.

#### Goal 

Any downtime should be avoided as much as possible.

#### Assessment criteria

| Condition          | Action<sup>*</sup>                             |
| ------------------ | --------------------------------------------- |
| Uptime > 90%               | No impact on salary                     |
| Uptime < 90%               | Salary can be decreased by 20%          |
| Uptime < 50%               | Storage provider can be replaced        |


| Condition                                                   | Salary impact<sup>*</sup>              |
| ----------------------------------------------------------- | -------------------------------------- |
| Node is down & URL is not set to empty < 12 hours  | No impact on salary                    |
| Node is down & URL is not set to empty > 12 hours  | Salary can be decreased by 20%      |
| Node is down & URL is not set to empty > 48 hours  | Storage provider can be replaced     |

<sup>*</sup> Sanctions (salary impacts) are not compounded. If there are few sanctions, the most strict one should be applied.
The sanctions can only be removed after 1 month from the incident.

### KR4 - Free storage

#### Definition

Free storage space on Storage provider node that is instantly available for any purposes.

#### Goal 

Maintain an extra storage capacity, in order to handle the increased needs of the platform.
Storage Providers must maintain as much free space as has been uploaded during the last three months.

#### Assessment criteria

| Condition                                                                        | Salary impact<sup>*</sup>              |
| ------------------------------------------------------------------------------- | -------------------------------------- |
| ![equation](https://latex.codecogs.com/svg.image?Free&space;Storage&space;Size&space;>&space;\left&space;(&space;StorageSize_{now}-StorageSize_{3&space;months&space;Ago}&space;\right&space;)&space;*&space;3)          | No impact on salary                    |
| ![equation](https://latex.codecogs.com/svg.image?Free&space;Storage&space;Size&space;<&space;\left&space;(&space;StorageSize_{now}-StorageSize_{3&space;months&space;Ago}&space;\right&space;)&space;*&space;3)        | Salary can be decreased by 20%      |
| ![equation](https://latex.codecogs.com/svg.image?Free&space;Storage&space;Size&space;<&space;StorageSize_{now})   |  Storage provider can be replaced     |                                        |
 

### KR 10 - Datacenter Diversification 

#### Definition

A risk management strategy when Storage providers' nodes are diversified among different data centers.

#### Goal 

Maintain nodes' AS<sup>**</sup> diversity. Diverse set of Storage provider nodes is crucial to the success of a well-formed blockchain network.

<sup>**</sup>AS = autonomous system

#### Assessment criteria

If storage provides are in the AS with concentration of providers > 50%, the last who joined should leave the AS. 
If that's not clear who is the last one to join, WG Lead will ask one of the provides to leave the AS. 
If there is no change after 1 week, the chosen provider will be reduced in salary by 20%. 
If there is no change after 2 weeks, the storage provider can be replaced.  


## Bonus

If any storage provider works with no sanctions straight for 6 months, an additional 1 salary can be rewarded.
