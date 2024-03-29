---
lab:
    title: 'Lab 05.1: Build canvas apps'
    module: 'Module 05: Create a canvas app'
---

# Lab 05.1: Build canvas apps

In this module you will design and build a canvas app for the company employees to submit problem reports.

## What you will learn

  - Import and use a pre-built component library
  - Create a Power Apps canvas app
  - Connect to a data source
  - Filter data
  - Create data rows
  - Use images with data rows
  - Bonus Exercise (optional): Create a canvas app from an image

## High-level lab steps

  - Import company components
  - Create app and layout main screen (including list of my items)
  - Submit New Report
  - Test
  - Bonus Exercise (optional): Create a canvas app from an image

## Prerequisites

* Must have completed **Lab 02.1: Data model**

## Detailed steps

### Exercise 1: Create canvas application

In this exercise, you will import a solution with shared components, create a view for the Problem Report table and create a canvas application.

#### Task 1: Import component library solution

In this task, you will import the shared components solution into your environment. This shared component library was built by another team at your company.

1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) page and make sure you are in the correct environment.

2.  Select **Solutions** and select **Import solution**.

3.  Select **Browse**.

4.  Go to the Lab Resources folder, select the **Shared Components** solution file, and select **Open**. You may also download the file to your computer [here](https://github.com/MicrosoftLearning/PL-100-Microsoft-Power-Platform-App-Maker/raw/jan2024update/Instructions/Labs/03/Resources/SharedComponents_1_0_0_4.zip). 

    > **TIP**
    > 
    > The lab resources can be found here: `F:\Instructions\Labs\03\Resources\SharedComponents_1_0_0_4.zip`

5.  Select **Next**.

6.  Select **Import** and wait for the import to complete.

7.  Select **Publish all customizations** and wait for the publishing to complete.

8.  Open the **Shared Components** solution.

9.  The solution should have one item in it: **Lamna Healthcare Shared Components**

10. Navigate to the [Power Apps maker portal](https://make.powerapps.com/) page and make sure you are in the correct environment.    

11. Select **Apps** and select the **Lamna Healthcare Shared Components App** to edit the app.

13. If prompted, select your **Region/Country** and select **Get started** or select **Skip**.
    
    > **NOTE**
    >
    > When the app is open in Edit mode, move on to next step, as the Preloader component shows a Loading icon but it is not actually waiting for something to load.

14. After the app opens, select the drop-down &#709; next to the **Save** button and select **Save as**.

15. Change app name to `Lamna Healthcare Shared Components A` and select **Save**.

16. Select **OK** when prompted to save as a new library.

17. Close the **Lamna Healthcare Shared Components** tab in your browser.


#### Task 2: Create view

In this task, create a view that will show the current user’s problem reports. Later, this view will be used with the filter function in the canvas app.

1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) page and make sure you are in the correct environment.

2.  Select **Solutions** and open the **Company 311** solution.

3.  Locate and open the **Problem Report** table.

4.  Select **Views** in the tree view in the **Objects** pane and open the **Active Problem Reports** view.

    ![A screenshot of the solution explorer screen with Views selected under problem report table and the cursor over the active problem reports view link](03/media/lab3-Exx1-task2-1.png)

5.  Select **Edit filters**.

6.  You want to show the Problem Reports that were created by you. Change Status Reason to **Created By** and Equals to **Equals current user**.

7.  Select **Ok**.

8.  Select **Save As**.

9.  Enter `My Reports` for **Name** and select **Save**.

10.  Select **Save and publish** and wait for the publishing to complete.

11. Select the **🡠 Back** button on the command bar to go back to the Problem Report table details.


#### Task 3: Create the user application

In this task, create a canvas app using the phone form factor.

1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) page and make sure you are in the correct environment.

2.  Select **Solutions** and open the **Company 311** solution.

3.  Select **+ New** > **App** > **Canvas app**.

4.  Enter `Company 311 Phone App` for **App name**, select **Phone** for format, and select **Create**.

5.  Select **Skip** if presented with a pop-up.

6.  In the **Tree view**, select the three dots (**...**) beside **Screen1** and select **Rename**.

7.  Rename the screen to `Main Screen` and press Enter on your keyboard.

    It’s always a good idea to give screens a meaningful name.

8.  Select the **Main Screen** and then select **+** icon from the left navigation pane.

9.  Select **Get more components** at the bottom of the Insert pane.

