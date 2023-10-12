---
lab:
    title: 'Lab 04: Power Automate'
    module: 'Module 04: Power Automate'
---

> **NOTE**
>
> Effective November 2020:
>
> - Common Data Service has been renamed to Microsoft Dataverse. [Learn more](https://aka.ms/PAuAppBlog)
> - Some terminology in Microsoft Dataverse has been updated. For example, *entity* is now *table* and *field* is now *column*. [Learn more](https://go.microsoft.com/fwlink/?linkid=2147247)
>


# Lab 04: Power Automate

In this lab, you will create Power Automate cloud flows to automate various parts of the Company 311 solution.

The following have been identified as requirements you must implement to complete the project: 

  - Escalation, approval, and execution process for urgent maintenance issues 

  - Notify reporting user about the issue status changes 

  - How to use a business rule to implement logic.

## What you will learn

  - How to design data columns (in the data model) to support automation 

  - How to build a flow using Microsoft Dataverse Connector

  - How to use approvals 

## High-level lab steps

  - Add columns to support escalation 
  - Build flow to approve escalation  
  - Build flow to notify user of status change
  - Build approval as an adaptive card in Microsoft Teams 

## Prerequisites

* Must have completed **Lab 02.1: Data model and model-driven app**
* Must have completed **Lab 02.2: Business Process Flows and Business Rules**

## Things to consider before you begin

  - What is the most efficient way to identify urgent maintenance issues and escalate them

## Detailed steps  

### Exercise 1: Build notify flow

In this exercise, you create a flow that will notify the creator of a problem when the status changes.

#### Task 1: Create flow

In this task, you will create a flow that send notification when the status of problem report row changes.

1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) and make sure you are in the correct environment (MOD Administrator's Environment).

2.  Select **Solutions** and open the **?????** //Is this right?? Or should they create another solution? 

3.  Select **+ New** > **Automation** > **Cloud Flow** > **Automated**.

    ![A screenshot showing dropdown menu to create new automated cloud flow](04/media/image1.png)

4.  Enter `when a row` in the search box, then locate and select the **When a row is added, modified or deleted** action from the **Microsoft Dataverse** connector. 

5.  Select **Create**.

    ![Trigger selection screen with Microsoft Dataverse trigger selected and a cursor over Create button](04/media/image1-1.png)

6.  Select **Modified** for **Change type**, select **Problem Reports** for **Table name**, **Organizations** for **Scope** and expand **Show advanced options**.

7.  Enter `statuscode` for **Select columns** then select **… Menu** button of the trigger step.

    ![A Screenshot with an arrow pointing to the ellipses icon for more options and a border around the select columns statuscode](04/media/image3.png)

8.  Select **Rename**.

9.  Rename the trigger step `When problem report status changes`

10.  Select **+ New step**.

    ![A Screenshot with an arrow pointing to the add new step button](04/media/image4.png)

11. Select **Connectors** tab and then select **Microsoft Dataverse**. Select **Get a row by ID**.

12. Select **Users** for **Table name**.

13. Select the **Row ID** field, go to the Dynamic pane, search for `created` and select **Created By (Value)** to add it.

14. Select **Show advanced options** on the new step.

15. Enter `internalemailaddress` for **Select columns**.

16. Select the **… Menu** button of the new step and select **Rename**.

17. Rename the step `Get problem creator`

18. Select **+ New step**.

19. Search for `send email` and select **Send an email (V2).**

20. Select the **To** field and select the **Switch to Advanced Mode** arrows icon. Selecting this button toggles show/hide of the Dynamic content pane.

    ![A Screenshot with an arrow pointing to the switch to advanced mode icon](04/media/image5.png)

21. Select the **Primary Email** field from the **Get problem creator** step.

22. Enter `Problem report status change notification` for **Subject**.

23. Select the **Body** field.

24. Enter `The status of the problem you reported has changed.` and press the **[ENTER]** key.

25. Enter `Problem Title:` followed by a **[SPACE]**, go to the **Dynamic content** pane, search for `title` and select **Title**.

26. Press the **[ENTER]** key.

27. Enter `Current Status:` followed by a **[SPACE]**, go to the **Dynamic content** pane, select the **Expression** tab, paste the expression below, and select **OK**. This expression will show the label of the Status Reason instead of the value.

    `triggerOutputs()?['body/_statuscode_label']`

    ![A Screenshot with an arrow pointing to the ok button under the expression tab with the relevant expression pasted into it](04/media/image6.png)

28. Select the **… Menu** button of the new step and select **Rename**.

29. Rename the step to `Notify problem creator`

30. The step should now look like the image below.

    ![A screenshot of the modify problem creator window being to primary email, the subject being problem report status change notification, and the body being "The status of the problem you reported has changed" with the problem title and current status as trigger outputs below that](04/media/image7.png)

31. At the top of the page, change the flow name from **Untitled** to `Notify Problem Creator`

32. Select **Save** and wait for the flow to be saved.

    ![A screenshot of the current flow](04/media/image8.png)

33. Select the **🡠** button to go back to the previous page.


#### Task 2: Test the flow

In this task, you will test the Notify Problem Creator flow.

1.  On the Power Apps maker portal, `https://make.powerapps.com` ensure you are in the correct environment.

2.  Select **Apps**, and then select the **Company 311 Admin** Model-driven application. Select **Play**.

3.  Select **+ New**.

4.  Enter `Flow test` for **Title**, select **London Paddington** for **Building**, enter `This is a flow test` for **Details**, and select **Save**.

5.  Scroll down and change the **Status Reason** value to **In Progress** and save again.

6.  Close the application browser window or tab.

7.  You should now be back to the [Power Apps maker portal](https://make.powerapps.com/)

8.  Select **Solutions** and open the **Company 311** solution.

9.  Locate and open the **Notify Problem Creator** Cloud flow.

10. You should see a succeeded flow run in the **28-day run history section**. Open the run.

    ![A Screenshot with an arrow pointing to the start date of the 28-day run history section](04/media/image9.png)

11. All the flow steps should have a **green** check mark.

12. Select the **App launcher** and under **Apps**, select **Outlook**.

    ![A Screenshot with an arrow pointing to the app launcher and a border around outlook](04/media/image10.png)

13. You should have received an email from the Cloud flow. **Open** the email.

14. The email should look like the image below.

    ![A screenshot of the email you should receive with the status of the problem, problem title, and its current status](04/media/image11.png)


### Exercise 2: Build escalation flow

In this exercise, you will create and add two new columns to the Problem Report table and create an escalation flow.

#### Task 1: Add Columns

In this task, you add a new Columns to the Problem Report table.

1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) and make sure you are in the correct environment.

2.  Select **Solutions** and open the **Company 311** solution.

3.  Locate and open the **Problem Report** table in the **Objects** pane.

4.  Select **+ New > Column**.

5.  Enter **Estimated Cost** for **Display name**, select **Currency** for **Data type** and select **Save**.

6.  Select **Forms** from the **Objects** pane.

7.  Open the **Information** form of type **Main**.

8.  Add **Estimated Cost** column to the form and place it below the **Status Reason** column.

9.  Add the **Assign to** column and place it below the **Estimated Cost** column.

10. The **Resolution details** section of the form should now look like the image below. Select **Save and publish**.

    ![A screenshot with a border around estimated cost and assign to columns placed on the form and an arrow pointing to the save button](04/media/image12.png)

11. Select the **← Back** button located on the top left of the screen.

12. Select **All**, select **Publish all customizations**, and wait for the publishing to complete.


#### Task 2: Build escalation flow

In this task, you will create the escalation flow.

1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) and make sure you are in the correct environment.

2.  Select **Solutions** and open the **Company 311** solution.

3.  Select **+ New > Automation > Cloud Flow > Automated**.

4.  Search for **when a row is added** and select **When a row is added, modified, or deleted**  from **Microsoft Dataverse** connector then select **Create**.

5.  Select **Added or Modified** for **Change type**, select **Problem Reports** for **Table name**, select **Organization** for **Scope** and select **Show advanced options**.

6.  Enter **lh_estimatedcost,lh_assignto** for **Select columns**.

7.  Select the **… Menu** button of the trigger step and select **Rename**.

8.  Rename the trigger step **When a problem report is created or updated**.

9.  Select **+ New step**.

10. Search for **Condition** and Select **Condition** control.

11. Select the first **Choose a value** field.

12. Go to the Dynamic content pane, search for **estimated** and select **Estimated Cost**.

    ![A screenshot of the dynamic content pane with the word estimated in the search bar](04/media/image13.png)

13. Select **is greater than** in the second field and enter **1000** in the third field.

14. Rename the condition step to **Check if cost is greater than 1000**.

15. Go to the **If yes** branch and select **Add an action**.

16. Search for **Get a row** and select **Get a row by ID** from **Microsoft Dataverse**.

17. Select **Users** for **Table name**.

18. Select the **Row ID** field and select **Assign to (Value)** from the **Dynamic content** pane.

19. Select **Show advanced options**.

20. Enter **internalemailaddress** for **Select columns**.

21. Rename the **Get a Row by ID** step **Get user**.

23. Select **Add an action**.

24. Search for **approval** and select **Start and wait for an approval**.

25. Select **Approve/Reject - Everyone must approve** for **Approval type**.

26. Enter **Cost approval required** for **Title**.

27. Select the **Assigned to** field.

28. Go to the **Dynamic content** pane and select **Primary Email** from the **Get user** step.

29. Paste the markdown text below in the **Details** field.

    > \#\# URGENT Approval Required
    >
    > This is \*\*very\*\* expensive item with the estimated cost of

30. Place your cursor after cost of, go to the Dynamic content pane, select the **Expression** tab, paste the expression below, and select **OK**.

    `formatNumber(triggerOutputs()?['body/lh_estimatedcost'], 'C2')`

    ![A Screenshot with an arrow pointing to the ok button in the expression tab under the pasted expression](04/media/image14.png)

31. Select **Add an action**.

32. Search for **condition** and select the **Condition** action from the Control connector.

33. Select the first **Choose a value** field.

34. Go to the **Dynamic content** pane, search for **Outcome** and select **Outcome**.

35. Select **equals to** in the second field and enter **Reject** for value in the third field.

36. Go to the **If yes** branch and select **Add an action**.

37. Search for **update a Row** and select **Update a Row** from **Microsoft Dataverse**.

38. Select **Problem Reports** for **Table name**.

39. Select the **Row ID** field.

40. Go to the **Dynamic content** pane, search for **problem report** and select **Problem Report**.

41. Select **Show advanced options**.

42. Select the **Resolution** field, go to the **Dynamic content** pane and select **Response summary**.

43. Select **Won’t fix** for **Status Reason**.

44. Rename the step **Update problem report**.

45. Scroll up and rename the flow **Escalate Expense Approval**.

46. Select **Save**.

    ![A screenshot of the current flow](04/media/image15.png)

47. Close the flow designer browser window or tab.

48. Select **Done** on the popup.


#### Task 3: Test flow

In this task, you will test the escalation flow.

1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) and make sure you are in the correct environment.

