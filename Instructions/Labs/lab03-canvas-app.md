---
lab:
    title: 'Lab: Canvas app'
    module: 'Module 4: Building canvas apps'
---

> [!NOTE]
> Effective November 2020:
> - Common Data Service has been renamed to Microsoft Dataverse. [Learn more](https://aka.ms/PAuAppBlog)
> - Some terminology in Microsoft Dataverse has been updated. For example, *entity* is now *table* and *field* is now *column*. [Learn more](https://go.microsoft.com/fwlink/?linkid=2147247)
>
> This content will be updated soon to reflect the latest terminology.


# Lab 03: Canvas app

In this module you will design and build a canvas app for the company employees to submit problem reports.

## What you will learn

  - Import and use a pre-built component library
  - Create a Power Apps canvas app
  - Connect to a data source
  - Filter data
  - Create data Rows
  - Use images with data Rows
  - Embed canvas Power App into Microsoft Teams

## High-level lab steps

  - Import company components
  - Create app and layout main screen (including list of my items)
  - Submit New Report
  - Test
  - Embed canvas app in Microsoft Teams

## Prerequisites

* Must have completed **Lab 02: Data model and model-driven app**

## Detailed steps

### Exercise 1: Create canvas application

In this exercise, you will import a solution with shared components, create a view for the problem report Table, and create a canvas application.

#### Task 1: Import component library solution

In this task, you will import the shared components solution into your environment. This shared component library was built by another team at your company.

1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) page and make sure you are in the correct environment.

2.  Select **Solutions** and click **Import**.

![Import solution - screenshot](03/media/image1.png)

3.  Click **Browse**.

4.  Go to the course resources folder, select the **Shared components** solution, and click **Open**.

5.  Click **Next**.

6.  Click **Import**.

7.  Click **Publish All Customizations** and wait for the publishing to complete.

8.  You should now see the **Shared Components** solution you imported. Click to open the **Shared Components** solution you imported.

9. The solution should have one item in it, **Lamna Healthcare Shared Components**.

![Imported solution components - screenshot](03/media/image2.png)

> [!IMPORTANT]
> There is an issue where importing the app as part of a solution may not add it to your components library. The following steps are designed to resolve the issue.

10. Navigate to **Apps**, Select the **Lamna Healthcare Shared Components App**.
11. Click the **Edit Icon** to edit the app.

![Edit components app](03/media/image2-1.png)

12. After the app opens, click **File** > **Save As**.
13. Save the app as **Lamna Healthcare Share Components A**.

![Save component app under a new name - screenshot](03/media/image2-2.png)

14. Click **OK**.
15. Close the **Lamna Healthcare Shared Components** tab in your browser.

#### Task 2: Create view

In this task, you will create a view that will show the current user’s problem reports. Later you will use this view with the filter function in the canvas app.

1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) page and make sure you are in the correct environment.

2.  Select **Solutions** and click to open the **Company 311** solution.

3.  Locate and click to open the **Problem Reports** Table.

4.  Select the **Views** tab and click to open the **Active Problem Reports** view.

![Open view - screenshot](03/media/image3.png)

5.  Click **Edit filters**.

![Edit filters - screenshot](03/media/image4.png)

6.  Change the filter to **Created By Equals current user** and click **OK**.

![Edit filter - screenshot](03/media/image5.png)

7.  Click on the chevron button next to the Save button and select **Save As**.

![Save view as - screenshot](03/media/image6.png)

8.  Enter **My Reports** for **Name** and click **Save**.

9.  Click **Publish** and wait for the publishing to complete.

10. Click on the **Back** button.

#### Task 3: Create the user application

In this task, you will create a canvas application using the phone form factor.

1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) page and make sure you are in the correct environment.

2.  Select **Solutions** and click to open the **Company 311** solution.

3.  Click **+ New | App |Canvas app | Phone form factor**.

![Create canvas application - screenshot](03/media/image7.png)

4.  Click **Skip** on the welcome screen.

5.  Select your **Region/Country** and click **Get started**.

6.  Click **File** and select **Save**.

7.  Enter **Company 311 Phone App** for name and click **Save**.

8.  Click on the back button.

![Back to app designer - screenshot](03/media/image8.png)

9.  Go to the Tree view and double click **Screen1**.

![Edit screen name - screenshot](03/media/image9.png)

10. Rename the screen **Main Screen**. It’s always a good idea to give your screens a meaningful name.

![Rename screens - screenshot](03/media/image10.png)

11. Select the **Main Screen** and click **Insert**.

