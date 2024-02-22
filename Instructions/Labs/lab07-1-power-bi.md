---
lab:
    title: 'Lab 07.1: Build Power BI dashboards'
    module: 'Module 07: Create and use analytics in Power BI'
---

# Lab 07.1: Build Power BI dashboards

In this lab, you will build a Power BI dashboard that visualizes data about problems reported by company employees.

## What you will learn

  - How to refine the data model and prepare it for reporting
  - How to create a Power BI visualization 
  - How to embed a Power BI report in Microsoft Teams

## High-level lab steps

We will follow the below steps to design and create the Power BI dashboard:

-   Transform the data to include user-friendly descriptions for the related rows (lookups)
-   Create and publish a report with various visualizations of the information about problem reports
-   User natural language query to build additional visualizations
-   Build mobile view
-   Embed the Company 311 Power BI report to Microsoft Teams

## Prerequisites

* Must have completed Lab 02.1: Data model
* Permissions to install programs on your computer (required for Power BI Desktop installation)

## Things to consider before you begin

-   Who is the target audience of the report?
-   How will the audience consume the report? Typical device? Location?
-   Do you have sufficient data to visualize?
-   What are the possible characteristics you can use to analyze data about the visits?

## Detailed steps

### Exercise 1: Create a workspace

In this exercise, you will create a Power BI report based on data from Microsoft Dataverse tables.

#### Task 1: Create a new workspace