10. In the **Lamna Healthcare Shared Components A** Library, select **Header** and **TabControl**, and then select **Import**.

    ![A screenshot of the import components window with Ta control and header selected](03/media/lab3-Exx1-task3-5.png)

11. Expand **Library components** in the Insert pane, select **Header** and **Tab Control**. These are both components from the library you imported earlier in the lab.

    ![A screenshot with a border around the library components Header and Tab control](03/media/lab3-Exx1-task3-6.png)

12. Move the **Tab Control** to the bottom of the screen and the **Header Control** to the top of the screen.

13. Select the **Header Control**.

14. You want to change the **Text** value of the Header Control. Use the **Property selector** to change the property to **Text** and then populate `Company 311` as the value in the formula bar. You will use the Property selector to change properties of app components in this manner throughout this lab.

    ![A screenshot of a border around the expression tab with the text value set to company 311](03/media/lab3-Exx1-task3-7.png)

15. Set the **Height** of the **Header Control** to `75`

16. In the **Tree view**, right-click on the Main Screen and select **Duplicate screen**.

    ![A screenshot with a border around the duplicate screen button](03/media/lab3-Exx1-task3-9.png)

17. Rename the new screen `New Reports Screen`

18. Select the **Tree view**, select **App** and change the **OnStart** value to the formula below. This formula will create a new variable named My Tabs and set it to a table of tab items.

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

    > **IMPORTANT**
    >
    > When expressions are copied, the quotes and double quotes are sometimes replaced with their “smart” counterparts which are not valid in formulas. If you copy and paste the expression above, make sure the resulting formula does not contain any errors.

19. Select the **Tab Control** component in the **Main Screen** and change the **Items** value to `'My Tabs'`

    ![A screenshot of the items value set to my tabs for Tab control](03/media/lab3-Exx1-task3-11.png)

20. With the Main Screen Tab Control component still selected, change the **SelectedColor** value to `Color.WhiteSmoke`

21. Select the **Tab Control** inside the **New Report Screen** and set the **Items** value to `'My Tabs'`

22. With the New Report Screen Tab Control still selected, change the **SelectedColor** value to `Color.WhiteSmoke`

23. In the **Tree view**, right-click on **App** and select **Run OnStart**.

    ![A screenshot of the run on start button coming from the ellipsis icon for see more under the app button](03/media/lab3-Exx1-task3-12.png)

24. The tab names should update.

    ![A screenshot of the two tabs you added](03/media/lab3-Exx1-task3-13.png)

25. Select **Save** from the command bar.

    Do not navigate away from this page.


### Exercise 2: My reports

In this exercise, add a gallery that will show reports created by the current logged in user.

#### Task 1: Add gallery

1.  In the tree view, select the **Main Screen**

2.  Select **Insert** menu, then select **Vertical gallery**.

3.  Select the tree view and rename the new gallery to `My Reports Gallery`

4.  Resize and reposition **My Reports Gallery**, setting the **Y** value to `75` and the **Height** value to `1000` 

    Your Main Screen should resemble this example:

    ![A screenshot of the my reports gallery selected](03/media/lab3-Exx2-task1-2.png)

5.  Select **My Reports Gallery**, go to the **Properties** pane, and select **Problem Reports** for **Data Source**. If you do not see Problem Reports, select **See all tables** or **Search** for the table.

6.  Select the **My Reports** view you created for **View**.

7.  Under **Fields**, select **Edit** (you may also have "7 selected" displayed; click "7 selected" to edit the fields).

8.  Change Subtitle1 to **statuscode**. This is the **Status Reason** column.

9.  Select **Image** control within the gallery by expanding **My Reports Gallery** in the tree view and selecting **Image1**.

10.  Set **Image** value to the formula below. This allows images to be displayed correctly when view is used as a source.

    `LookUp('Problem Reports', 'Problem Report' = ThisItem.'Problem Report').Photo`

11.  Select the **Save** icon.

    Do not navigate away from this page.


### Exercise 3: Allow removing reports

In this exercise, allow unassigned reports to be removed. This will allow users to easily remove any reports that were accidentally created.

#### Task 1: Allow remove

1.  Expand the **My Reports Gallery**.

2.  Select the **NextArrow1** icon inside the **My Reports Gallery**.

    ![A screenshot of the arrow icon inside the my reports gallery](03/media/lab3-Exx3-task1-1.png)

3.  In the **Tree view**, double-click **NextArrow1** and rename it to `Remove Report`

