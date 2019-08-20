## Assumptions

The estimate below assumes:
* 1000 users in the tenant
* 1 message sent to all users each week (~5/month)
* Administrator opts to create a custom domain name and obtain an SSL certificate for the site. 
    * When purchased through Azure, this is *typically* ~$12 for a domain name, and $75/year for the SSL certificate.

We ignore:
* Operations associated with app installations, as that happens only once per user/team
* Operations associated with the authors viewing the tab, given the assumption that they are sending only 5 messages/month.

## SKU recommendations

The recommended SKUs for a production environment are:
* App Service: Standard (S1)
* Service Bus: Basic

## Estimated load

**Number of messages sent**: 1000 users * 5 messages/month = 5000 messages

**Data storage**: 1 GB max    
* Messages are on the order of KBs

**Table data operations**:
* Notifications
    * (1 read/send * 5000 messages) = 5000 reads
    * (1 write/send * 5000 messages) = 5000 writes
    * Aggregating status: (1 read/recipient * 5000 messages) = 5000 reads

**Service bus operations**:
* ((1 write + 1 read) operations/sent message * 5000 messages) = 10000 operations

**Azure Function**:
* (1 invocation/send * 5000 messages) = 5000 invocations

## Estimated cost

**IMPORTANT:** This is only an estimate, based on the assumptions above. Your actual costs may vary.

Prices were taken from the [Azure Pricing Overview](https://azure.microsoft.com/en-us/pricing/) on 15 August 2019, for the West US 2 region.

Use the [Azure Pricing Calculator](https://azure.com/e/c3bb51eeb3284a399ac2e9034883fcfa) to model different service tiers and usage patterns.

Resource                                    | Tier          | Load              | Monthly price
---                                         | ---           | ---               | --- 
Storage account (Table)                     | Standard_LRS  | < 1GB data, 15000 operations | $0.045 + $0.0008 = $0.05
Bot Channels Registration                   | F0            | N/A               | Free
App Service Plan                            | S1            | 744 hours         | $74.40
App Service (Bot + Tab)                     | -             |                   | (charged to App Service Plan) 
Azure Function                              | Dedicated     | 5000 executions   | (free up to 1 million executions)
Service Bus                                 | Basic         | 10000 operations  | $0.05
Application Insights                        | -             | < 5GB data        | (free up to 5 GB)
**Total**                                   |               |                   | **$74.50**
