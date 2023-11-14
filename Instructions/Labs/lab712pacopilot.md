# Create Automated Processes with Power Automate and Copilot​
## Part 1: Create a cloud flow with Copilot in Power Automate

In this lab, you'll create an automation using Copilot in Power Automate to send an email when an expense report is created. Expense report is a Microsoft Dataverse table. You will use Copilot in Power Automate to help build the initial flow and make revisions to get to your desired flow design.

### Exercise 1: Create a flow with Copilot
Follow these steps to create a flow using Copilot.

1. Sign in to Power Automate at `https://make.powerautomate.com` using the credentials provided to you on the **Resources** tab.

1. If prompted, select **Get started**.

1. At the top right of your screen, change the Environment to **Dev One**. This is where you will be working for the entirety of this lab. 

1. In the center of the **Home** page within Power Automate, in the text field, enter the following prompt:

   `send an email when a Dataverse record is created`

1. Select the **Generate** button (Note: Submit may be substituted for Generate)

1. From the prompt, Copilot provides the outline for a suggested flow that you can review. To accept the flow, select **Next**.

1. Review the connected apps and services. If a connection hasn't been made, edit or fix it and then select **Create flow**.

   The Edit with Copilot designer opens with your flow along with a Copilot chat window on the right.

### Exercise 2: Make changes to a flow with Copilot
Follow these steps to revise and finalize your flow using Copilot.

1. Set up some parameters by selecting the **When a row is added, modified or deleted** trigger.

   A panel on the left side of the screen shows the trigger details, including an empty **Table Name** parameter that's required.

1. From the **Table Name** drop-down menu, search for and select **Expense Reports**.

1. Collapse the **When a row is added, modified or deleted** pane with the double arrows. 

1. Select the **Send an email** action.

1. Select the **To** field and remove any text in the field before entering the email address that you're using for this lab (the Administrative Username on the Resources tab).

1. In the **To** field, select "Use "(email address)" as a custom value".

1. Enter the following text into the Copilot chat window and then press the **Enter** key on your keyboard:

   `Add "A new expense report has been created" as the Subject parameter for the Send an email action`

   The Send an email action pane will collapse. Reopen it and notice that the **Subject** field was populated with the prompt text.

1. Enter the following text into the Copilot chat window and then press the **Enter** key on your keyboard:

   `Add "A new expense report called (Report Name) has been created." as the Body parameter for the Send an email action.`

   The **Body** field should populate with the prompt text.

1. In the **Body** field, highlight "(Report Name)" and select the lightning icon for dynamic content. Select the **Report Name** dynamic content.

1. Collapse the **Send an email** action.

1. Rename the flow `Send an email when an expense report is submitted` by replacing the default flow name at the top left.

1. Select **Save**

1. Use the **Back** arrow in Power Automate to navigate to the flow details page. 

1. Open another tab and navigate to `https://make.powerapps.com`

1. Select **Apps** from the left navigation.

1. Locate and hover over the **Expense Tracker app** and select the **Play** icon to run the app.

1. Select **New** to create a new Expense Report.

1. Enter `Trip to Microsoft Ignite` as the **Report Name**.

1. Select **Save**.

### Exercise 3: Run your flow

1. Navigate back to the tab with your flow.

1. Look at the 28-day run history. You may need to select the **Refresh** icon to see the most recent run of your flow.

1. Select the flow run to review the outcome. 

1. In another tab, log in to `https://outlook.com` with your provided credentials to verify that you received the email. 

Congratulations! You have created a flow with the help of Copilot in Power Automate. 


