# OKR 1 - Uptime
## Definition

Percentage of time when server is available.

## Goal

Any downtime should be avoided as much as possible.

## Comment

TBD Storage provider Lead should have an ability to forcely set URL to empty

## Requirements

### Measurement

Script that will check availability of server every 10 minutes (test download a small piece of data from the server). 

### Target

\> 90% (calculated as a monthly average)

### Sanctions

If uptime is lower than 90% (calculated as monthly average), Storage provider can be fired. 

Information about planned any maintanace work should be communicated to Storage provider Lead in advance.  

If a server is down, strorage provider should immediately set URL to empty.
 
Storage provider can be slashed with up to 30% of the next month' salary if URL is not set to empty within 12 hours after server is down. If the situation is repeated within one month, Storage provider can be fired. 


# OKR 2 - (Data center) Diversification
## Definition

A risk management strategy when Storage provider nodes are diversified among different data centers.

## Goal

Maintain node's diversity. Diverse set of Storage provider nodes is crucial to the success of a well-formed blockchain network.

## Comment

## Requirements

### Measurement

Script that will check autonomous system (AS) names of the servers once per day.

### Target

No data center should host >33% of nodes.

To ensure good coverage for users the Lead defines preferred locations in opernings according to regional requirements set by the council.

### Sanctions

If the problem is not solved within 2 weeks, then use Standard sanction*.

>Standard sanction:
>If the Storage provider's (average weekly) value worse than target, Storage provider shall be warned. If no improvements after 1 week, Storage provider can be slashed up to 30% 
of the next month' salary.  If no improvements after 2 next weeks, Storage provider can be fired.

Users who were first in data center will have a higher priority over users who come later.

# OKR 3 - Rendering time
## Definition

Amount of delay from the time when an upload is initiated to it's completion.

## Goal

Maintain lowest possible rendering time.

## Comment

When launching the landing page, some assets are often lagging behind, which gives a poor user experience. This is partially attributed to a non-optimal selection criteria by the Joystream Player, but if all the Storage providers behaved "perfectly", that wouldn't be an issue anyway.

## Requirements

### Measurement

Script that will check storage provider response time every hour. There should be at least 10 tests with different file sizes for every storage provider. Median values should be used.


### Target

\<2 sec

### Sanctions

Standard sanction*

>Standard sanction:
>If the Storage provider's (average weekly) value worse than target, Storage provider shall be warned. If no improvements after 1 week, Storage provider can be slashed up to 30% 
of the next month' salary.  If no improvements after 2 next weeks, Storage provider can be fired.

# OKR 4 - Download speed
## Definition

How many megabits of data per second storage providers can send from Storage provider node to another server on the internet. 

## Goal

Maintain the highest possible upload speed.

## Comment

## Requirements

### Measurement

Script that will check download speed every hour. There should be at least 3 tests with different file sizes for every storage provider. 

### Target

\>25 Mbits/s (=4K video)

### Sanctions

Standard sanction*

>Standard sanction:
>If the Storage provider's (average weekly) value worse than target, Storage provider shall be warned. If no improvements after 1 week, Storage provider can be slashed up to 30% 
of the next month' salary.  If no improvements after 2 next weeks, Storage provider can be fired.

# OKR 5 - Available storage space
## Definition

Free storage space on Storage provider node that is instantly available for any purposes.

## Goal

Maintain an extra storage capacity, in order to handle increased needs of the platform.

## Comment

## Requirements

### Measurement

Storage providers should provide information about their's excess of storage capacity via script that should be installed on storage providers' nodes.  Script will check excess of storage capacity every hour. 
Note: Available storage space is a storage space that can be instantly available.

### Target

Storage Providers must maintain as much free space as has been uploaded during the last three months.

### Sanctions

Standard sanction*

>Standard sanction:
>If the Storage provider's (average weekly) value worse than target, Storage provider shall be warned. If no improvements after 1 week, Storage provider can be slashed up to 30% 
of the next month' salary.  If no improvements after 2 next weeks, Storage provider can be fired.
