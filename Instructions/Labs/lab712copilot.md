
# Lab 1: Create an approval flow with Copilot in Power Automate

In this exercise, you'll create an automation by using Copilot in Power Automate to automate the approval process for expense reports. 
You'll use Copilot to create a flow that sends an email to the reviewer when a new expense report is created. 
Then, the reviewer can approve or reject the expense report from within the email.

Follow these steps to create a flow by using Copilot.

1. Sign in to Power Automate at `https://make.powerautomate.com`.

1. In the center of the **Home** page within Power Automate, in the text field on **Start building your flow with Copilot**, enter the following prompt:

   `request approval when a Dataverse record is created`

1. Select the **Generate** button (note: Submit may be substituted for Generate)

1. From the prompt, Copilot provides the outline for a suggested flow that you can review. To accept the flow, select **Next**.

1. Review the connected apps and services. If a connection hasn't been made, edit or fix it and then select **Create flow**.

   The Edit with Copilot designer opens with your flow along with a Copilot chat window on the right.

1. Set up some parameters by selecting the **When a row is added, modified or deleted** trigger.

   A panel on the left side of the screen shows the trigger details, including an empty **Table Name** parameter that's required.

1. From the **Table Name** dropdown menu, search for and select **Expense Reports**.

1. Collapse the **When a row is added, modified or deleted** pane with the double arrows. 

1. Select the **Start and wait for an approval** action.

   Notice that the **Approval Type** parameter is missing.

1. From the **Approval Type** dropdown menu, select **Approve/Reject - First to respond**.

   After you select the **Approval Type**, more parameters are now available.

1. In the Copilot chat window, enter the following prompt and submit:

    `Add "New expense report received" as the Title parameter for the Start and wait for an approval action`

   It takes a few seconds for Copilot to process the prompt. 

1. Select the **Start and wait for an approval** action to confirm that the Title parameter has been populated with the text.

1. For the **Assigned To** parameter, enter the email address that you're using for this lab. This email address is the one that receives the approval request.

1. For the **Details** parameter, enter the following text:

   `A new expense report has been received. Please review the details to approve or reject the report:

   Report Name:`

1. Place your cursor next to **Report Name** in the **Details** parameter and then select the lightning icon to open the **Dynamic content** pane.

1. In the **Dynamic content** pane, find the **Report Name** field and then select it.

   The **Report Name** dynamic content field is now added to the **Details** parameter.

1. Collapse the **Start and wait for an approval** action by selecting the double arrow icon.

1. Select the **+** icon following the **Start and wait for an approval** action.

1. Select **Add an action**

1. Search for **Condition** in the Search bar and select **Condition** under Control.

1. Select the **Choose a value** box and then select **Outcome** from the **Dynamic content** pane.

1. Select **is equal to** for the condition and then enter **Approve** for **Value**.

1. Collapse the **Condition** action and then select **+** under the **True** branch of the condition.

1. Select **Add an action**

1. Search for **Update a row** and select **Update a row** under **Microsoft Dataverse**.

1. From the **Table Name** dropdown menu, search for and select **Expense Reports**.

1. Select the **Row ID** field and then select the Lightning icon for Dynamic content.

1. Select **See More** for **When a row is added, modified, or deleted**

1. Locate and select the **Expense Report** unique identifier field from the **Dynamic content** pane.

1. Select **Show all** for **Advanced parameters**.

1. Select **Approved** from the **Status Reason** dropdown menu.

   When a report is approved, the **Status Reason** field in the **Expense Report** row will be updated to **Approved**.

1. Collapse the **Update a row** action and then select **+** under the **False** branch of the condition.

1. Select **Add an action**

1. Search for **Update a row** and select **Update a row** under **Microsoft Dataverse**.

1. From the **Table Name** dropdown menu, search for and select **Expense Reports**.

1. Select the **Row ID** field and then select the Lightning icon for Dynamic content.

1. Select **See More** for **When a row is added, modified, or deleted**

1. Locate and select the **Expense Report** unique identifier field from the **Dynamic content** pane.

1. Select **Show all** for **Advanced parameters**.

1. Select **Denied** from the **Status Reason** dropdown menu.

   When a report is rejected, the **Status Reason** field in the **Expense Report** row will be updated to **Denied**.

1. Collapse the **Update a row** action.

1. In the Copilot chat window, enter the following prompt and then submit:

   `Under the "Update a row" action for both branches in the condition, add a new "Send an email (V2)" action`

1. Notice the response from Copilot and the changes made to the flow. Select the **Send an email** action for the **True** branch of the condition.

1. Select the **To** field and remove any text in the field before entering the email address that you're using for this lab.

1. In the **To** field, select "Use "(email address)" as a custom value".

1. Enter the following text into the Copilot chat window and then press the **Enter** key on your keyboard:

   `Add "The expense report has been approved" as the Subject parameter for the Send an email action`

   The **Subject** field should populate with the prompt text.

1. Enter the following text into the Copilot chat window and then press the **Enter** key on your keyboard:

   `Add "For your records, the following expense report has been approved:" as the Body parameter for the Send an email action`

   The **Body** field should populate with the prompt text.

1. Enter the following content after the **Body** text:

   **Report Name:**

   **Approval Date:**

   Add the **Report Name** and **Completion Date** fields from the **Dynamic content** pane to the appropriate lines in the **Body** text.

1. Add the **Response summary** field from the **Dynamic content** pane to the end of the **Body** text.

1. Collapse the **Send an email** action.

1. Select the **Send an email 2** action under the **False** branch of the condition.

1. Select the **To** field and remove any text in the field before entering the email address that you're using for this lab.

1. For the **Subject** field, enter the following content into the Copilot chat window and then press the **Enter** key on your keyboard:

   `Add "The expense report has been denied" as the Subject parameter for the Send an email 2 action`

1. For the **Body** field, enter the following text into the Copilot chat window and then press the **Enter** key on your keyboard:

   `Add "For your records, the following expense report has been denied:" as the Body parameter for the Send an email 2 action`

1. Enter the following content after the **Body** text:

   **Report Name:**

   **Denial Date:**

   Add the **Report Name** and **Completion Date** fields from the **Dynamic content** pane to the appropriate lines in the **Body** text.

1. Add the **Response summary** field from the **Dynamic content** pane to the end of the **Body** text.

1. Collapse the **Send an email 2** action.

1. Rename the flow to **Request Approval for Expense Report** by selecting the **request approval when a Dataverse record is created** text in the upper-left corner of the screen.

1. Save the flow by selecting the **Save** button in the upper-right corner of the screen.

1. Test the flow by selecting the **Test** button in the upper-right corner of the screen. Select **Manually** and then select **Test**. (If you receive an error message, you may close this out. The flow should still run.)

1. To submit an expense report, go to the Expense Tracker app in https://make.preview.powerapps.com.

1. Run the app and then select **+New** to create an expense report.

1. Fill in the expense report name.

1. Select **Save**.

1. Select the **X** in the upper-right corner to close out of the app.

   The flow runs and sends an approval email to the email address that you provided in the flow that you built.

1. Sign in to the email account that you're using for this lab at https://outlook.com and then wait for the email to arrive. (If the flow doesn't run immediately, make sure that you wait for it. It might take up to 10 minutes for the flow to be triggered, especially on the first try.)

1. Select **Approve**.

1. Add a comment and then select **Submit**.

   The flow continues to run; it updates the row and sends an email to the requestor. The email that's sent to the requester resembles the following image.

1. Check the flow and notice that the flow is now marked as **Succeeded** in the run history.

