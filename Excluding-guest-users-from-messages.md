## Issue
Prior to version 4.1.1, messages could be sent to guest users in the following cases:
1. The message is sent (via 1:1 chat) to a team that has guest users.
2. The message is sent to an M365 group or security group that has guest users.
3. Company Communicator was installed for guest users through an app setup policy (see https://docs.microsoft.com/en-us/microsoftteams/non-standard-users#personal-bots-installed-with-policies).
4. Guest users that received messages in cases 1-3 will receive subsequent messages sent using the "All users" option.

This issue has been fixed in [v4.1.1](https://github.com/OfficeDev/microsoft-teams-apps-company-communicator/releases/tag/v4.1.1).

## Resolution
To ensure that guest users are excluded from receiving messages sent via Company Communicator, please update Company Communicator to version 4.1.1 or greater.

**NOTE:** The history of messages sent by Company Communicator, and the AAD object IDs of the recipients to whom the messages were delivered, is always stored in the **SentNotificationData** table for later review.