2.  Select **Apps** and open the **Company 311 Admin** application.

3.  Open one of the **Problem Report** rows.

4.  Scroll down, enter **2500** for **Estimated Cost**, assign it to **yourself** (for test purposes) and select **Save**.

5.  Navigate to the [Power Automate maker portal](https://make.powerautomate.com/).

6.  Select **Approvals**.

7.  You should see at least one approval in the received tab. Open the approval. It can take around 10-15 minutes for approvals to show up here on the first run.

    ![A Screenshot with an arrow pointing to the cost approval required request](04/media/image16.png)

8.  Select **Reject**, enter **We don't have the funds for this item** for **comment**, and select **Confirm**.

    ![A screenshot of the details of the request with the relevant text in each field](04/media/image17.png)

9.  Go back to the **Company 311 Admin** application.

10. Change the view to **My Reports** and open the same row you change the estimated cost.

11. The **Status Reason** should be set to **Won’t fix** and the **Resolution** should contain the details of Approver, Response, Request Date and Response Date.

12. Select **Save**, if you have not done so previously.

    ![A screenshot of the status reason and resolution matching the values and text you put into the request](04/media/image18.png)


### Exercise 3: Send approval requests as adaptive card in Microsoft Teams

In this exercise, you will setup a team in Microsoft Teams dedicated to the Company 311 applications. You will modify the flow to send the approval request as an adaptive card in Teams chat instead of an approval message.

* Task 1: Setup Company 311 Team
* Task 2: Modify flow to send adaptive card in Teams chat
* Task 3: Test adaptive card

#### Task 1: Setup Company 311 Team

In this task you will setup a Microsoft Teams team for the Lamna Healthcare Company, if you have not done so in previous exercises.

**Note:** If you have already created the **Company 311** Teams in the Microsoft teams, skip this part and continue to the next task.

1.  Navigate to [Microsoft Teams](https://teams.microsoft.com) and sign in with the same credentials you have been using previously.

2.  Select **Use the web app instead** on the welcome screen.

    ![A screenshot of the Microsoft Teams landing page with a border around the use the web app instead button](04/media/image-5-teams.png)

3.  When the Microsoft Teams window opens, dismiss the welcome messages.

4.  On the bottom left corner, choose **Join or create a team**.

5.  Select **Create a team**.

    ![A screenshot with a box around the join or create a team button at the bottom of the window and a border around the create a team button](04/media/image-5-createteam.png)

6.  Press **From scratch**.

7.  Select **Public**.

8.  For the Team name choose **Company 311** and select **Create**.

9.  Select **Skip** adding members to Company 311.


#### Task 2: Modify flow to send adaptive card in Teams chat

In this task you will replace the approval sent by email with an adaptive card. 

1.  Navigate to the [Power Automate maker portal](https://make.powerautomate.com/) and make sure you are in the correct environment.

2.  Select **Solutions** and open the **Company 311** solution.

3.  Select **Cloud flows** from the **Objects** pane and open the **Escalate Expense Approval** flow. Select **Edit**. 

4.  Locate **Start and wait for an approval** step created earlier in **Exercise 2, Task 2**. 

5.  Select the **...** menu, and then select **Delete**. 

6.  Hover your mouse between the steps, select the **+** to insert a new step then select **Add an action**. 

7.  Search for **approval**, and select **Create an approval**. 

8.  Select **Approve/Reject - Everyone must approve** for **Approval type**. 

9.  Enter **Cost approval required** for **Title**. 

10. Select the **Assigned to** field. 

11. Go to the **Dynamic content** pane and select **Primary Email** from the **Get user** step. 

12. Paste the markdown text below in the **Details** field. 

    > \*\*{title}\*\*
    >
    > {details}
    >
    > This is a \_very\_ expensive item with the estimated cost of

13. Select **{title}** placeholder, go to the **Dynamic content** pane, locate and select **Title** field from **When a problem report is created or updated** step.

14. Select **{details}** placeholder, go to the **Dynamic content** pane, locate and select **Details** field from **When a problem report is created or updated** step.

15. Place your cursor after **cost of** , go to the **Dynamic content** pane, select the **Expression** tab, paste the expression below, and select **OK**.

    `formatNumber(triggerOutputs()?['body/lh_estimatedcost'], 'C2')`

16. Your step should look like the following: 

    ![A screenshot of the create an approval window with the following. Approval type as approve/reject - everyone must approve, title as cost approval required, assigned to primary email, details as title, details, some text and format number, item link, and item link description](04/media/image-5-create-approval.png)

17. Hover your mouse again below Create an approval step, select **+** and then select **Add an action**.

18. Search for `teams` and select **Post adaptive card and wait for a response** action.

19. Select **Flow bot** for Post as and select **Chat with Flow bot** for Post in.

20. Select the **Recipient** field.

21. Go to the **Dynamic content** pane and select **Primary Email** from the **Get user** step.

22. Select **Message** field.

23. Go to the **Dynamic content** pane and select **Teams Adaptive Card** from the **Create an approval** step.

24. The **Post adaptive card and wait for a response** step should look like the image below:

    ![A screenshot of the post adaptive card in a chat or channel pane](04/media/image-5-post-adaptive-card.png)

25. Hover your mouse again below Post card in a chat or channel step, select **+** and then select **Add an action**.

26. Search for `approval` and select **Wait for an approval** action.

27. Select **Approval ID** field.

28. Go to the **Dynamic content** pane and select **Approval ID** from the **Create an approval** step.

    ![A screenshot of the wait for an approval panel with approval ID in the approval ID field](04/media/image-5-wait-for-approval.png)

29. You now have replaced **Start and wait for an approval** step with the following:

    ![A screenshot of the current flow with: create an approval, post adaptive card in a chat or channel, and wait for an approval](04/media/image-5-replaced-approval.png)

30. Expand the **Condition** step. The left side of the condition should be empty because it was referring the step which is now removed. 

31. Go to the **Dynamic content** pane, search for `outcome`, and select **Outcome** from **Wait for an approval** step. 

32. Locate **Update problem report** step under **If yes** branch. 

33. Select **Show advanced options**.

34. Select the **Resolution** field, go to the **Dynamic content** pane, and select **Response summary** from **Wait for an approval** step.

35. Select **Save**.

36. **Close** the flow designer browser window or tab.

37. Select **Done** on the pop-up.


#### Task 3: Test flow

In this task, you will test the escalation flow with the Teams and adaptive cards.

1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) and make sure you are in the correct environment.

2.  Select **Apps** and open the **Company 311 Admin** application.

3.  Open one of the **Problem Report** Rows.

4.  Scroll down, enter any amount greater than **1000** for **Estimated Cost**, assign it to **yourself** (for test purposes) and select **Save**.

5.  Navigate to [Microsoft Teams](https://teams.microsoft.com).

6.  Select **Chat**.

7. You should see the **Cost approval required** adaptive card in a message from **Power Automate**.

    ![A screen shot of the request for cost approval pane](04/media/image-5-sample-adaptive-card.png)  

8. Select the **Reject** button and enter a comment of your choice in the **Comments** area, for example **The item is too expensive**.

9. Select **Submit**. The card will become read-only.

    ![A screenshot of the request once you have rejected it](04/media/image-5-readonly-card.png)

10. Go back to the **Company 311 Admin** application.

11. Change the view to **My Reports** and open the same Row you change the estimated cost.

12. The **Status Reason** should be set to **Won’t fix** and the **Resolution** should contain the details of Approver, Response, Request Date and Response Date.

    ![A screenshot of the status reason and resolution matching the details of your response to the request](04/media/problemreportadaptivecard.png)


## **Discussion**

  - Would creating a boolean field for Approved/Rejected be better?
  - What are the pros and cons of using Microsoft Teams over regular email?

## **Bonus exercises**

  - Add ability for the users to subscribe to the reported problems and only notify if there is a subscription. 
  - Auto-subscribe creator of the problem report.
  - How to find out previous value of status reason?
  - Create your own adaptive card using [Adaptive Cards Designer](https://adaptivecards.io/designer/).