![Insert component - screenshot](03/media/image11.png)

12. Select **Get more Components**.

![Get more components - screenshot](03/media/image12-1.png)

13. Expand the **Lamna Healthcare Shared Components A** Library, and select **Header** and **Tab Control**.

![Import header and tab controls from the library - screenshot](03/media/image12-2.png)

14. Click **Import**.

15. Expand **Library components**, select **Header Control** and **Tab Control**. These are both components from the library you imported earlier in the lab.

![Select and insert controls into the app - screenshot](03/media/image12-3.png)

16. Move the **Tab Control** to the bottom of the screen and the **Header Control** to the top of the screens.

17. Select the **Header Control** and change the **Text** value to **"Company 311".**

![Change text value - screenshot](03/media/image13.png)

18. Right click on the Main Screen and select Duplicate screen.

![Duplicate screens - screenshot](03/media/image14.png)

19. Rename the new screen **New Reports Screen**.

20. Select the **Tree view**, select **App** and change the **OnStart** value to the formula below. This formula will create a new variable named My Tabs and set it to a table of tab items.

```javascript
Set('My Tabs', Table( {
	Label: "My Reports",
	Screen: 'Main Screen',
	Icon: "",
	SelectedIcon:""
},
{
	Label: "New Report",
	Screen: 'New Reports Screen',
	Icon: "",
	SelectedIcon:""
}
))
```

> [!IMPORTANT]
> When expressions are copied, the quotes and double quotes are sometimes replaced with their "smart" counterparts which are not valid in formulas. If you copy and paste the expression above, make sure the resulting formula does not contain any errors.     

![tab data variable - screenshot](03/media/image15.png)

21. Select the **Tab Control** in the **Main Screen** and change the **Items** value to **‘My Tabs’**.

![Set tab items - screenshot](03/media/image16.png)

22. Change the **SelectedColor** value to **WhiteSmoke**.

23. Select the **Tab Control** inside the **New Report Screen** and set the Item value to **‘My Tabs’**.

24. Change the **SelectedColor** value to **WhiteSmoke**.

25. Click on the **…** button of the **App** and select **Run OnStart**.

![Run app on start - screenshot](03/media/image17.png)

26. Your tabs should now show the two tabs you added.

![Tab with data - screenshot](03/media/image18.png)

27. Do not navigate away from this page.

### Exercise 2: My reports

In this exercise, you will add a gallery that will show reports created by the current logged in user.

#### Task 1: Add gallery

1.  Select the **Main Screen**, go to the **Insert** tab, click **Gallery**, and select **Vertical**.

![Insert gallery - screenshot](03/media/image19.png)

2.  Rename the new gallery **My Reports Gallery**.

3.  Resize and reposition **My Reports Gallery** and make sure the screen looks like the image below.

![Gallery positioning - screenshot](03/media/image20.png)

4.  Select **My Reports Gallery**, go to the **Properties** pane, and select **Problem Reports** for **Data Source**. If you do not see Problem Reports, click See all Tables.

![Gallery data source - screenshot](03/media/image21.png)

5.  Select the **My Reports** view you created for **View**.

6.  Click **Edit Columns**.

![Edit gallery Columns - screenshot](03/media/image22.png)

7.  Change Subtitle1 to **statuscode**. This is the Status Reason Column.

![Edit Column - screenshot ](03/media/image23.png)

8.  Click File and then click Save.

9.  Click on the Back button.

10. Do not navigate away from this page.

### Exercise 3: Allow removing reports

In this exercise, you will allow unassigned reports to be removed. This will allow users to easily remove any accidental reports.

#### Task 1: Allow remove

1.  Expand the **My Reports Gallery**.

2.  Select the **Icon** inside the **My Reports Gallery**.

![Select icon - screenshot](03/media/image24.png)

3.  Change the **Icon** value to **Icon.Trash**.

![Change icon - screenshot](03/media/image25.png)

4.  Change the **Visible** value to the formula below. This formula will hide the icon if the status reason is not New.

`If(Text(ThisItem.'Status Reason') = "New", true, false)`

![Change visible value - screenshot](03/media/image26.png)

5.  Make sure you still have the icon selected. Change the **OnSelect** value to the formula below. This formula will remove item from the data source.

`Remove('Problem Reports', ThisItem)`

6.  Click **File** and then click **Save**.

7.  Do not navigate away from this page.

### Exercise 4: Add new report

In this exercise, you will add a form to submit new problem reports.

#### Task 1: Add new report form

