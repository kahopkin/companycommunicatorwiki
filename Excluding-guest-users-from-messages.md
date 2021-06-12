## Issue
Prior to version 4.1.1, messages could be sent to guest users in the following cases:
1. The message is sent (via 1:1 chat) to a team that has guest users.
2. The message is sent to an M365 group or security group that has guest users.
3. Guest users that received messages in cases #1 and #2 will receive subsequent messages sent using the "All users" option.

This issue has been fixed in [v4.1.1](https://github.com/OfficeDev/microsoft-teams-apps-company-communicator/releases/tag/v4.1.1).

## Resolution
To ensure that guest users are excluded from receiving messages sent via Company Communicator, please take the following steps:
1. Update Company Communicator to version 4.1.1 or greater.
2. Log in to the Azure Portal, and navigate to the Azure Storage account resource used by your instance of Company Communicator. Select **Data storage > Tables** from the list of options on the left side of the page. You will be taken to a page listing the tables in the storage account.
3. Select the **UserData** table, and click **Delete** to delete the table. When prompted to confirm, select "Yes".
4. Restart the 3 Azure Function instances used by Company Communicator.

The next time a message is sent to all users, it may take longer than usual, because the app will re-synchronize the list of users in your organization.

**NOTE:** The history of messages sent by Company Communicator, and the AAD object IDs of the recipients to whom the messages were delivered, is always stored in the **SentNotificationData** table for later review.