4.  While still selected on the Remove Report icon, change the **Icon** value to **Icon.Trash**.

5.  Change the **Visible** value to the formula below. This formula will hide the icon if the status reason is not New.

    `If(ThisItem.'Status Reason' = 'Status Reason (Problem Reports)'.New, true, false)`

6.  Make sure you still have the **Remove Report** icon selected. Change the **OnSelect** value to the formula below. This formula will remove the Problem Report row when a user selects the Remove Report (trash) icon.

    `Remove('Problem Reports', ThisItem)` 

7.  Change the **Tooltip** value to `"Remove this report"` 

8.  On the properties pane, set all the **Padding** values to `0`. This allows the icon to better fill the space in the gallery row. 

9.  Select **Save**. 

    Do not navigate away from this page.

### Exercise 4: Add new report

In this exercise, add a form to the canvas app to submit new problem reports.

#### Task 1: Add new report form

1.  Select the **New Reports Screen**, select **Insert**, then select **Edit Form**.

2.  Rename the form to `New Report Form`

3.  Select **New Report Form**, go to the **Properties** pane, and select **Problem Reports** for **Data source**.

4.  Select **Edit fields** (this may display as "4 selected" beside Fields; select "4 selected).

5.  Remove the **Status Reason** Column.

6.  Remove the **Created On** Column.

7.  Select **+ Add field**.

8.  Select **Building**, **Details**, and **Photo**, and then select **Add**.

9.  Close the **Fields** pane.

10. Resize and reposition the form, setting the **Y** value to `75` and the **Height** value to `900` 

    It takes most of the page and leave enough room for a button at the bottom.

    ![A screenshot of the form resized and reposition for room at the bottom for a button](03/media/lab3-Exx4-task1-4.png)

11. Select the **New Reports Screen**.

12. Select **Insert** then select **Button**.

13. Rename the button `Submit Report`

14. Move the button below the form, or set **X** value to `180` and **Y** value to `990`

15. Change the **Submit Report** button **Text** property to `Submit`

16. Select the **Submit Report** button and change the **OnSelect** value to the formula below. This formula will create a new Row in the Problem Reports table.

    `SubmitForm('New Report Form')`

17. Select the **New Report Form**.

18. Change the **OnSuccess** value to the formula below. This formula will show a notification after the new Problem Report row gets created and clears the form when the record creation is successful.

    `Notify("Created new problem report row");NewForm('New Report Form')`

19. Select the **New Reports Screen**.

20. Set the **OnVisible** value to the formula below. This formula will create a new form when the screen becomes visible.

    `NewForm('New Report Form')`

21. Select **Save**.

22. Select **Publish**.

23. Select **Publish this version** and wait for the publishing to complete.

    Do not navigate away from this page.


### Exercise 5: Test the application

In this exercise, test the canvas application by submitting a problem report.

#### Task 1: Test application

1.  Select the **Main Screen** and select the Play icon to **Preview the app**.

    ![Play button to preview the app](03/media/lab3-Exx5-task1-1.png)

2.  The application should load, and the list should show all the reports you created.

    ![A screen of your loaded application](03/media/lab3-Exx5-task1-2.png)

3.  Select the **New Report** tab.

4.  The **New Report Form** should load. Fill out the form and select the area under the **Photo** label.

5.  Select an image.

6.  Select **Submit**.

7.  The row should get created successfully and you should see the success message.

8.  Select the **My Reports** tab.

9.  You should see the new report you created. Select the **Remove Report** button to test the delete.

    ![A Screenshot with an arrow pointing to the trash can icon to delete](03/media/lab3-Exx5-task1-4.png)

10. The row should be deleted and removed from the list.

    ![A screenshot of the row deleted and removed from the list](03/media/lab3-Exx5-task1-5.png) 

11. **Close** the preview mode.

12. **Close** the app studio by closing the browser tab.


### BONUS EXERCISE: Explore other ways to build canvas applications
In this exercise, create a canvas app from an image mockup. *This exercise is optional and not required to continue to the next lab.*

#### BONUS TASK 1: Create an app from an image
1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) page
    and make sure you are in the correct environment.
    
2.  Select + **Create** on the left navigation.

3.  Under the **Start From** section, select **Image**.

5.  From the **Convert into an app** screen, select **Next**.

6.  Name the app **Report Problems** and set the app format to **Phone**.