1.  Select the **New Report Screen**, go to the **Insert** tab, click **Form**, and select **Edit**.

![Insert edit form - screenshot](03/media/image27.png)

2.  Rename the form **New Report Form**.

3.  Select **New Report Form**, go to the **Properties** pane, and select **Problem Report** for **Data source**.

4.  Click **Edit fields**.

![Edit form Columns - screenshot](03/media/image28.png)

5.  Remove the **Status Reason** Column.

![Remove Columns from form - screenshot](03/media/image29.png)

6.  Remove the **Created On** Column.

7.  Remove the **Location** Column.

8.  Click **+ Add field**.

9.  Select **Details**, **Building**, **Department**, and **Photo**, and then click **Add**.

![Add Columns to form - screenshot](03/media/image30.png)

10. Resize and reposition the form so it takes most of the page and leave enough room for a button in the bottom.

![New report form - screenshot](03/media/image31.png)

11. Select the **New Report Screen**.

12. Go to the **Insert** tab and select **Button**.

13. Rename the button **Submit Report**.

14. Place the button below the form and make it stretch across the screen

15. Change the **Submit Report** button text to **Submit**

16. Select the Submit Report button and change the **OnSelect** value to the formula below. This formula will create a new Row and clear the form when the button is clicked.

`SubmitForm('New Report Form'); NewForm('New Report Form')`

17. Select the **New Report Form**.

18. Change the **OnSuccess** value to the formula below. This formula will show a notification after the new Row gets created.

`Notify("Created new problem report Row")`

19. Select the **New Report Screen**.

20. Set the **OnVisible** value to the formula below. This formula will create a new form when the screen becomes visible.

`NewForm('New Report Form')`

21. Click **File** and then click **Save**.


### Exercise 5: Test the application

In this exercise, you will test the canvas application you created by submitting a problem report.

#### Task 1: Test application

1.  Select the **Main Screen** and click **Preview the app**.

![Preview application - screenshot](03/media/image32.png)

2.  The application should load, and the list should show all the reports you created.

![Main screen - screenshot](03/media/image33.png)

3.  Select the **New Report** tab.

4.  The **New Report Form** should load. Fill out the form and click on the **Photo** Column.

5.  Select an image.

6.  Click **Submit**

7.  The Row should get created successfully and you should see the success message.

![Save Row message - screenshot](03/media/image34.png)

8.  Select the **My Reports** tab.

9.  You should see the new report you created. Click **Delete** to test the delete.

![Delete Row - screenshot](03/media/image35.png)

10. The Row should be deleted and removed from the list.

![Row list after deletion - screenshot](03/media/image36.png)

11. Close the application.

### Exercise 6: Embed canvas app in Microsoft Teams

In this exercise, you will add the Company 311 Phone App that you created earlier, to Microsoft Teams as a way for staff to be able to log issues directly within Teams.

#### Task 1: Setup Company 311 Team

In this task you will setup a Microsoft Teams team for the Lamna Healthcare Company, if you have not done so previously.

1.  Navigate to [Microsoft Teams](https://teams.microsoft.com) and sign in with the same credentials you have been using previously.

2.  Select **Use the web app instead** on the welcome screen.

![Teams Screen](03/media/image-3-teams.png)

3.  When the Microsoft Teams window opens, dismiss the welcome messages.

4.  On the bottom left corner, choose **Join or create a team**.

5.  Select **Create a team**.

![Create Team](03/media/image-3-createteam.png)

6.  Press **From scratch**.

7.  Select **Public**.

8.  For the Team name choose **Company 311** and select **Create**.

9.  Select **Skip** adding members to Company 311.


#### Task 2: Add canvas app to Teams

1.  Navigate to [Microsoft Teams](https://teams.microsoft.com)

2.  Select the **General** channel of the **Company 311** team.

3.  On the top of the page, press the **+** symbol to add a new tab.

![Add Tab in Teams](03/media/image-3-addpowerbitab.png)

4.  Search for **power** and select **PowerApps** from the results.

5.  Press **Add** to add Power Apps to Teams

![Add Power Apps in Teams](03/media/image-3-powerappsteams.png)

6. Select the **Company 311 Phone App** that you created earlier in this lab. 

> [!IMPORTANT]
> If you do not see the app you need to go back to the app editor and publish the app

7. Press **Save**

8. The **Company 311** app should now appear on a tab in Microsoft Teams.

![Add Power Apps in Teams](03/media/image-3-powerappinteams.png)

Click **Next** to advance to the next lab. 