Before you begin, download the [problem-reports-data.pbix](https://github.com/MicrosoftLearning/PL-100-Microsoft-Power-Platform-App-Maker/raw/master/Instructions/Labs/05/Resources/problem-reports-data.pbix) file and save it to your computer.

1.  Navigate to [Power BI](https://app.powerbi.com)

2.  On the left side of your screen, select **Workspaces**.

3.  Choose **New Workspace**.

4.  Name the Workspace `311 Workspace`.

5.  Select **Apply**.

6.  Select **Upload**.

7.  From the menu that appears, select **Browse**.     

8.  Locate and select **problem-report-data.pbix** file that you've downloaded earlier.

    > **TIP** 
    > 
    > This file can also be found here: ```F:\Instructions\Labs\05\Resources\problem-reports-data.pbix```

9.  Once data load is complete, select **problem-reports-data** report (will look like "..." when you hover over it).

10.  Select **Settings**.

11.  Change the **Report Name** to `Problem Report`.

12.  Select **Save**.

### Exercise 2: Create Power BI Report 

In this exercise, you will create a Power BI report based on data from Microsoft Dataverse tables.

#### Task 1: Create Chart and Time Visualizations

1.  Select the **problem report** with a type of **Report**.

2.  Once the report is open, select **Edit**. 

3.  Select the **Pie chart** icon in the **Visualizations** panel to insert the chart.

4.  Expand **lh_ProblemReport** table in the **Data** panel, drag **Building** Column and drop it into **Legend** target box.

5.  Drag **Problem Report** Column and drop it into **Values** target box.

6.  Resize the pie chart using corner handles so that all chart components are visible. Your report should now look like this:

    ![A screenshot with a border around the legend next to pie chart after resizing to make all your components visible](05/media/Lab5-Ex2-Task1-4.png)

7.  Select the report's design surface outside of the chart area (this will deselect your pie chart).

8.  On the **Visualizations** pane, select **stacked column** chart.

9.  Drag **Problem Report** Column and drop it into the **Y-axis** target box.

10.  Drag **Status** Column and drop it into **X-axis** target box.

11.  **Resize** the chart as required using the corner handles.

12.  **Test** the report interactivity:

- Select various building slices on the pie chart and observe changes on the stacked column chart.
- Select various bars on the stacked column chart and observe changes on the pie report.

12. Save work in progress by selecting **File** | **Save**.


### Exercise 3: Create Power BI Dashboard


#### Task 1: Create Power BI Dashboard

1.  Click on **311 Workspace**. If it is not in your menu, select **Workspaces** and then **311 Workspace**

2.  Select the **Problem report** with a type **Report**. 

3.  Select **Pin to a dashboard** on the menu (depending on the layout, you may need to press **...** to show additional menu items).

4.  Select **New dashboard** on the **Pin to dashboard** prompt.

5.  Enter `Problem Management Dashboard` as the **Dashboard name** and select **Pin live**.

6.  Select **Go to dashboard**.


#### Task 2: Add Visualizations Using Natural Language

1.  If not there already, go to the **311 workspace** and select the **Problem Management Dashboard**.

2.  Select **Ask a question about your data** on top of the dashboard.

3.  Enter **funnel count of problem reports by status** in Q&A area. The funnel chart will be displayed.

4.  Select **Pin visual**.

5.  Select **Existing dashboard**, select **Problem Management dashboard**, select **Pin**.

6.  Select **Exit Q&A** to return to your dashboard.


#### Task 3: Build Mobile Phone View

1.  If not already open, select the **Problem Management dashboard** from the **Dashboards** area.

2.  Select **Edit** and select **Mobile Layout** from the drop-down box.

3.  **Rearrange** the tiles as desired.

4.  Select the **down arrow** next to **Problem Management Dashboard** in the upper left corner of your screen.

5.  Under **location**, select **311 Workspace**.

6.  Ensure you select **problem report** with type **Report**.

7.  Select **File** and then select **Generate QR Code** from the drop down box.

8.  If you have a mobile device, scan the code using a QR scanner app available on both iOS and Android platforms.

    > **NOTE**
    >
    > To access the dashboard and report, you will have to sign in on the phone as the same user.

9.  Navigate and explore the reports and dashboards on your mobile device. 


### Exercise 4: Embed Power BI report

In this exercise, you will add the Company 311 Power BI report to Microsoft Teams and to the Company 311 Admin Model-driven application as a way for management and staff to be able to view the reports from directly within Teams and the Model-driven application. 

#### Task 1: Setup Company 311 Team

In this task you will setup a Microsoft Teams team for the Lamna Healthcare Company, if you have not done so previously.

1.  Navigate to [Microsoft Teams](https://teams.microsoft.com) and sign in with the credentials you have been using previously.

2.  Select **Use the web app instead** on the welcome screen.

    ![A screenshot of the Microsoft Teams landing page and a border around the use the web app instead button](05/media/Lab5-Ex4-Task1-1.png)

3.  When the Microsoft Teams window opens, dismiss the welcome messages.

4.  On the bottom left corner, choose **Join or create a team**.

5.  Select **Create a team**.

6.  Press **From scratch**.

7.  Select **Public**.

8.  For the Team name choose **Company 311** and select **Create**.

9.  Select **Skip** adding members to Company 311.


#### Task 2: Embed Power BI report to Teams

1.  Navigate to [Microsoft Teams](https://teams.microsoft.com).

2.  Select the **General** channel of the **Company 311** team.

3.  On the top of the page, press the **+** symbol to add a new tab.

4.  Search for and select **Power BI** from the results.

5.  Expand the **311 Workspace** and select the report you created earlier in this lab, then select **Save**.

6.  You should now have your Power BI report in a tab in Microsoft Teams.

    ![A screenshot of your Power BI report in a tab in Microsoft Teams](05/media/Lab5-Ex4-Task1-5.png)

#### Task 3: Embed Power BI report to Model-driven app

1.  Navigate to [Power Apps maker portal](https://make.powerapps.com/) and make sure you are in your practice environment.

2.  Select **Solutions** and open the **Company 311** solution.

3.  Select **+ New** and select **Dashboard | Power BI embedded**.

4. Enter `Problem management` for **Display name**, select **Power BI report** for type, uncheck **Show reports in this environment only** and select **311 Workspace** for **Power BI workspace**, select **Problem management** for **Power BI report** and select **Save**.

5.  Select **Publish all customizations** and wait for the publishing to complete.

6.  While still in the Company 311 solution, open the **Company 311 Admin** Model-driven application.

7. In app designer, make sure you have **Manage Problems** area selected. If not, click on the arrows and select **Manage Problems**.

8. Select the ellipsis (...) next to **Navigation** title and select **New group**.

9. Go to the **Properties** pane and enter **Reports** for **Title**.

10. Select the **Reports** group you just created, select **+ New**.

11. Select **Dashboard** for Type and click **Next**. 

12. **Under Power BI dashboards** check the checkmark next to **Problem management** and then select **Add**.

13. Select the ellipsis (...) next to the **Reports** group and select **Move up**. 

14. Select **Save**, then select **Publish**, wait for the publishing to complete and then select **Play**. 

15. The report should load. Interact with the report and make sure it behaves as expected.


### Exercise 5: Power BI embedded canvas app

In this exercise, you will add a canvas application to Power BI as a visual.

#### Task 1: Add canvas

1.  Navigate to [Power BI](https://app.powerbi.com).

2.  Select **Workspaces** and then select to open **311 Workspace**.

3.  Open the **Problem management** report.

4.  Select **Edit**.

5.  **Resize** and **reposition** the visuals as shown below.

    ![Power BI visuals - screenshot](05/media/Lab5-Ex5-Task1-1.png)

6.  Select an empty area of the canvas, go to the **Visualizations** pane and select **Power Apps for Power BI**.

7.  Select the Power BI visual you just created, expand the **lh_problemreport** table and select **Problem Report** column. Drag the **Problem Report** column into **Add data fields here** under **Visualizations >> PowerApps Data**

8.  Select your practice environment and select **Create new**.

9.  A **new browser tab** should open and load the **Power Apps Studio**.

10. Do not navigate away from this page.


#### Task 2: Customize the app

1.  Right-click on the **Gallery** and select **Delete**.

2.  Select **Settings** from the toolbar. 

3.  Select the **Display** tab.

4.  Change the **Orientation** to **Landscape** and select **Apply** on the popup. 

5.  Close the **Settings** window. 

6.  Select **Data** and select **Add data**.

7.  Select the **Problem reports** table.

8.  From the **Tree view**, select the **App** object.

9.  Select the **OnStart** property of the **App** object (found in the **Advanced** tab) and set it to the formula below. This formula will create two variables one to keep track of the current index of the reports table and another to keep track of the current item row.

    ```Set(currentIndex,1);Set(CurrentItem, LookUp('Problem Reports', 'Problem Report' = GUID(Last(FirstN([@PowerBIIntegration].Data,currentIndex)).'Problem Report'))) ```

10. Select the **+ Insert** button, expand **Media** group, then select **Image**.

11. Set the **Image** value to the formula below.

    ```CurrentItem.Photo```

12. Select the **...** menu button of the **App** object and select **Run OnStart**.

13. The photo from the Problem Report should load. If you are not seeing the photo, then go to the Admin **Model-driven App** and add photo to any Problem Report records where the **Photo** field is **empty**. 

14. Set the **X** value of the image to **0**.

15. Set the **Y** value of the image to **0**.

16. Set the **Width** value of the image to the formula below. (You will need to enter it using the Formula bar)

    ```Parent.Width```

17. Set the **Height** value of the image to the formula below. (You will need to enter it using the Formula bar)

    ```Parent.Height```

18. The image should fill the screen.

19. Do not navigate away from this page.


#### Task 3: Add controls

1.  Select the **Insert** tab and select **Text label**.

2.  Select **Label1** from the tree view and set the **Text** value to the formula below.

    ```CurrentItem.Title```

3.  Set the **Height** value of the label to **60**.

4.  Set the **X** value of the label to **0**.

5.  Set the **Y** value of the label to formula below.

    ```Parent.Height - Self.Height```

6.  Set the the **Width** value of the label to formula below.

    ```Parent.Width```

7.  Set the **Fill** value of the label to `RGBA(0, 108, 191, .5).`

8.  Set the **Color** value of the label to `RGBA(255, 255, 255, 1)`.

9.  Set the **Align** value to the formula below.

    ```Align.Center```

10. If you don't see the title, select the **...** button of the **App** object and select **Run OnStart** again.

11. Select **+ Insert**, enter **next** in the search box, then select **Next arrow** under **Icons**.

12. Double-click on the name of the icon you just added and rename it **Next icon**.

13. Select **+ Insert**, enter **back** in the search box, then select **Back arrow** under **Icons**.

14. Double-click on the name of second icon you just added and rename it **Back icon**.

15. Drag and place the **Next icon** above the right side of the label.

16. Drag and place the **Back icon** above the left side of the label.

17. The icons should now look like the image below.

    ![Icon location - screenshot](05/media/Lab5-Ex5-Task1-11.png)

18.  Select the **Next icon** and set the **OnSelect** value to the formula below.

    ```UpdateContext({CurrentItem: LookUp('Problem Reports', 'Problem Report' = GUID(Last(FirstN([@PowerBIIntegration].Data,currentIndex+1)).'Problem Report'))});UpdateContext({currentIndex: currentIndex+1})```

19.  Set the **DisplayMode** value of the **Next icon** to the formula below.

    ```If(currentIndex = CountRows([@PowerBIIntegration].Data), DisplayMode.Disabled, DisplayMode.Edit)```

20. Select the **Back icon** and set the **OnSelect** value to the formula below.

    ```UpdateContext({CurrentItem: LookUp('Problem Reports', 'Problem Report' = GUID(Last(FirstN([@PowerBIIntegration].Data,currentIndex-1)).'Problem Report'))});UpdateContext({currentIndex: currentIndex-1})```

21. Set the **DisplayMode** value of the **Back icon** to the formula below.

    ```If(currentIndex > 1, DisplayMode.Edit, DisplayMode.Disabled)```

22. Select **+ Insert**, enter **check** in the search box, then select **Check** under **Icons**.

23. In the tree view, double-click **Icon1** and rename the Check icon to **Complete icon**. 

24. Move the **Complete icon** to the top right of the screen.

25. Set the OnSelect of the **Check icon** to the formula below. This formula will update the status of the row to completed and then refresh Power BI.

    ```Patch('Problem Reports', CurrentItem, {'Status Reason': 'Status Reason (Problem Reports)'.Completed}); PowerBIIntegration.Refresh()```

26. Select **Play**.

27. Select the **next** and **back** icons and make sure the image changes.

28. **Close** the preview.

29. Select the **Save** button.

30. Enter **Power BI embed app** for **Name**.

31. Select **Save**.

32. Select the **Publish** button. Select **Publish this version**.

33. **Close** the app studio browser window or tab.

34. You should now be back on the Power BI report. Select **Refresh** on the top header. 

35. Select the **Next** and **Back** icons to make sure the application loads the images.

36. Select the **Completed** column of the stacked column chart and make a note how many rows are completed.

37. Select any column of the stacked column chart apart from **Completed**. Select the **next** icon to see the next image.

38. Select the **Complete** icon.

39. The completed count should increase. If the completed count doesn't increase, select refresh and wait for the visuals to be refreshed.

40. **Save** the report.

