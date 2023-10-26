## Lab 1: Use Copilot to create a canvas app

In this exercise, you’ll create a mobile application by using Copilot in Power Apps. Field agents will use this app to browse real estate inventory and manage appointments for showings, and the data will be stored in Dataverse.

> [!NOTE]
>
> In this lab, your results for data might vary. Power Apps uses AI to generate data for the lab and the data changes daily.

### Create the Real Estate Property table using Copilot 

1. Sign in to Power Apps at `https://make.powerapps.com`.

1. At the top right of your screen, change the Environment to **Dev One**. This is where you will be working for the entirety of this lab.

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

1. Review the suggested table. If you do not have a column for **Status**, respond in the Copilot chat:

    `Add a Choice column for Status`

1. Locate and select the **Status** column, then select **View column**. Notice the choices for Status.

1. Select the **X** in the upper-right corner of the column properties pane to close it.

1. Respond in the Copilot chat:

    `The Status choices should be Pending, Confirmed, Cancelled, and Completed`

1. Again, locate and select the **Status** column, then select **View column**. Notice there are now four choices: Pending, Confirmed, Cancelled, and Completed.

1. Close the column properties pane.

1. Review the suggested table and consider what information you want to manage for Real Estate Showings in your app. You can prompt Copilot to make changes to the table as you wish. Here are some example prompts: 

    `Add a column for Client Full Name`

    `Add a column for Client Email`

1. In the **Copilot** pane text box, enter and send the following text:

    `Add 5 more rows of data`

    Five more rows of data are created for the table.

1. To create the app, select the **Create app** button in the lower-right corner of the screen.

1. When the app first loads, a dialog might appear stating **Welcome to Power Apps Studio**. If so, select the **Skip** button.

    The app that has been built for you should show in **Edit** mode.

## Configure the Real Estate Showings table

1. Close the Copilot chat pane to allow for more screen space. You can access the Copilot pane at any time by selecting the Copilot (preview) icon at the top.

1. Select the **Data** icon from the left navigation bar. Notice that Copilot has created the **Real Estate Showings** Dataverse table.

    Next, you'll edit the table now that the app has been created.

1. Within the **Data** pane, hover your mouse cursor over the **Real Estate Showings** table. To the right of the table, select (**...**) > **Edit data**.

1. In the **Edit table** dialog, you can add your own columns to the table or modify existing columns.

1. Select your **ID** column header from the table (this may be named differently, or you may want to create it!).

1. From the dropdown menu, select the **Edit column** option.

1. In this example, you don't want the **Data type** to be a **Single line of text**. To change that value, go to the **Edit column** pane, and then from the **Date type** dropdown menu, select **Autonumber**.

1. Select **Save**.

1. Select **New column**.

1. Enter "Property" for the **Display Name**.

1. For **Data type**, select **Lookup** > **Lookup**.

1. For **Related table**, search for and select **Real Estate Property**.

1. Select **Save**.

1. Select **Close** in the lower-right corner of the **Edit table** dialog.

1. In the Data pane, select **Add data** and add the **Real Estate Properties** table.

1. Select the **Save** icon to save the app.

## Configure your canvas app
Let's modify your app so that it displays relevant data. 

1. Select the **Tree view** icon in the left navigation.

1. On the app's main screen, select **ScreenContainer1** > **BodyContainer1** > **SideBarContainer1** > **RecordsGallery1** > **Subtitle1**

1. Notice the Subtitle has been selected on the app preview. Select the Copilot icon near the Subtitle. 

1. Select **Text formatting** to open Copilot suggestions.

1. Review the suggestions for the Subtitle and decide what data you would like to display when a user is browsing Real Estate Showings. Select one of the suggestions.

1. Copilot has updated the expression for the Subtitle. Select **Next** and then close the **Try it out** pop-up, if presented with it.

1. Select **Body1** from the Tree view and update the **Text** value to display the **Status** of ThisItem. To do this, replace the column that is currently set to display (within the single quotation marks) with `Status` and select the appropriate **Status** column from the options.

1. On the app's main screen, select the **Form** control (You can also locate this in the Tree view by selecting **ScreenContainer1** > **BodyContainer1** > **RightContainer1** > **MainContainer1** > **Form1**).

1. On the **Properties** pane on the right, for the **Fields** property, select **Edit fields**.

1. In the **Fields** pane, expand your **ID** field for the Real Estate Showings table.

1. From the **Control type** dropdown menu, change the type to **View text**.

    Because you previously changed the **ID** field to **Autonumber**, you don’t want users entering their own number; Dataverse automatically enters the numbers for you.

1. Select **Add field**.

1. Select **Property** to add the Property field to the form.

1. Close the **Fields** pane.

1. Make a new request for a property that shows in the app by selecting the **Play** button from the upper part of the screen.

1. In the left pane, select the **+New** button.

1. Populate the fields to create a new Real Estate Showing.

1. Select the **check mark** in the upper-right corner of the screen to create a Real Estate Showing.

1. Close out of the app preview by selecting the **X** in the right corner.

    If a dialog appears saying **Did you know?**, select **OK**.

1. Save and publish your Real Estate Showings app.

Congratulations on creating your canvas app with Copilot! 
