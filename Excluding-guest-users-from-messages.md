To ensure that guest users are excluded from receiving messages sent via Company Communicator, please take the following steps:
1. Update Company Communicator to version 4.1.1.
2. Log in to the Azure Portal, and navigate to the Azure Storage account resource used by your instance of Company Communicator. Select **Data storage > Tables** from the list of options on the left side of the page. You will be taken to a page listing the tables in the storage account.
3. Select the **UserData** table, and click **Delete** to delete the table. When prompted to confirm, select "Yes".
4. Restart the 3 Azure Function instances used by Company Communicator.

The next time you send a message, it will take longer than usual, because the app will re-synchronize the list of users.

**NOTE:** The history of messages sent by Company Communicator, and the AAD object IDs of the recipients to whom the messages were delivered, is stored in the **SentNotificationData** table.