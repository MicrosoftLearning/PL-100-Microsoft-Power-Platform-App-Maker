## Lab 1: Use Copilot to create a canvas app

In this exercise, you’ll create a mobile application by using Copilot in Power Apps. Field agents will use this app to browse real estate inventory and manage appointments for showings, and the data will be stored in Dataverse.

> [!NOTE]
>
> In this lab, your results for data might vary. The reason is because Power Apps uses OpenAI to generate data for the lab and the data changes daily.

### Create a Real Estate Property table using Copilot 

1. Sign in to Power Apps at `https://make.powerapps.com`.

1. Select **Tables**.

1. Select **Describe the new table** to use Copilot to create a new table.

1. Where the Copilot chat reads "What do you want to do with this table", enter the following prompt and submit:

   `Store Real Estate Property information, including Address, Price, Size, Owner, and Owner Email.`

1. Review the suggested Real Estate Property table. 

 1. If your results have both a Name and an Address column, respond in the Copilot chat: 

   `Rename the Name column "Address" and store the addresses in that column.`

1. Respond in the Copilot chat:

   `The property prices in the example data should be between $100,000 and $1,000,000.`

1. Review the suggested Real Estate Property table. Compare your columns to the following and make any adjustments needed for them to align:
   - ID
   - Address
   - Price
   - Size
   - Owner
   - Owner Email

1. Select **Create**.

### Create a canvas app for managing real estate showings

1. Select the **Home** tab in the left navigation.

1. In the center text field, enter the following prompt and submit to create an AI-generated table and canvas app:

    `Build an app to manage real estate showings`

1. After Copilot AI generates a table based on your prompt, look through the table to view the columns that are created for the start of your table.

1. Respond in the Copilot chat:

   `Change the data type of the Address column to a lookup to the Real Estate Property table`

1. Notice the change to the column. Respond in the Copilot chat:

   `Remove the Address column`

1. Notice the change to the column. Respond in the Copilot chat:

    `Add a column for Client Full Name`

1. Notice the change to the column. Respond in the Copilot chat:

    `Add a column for Client Email`

1. If you do not have a column for **Status**, respond in the Copilot chat:

    `Add a column for Status`

1. Locate and select the **Status** column, then select **View column**. Notice there are three choices for Status.

1. Select the **X** in the upper-right corner of the column properties pane to close it.

1. Respond in the Copilot chat:

    `The Status choices should be Pending, Confirmed, Cancelled, and Completed`

1. Again, locate and select the **Status** column, then select **View column**. Notice there are now four choices: Pending, Confirmed, Cancelled, and Completed.

1. Select the **X** in the upper-right corner of the column properties pane to close it.

    Next, you'll add more data to your table and the existing columns. 

1. In the **Copilot** pane text box, enter and send the following text:

    `Add 5 more rows of data`

    Five more rows of data are added for each existing column in the table.

    Your table should have several columns. Compare your columns to this list and remove any that you do not need.

    The list of columns that you need are:

    - ID

    - Name

    - Date

    - Time

    - Agent

    - Status

    - Notes

    - Client Full Name

    - Client Email

    Use what you've learned with the **Copilot Chat** window to adjust your table to match the preceding list. Make sure that you refer to the **Suggestions** section if you need to remove a column, change a column name, or add a column.

1. To create the app, select the **Create app** button in the lower-right corner of the screen.

1. When the app first loads, a dialog might appear stating **Welcome to Power Apps Studio**. If so, select the **Skip** button.

    The app that has been built for you should show in **Edit** mode.

1. Select the **Data** icon from the left navigation bar. Notice that Copilot has created the **Real Estate Showings** Dataverse table.

    Next, you'll edit the table now that the app has been created.

1. Within the **Data** pane, hover your mouse cursor over the **Real Estate Showings** table. To the right of the table, select the ellipsis (**...**).

1. From the menu, select **Edit data**.

1. In the **Edit table** dialog, you can add your own columns to the table or modify existing columns.

1. Select the **ID** column header from the table.

1. From the dropdown menu, select the **Edit column** option.

1. In this example, you don't want the **Data type** to be a **Single line of text**. To change that value, go to the **Edit column** pane, and then from the **Date type** dropdown menu, select **Autonumber**.

1. Select **Save**.

1. Select **New column**.

1. Enter "Property" for the **Display Name**.

1. For **Data type**, select **Lookup**.

1. For **Related table**, search for and select **Real Estate Property**.

1. Select **Save**.

1. Select **Close** in the lower-right corner of the **Edit table** dialog.

   The table should now show as **Refreshed** in the **Data** pane.

1. Select the **Save** icon to save the app.

1. Modify the gallery in the application so that it displays the relevant data. Select the **Tree view** icon to return to the Tree view.

1. On the app's main screen, select **ScreenContainer1** > **BodyContainer1** > **SideBarContainer1** > **RecordsGallery1** > **Subtitle1**

1. Notice the data on the app preview that has been selected. In the formula bar, change the Text for Subtitle1 to:

    `Text(ThisItem.Date, "[$-en-US]mm/dd/yyyy")`

1. Select the **Body** and then update the **Text** value to display the **Status** of ThisItem. To do this, replace the column that is currently set to display (within the single quotation marks) with `Status` and select the appropriate **Status** column from the options.

1. On the app's main screen, select the **Form** control (You can also locate this in the Tree view by selecting **ScreenContainer1** > **BodyContainer1** > **RightContainer1** > **MainContainer1** > **Form1**).

1. On the **Properties** pane on the right, for the **Fields** property, select **Edit fields**.

1. In the **Fields** pane, expand the **ID** field.

1. From the **Control type** dropdown menu, change the type to **View text**.

    Because you previously changed the **ID** field to **Autonumber**, you don’t want users entering their own number; Dataverse automatically enters the numbers for you.

1. Select **Add field**.

1. Select **Property** to add the Property field to the form.

1. In the **Fields** pane, select the **X** in the upper-right corner to close the pane.

1. Make a new request for a property that shows in the app by selecting the **Play** button from the upper part of the screen.

1. In the left pane, select the **+New** button.

1. Populate the fields to create a new Real Estate Showing.

1. Select the check mark in the upper-right corner of the screen.

1. Close out of the app preview by selecting the **X** in the right corner.

    If a dialog appears saying **Did you know?**, select **OK**.

    The new request is added to the left of the list of requests.

1. From the upper part of your screen, select the **Save** button to save the new app that you created.

    If the system prompts you, save the app name as **Real Estate Showings**.

Congratulations on creating your canvas app with Copilot! 