7.  Select the **Choose File** button and select the **Report a Problem.png**
    file from your class resources folder, select the **Next** button. (You can find that file [here](https://github.com/MicrosoftLearning/PL-100-Microsoft-Power-Platform-App-Maker/blob/jan2024update/Instructions/Labs/03/Resources/Report%20a%20Problem.png))

8.  On the Draw tags and assign components screen, verify your screen matches
    the image below:

    ![A screenshot of a computer Description automatically generated](03/media/lab3-Exx6-task1-3.png) 

9.  Select the **Text Input** box under the **Status** label, from the menu that
    appears, change the **Data Type** to **Drop Down.**

10.  Select the **Text Input** box under the **Resolved On** label, from the menu
    that appears, change the **Data Type** to **Date Picker.**

11. Your tagged form should resemble the image below:

![A screenshot of a computer Description automatically generated](03/media/lab3-Exx6-task1-6.png)

11.  Select the **Next** button.

12.  On the **Set up your Data** screen, ensure that **Connect to a Dataverse
    table is selected**, then select **Next.**

13.  On the **Select table** screen, choose **Problem Report**, then select **Next**. Next, we will tag the specific fields to the correct column in Dataverse.

> **NOTE**
>
> When defining how the columns will be set up, you need to make sure that the selector includes both the **Label** and **Input** Field. Your app may not render correctly if not.

14.  Select the Tag around the **Name** label and the input field.

15.  Assign the item to the **Title** column, select **Save**.

16.  Using the table below, repeat the above process for each item on the form to update the column that they represent.

| Field       | Dataverse Column |
|-------------|------------------|
| Building    | Building         |
| Details     | Details          |
| Department  | Department       |
| Status      | Status Reason    |
| Resolved On | Resolved On      |
| Resolution  | Resolution       |

17.  Once complete, your tagged columns should resemble the image below, select
    the **Next** button.

![A screenshot of a computer Description automatically generated](03/media/Lab3-Ex6-step17.png)

18.  On the **Review** screen, verify that your Problem Report columns are mapped correctly.

19.  Select **Create.**
    
> **NOTE**
>
> It can take a few minutes for your new app to be created.

20.  Your newly created app will resemble the image below:

![A screenshot of a computer Description automatically generated](03/media/Lab3-Ex6-step20.png)
    
#### BONUS TASK 2: Modify your canvas app
When you create an app from an image, you are somewhat limited as to the types of fields that you can select. For this reason, some items such as lookup fields will not display properly since the data type was defined as text. For this reason, we will make some modifications to the application to fix this.

Both the Department and Building field are lookup fields. We are going to remove the generated ones and replace them with the actual fields from Dataverse.

1.  On the left side of your app screen, select the **Form1** control.

2.  In the **Properties** section on the right of the screen, select **Edit
    Fields.**

3.  Hover the **Building_DataCardXXX (Custom)** field and **Remove** it.

4.  Hover the **Department_DataCardXXX (Custom)** field and **Remove** it as
    well.

    Next, we are going to add the actual Lookup field from Dataverse to the app.

5.  Select **Add Fields.**

6.  From the menu that appears, select the **Building** and **Department**
    fields and select **Add**. Next, we are going to make some formatting changes to ensure that all the
    Data Cards on the form look the same.

7.  Close the Fields pane.

8.  Using the **Sizing controls** on **Form1**, make the form bigger so that the
    **Department** field displays.

9.  In the **Fields** menu to the left of the canvas app screen, move the
    **Building** field below the **Name** field.

10.  Move the **Department** field below the **Building** field.

11. On **Form1**, Select the **Label** control on the **Details** Data Card.

12. Change the **Font** to **21** and the **Font Weight** to **Semibold**.

13. Repeat that process for the **Status**, **Resolved On** and **Resolution**
    Data Cards.

14. On **Form1** in Tree View, select the **Name_DataCardXXX (Custom)** control

15. Using the **Sizing** controls, change the **Height** of the control to about
    142.

16. Move the **Name** Data Card’s, **Textinput** control to the bottom of the
    control, and expand the controls width so that it is the same width of the
    other controls on the form.

17. Move the controls **TextLabel** to align with the other labels on the form.

18. Change the **Name Label Font** to **21** and the **Font Weight** to
    **Semibold**.

19. If necessary, resize the **Form** control to ensure that the **Resolution**
    field is completely displayed.

20. Your completed App should resemble the Image below.

    ![A screenshot of a computer Description automatically generated](03/media/Lab3-Ex6-step39.png)
