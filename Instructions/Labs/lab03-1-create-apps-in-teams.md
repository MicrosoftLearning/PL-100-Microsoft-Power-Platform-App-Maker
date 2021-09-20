---
lab:
    title: 'Lab 03.1: Create apps in Teams'
    module: 'Module 03: Create a canvas app'
---

> [!NOTE]
> Effective November 2020:
>
> - Common Data Service has been renamed to Microsoft Dataverse. [Learn more](https://aka.ms/PAuAppBlog)
> - Some terminology in Microsoft Dataverse has been updated. For example, *entity* is now *table* and *field* is now *column*. [Learn more](https://go.microsoft.com/fwlink/?linkid=2147247)
>

Lab 03.1: Create apps in Teams
=================================

## Scenario

It is not uncommon for organizations to accumulate unused computer Peripherals, power cords and other electronics. Your organization is taking steps to reuse existing devices and computer peripherals before ordering new equipment.

You are asked to create an application where users can post devices they no longer need and browse through what their colleagues posted.

## Requirements

1)	Application must use Dataverse for Teams.
2)	Users should be able to create new items, edit items they created and see items created by other users.
3)	Items should be removed from the list if they are no longer available.
4)  Allow users to reserve an item.
5)  Allow user to mark item for pick up.
6)  If item is reserved, only reserved user should be able to mark item picked up.
7)  Users should be able to search items.

## What you will learn

1)	How to create an application using Dataverse for Teams.
2)	How to publish application.
3)	How to give other users permission to your application.

## Detailed steps

### Exercise 1: Get started with Microsoft Dataverse for Teams

In this exercise, you will create a new team and install Power Apps for Teams.

#### Task 1: Create team
In this task you will create a new team

1. Navigate to [Microsoft Teams](https://teams.microsoft.com).
2. Select **Teams**, click **Join or create a team** and click **Create Team**.

![A screenshot with a box around the teams button on the left side of the window and an arrow pointing to the create team button](03-1/Media/ex1-t1-image1.png)

3. Select **From scratch**.
4. Select **Public**.
5. Enter **Green** for Team name and click **Create**.

![A screenshot with the word green in the team name field](03-1/Media/ex1-t1-image2.png)

6. Click **Skip**.
7. You should now have a new team named **Green**.

![A screenshot of the microsoft teams page with your new team named green now under your teams](03-1/Media/ex1-t1-image3.png)

8. Do not navigate away from this page.

#### Task 2: Install Power Apps
In this task you will install Power Apps for Teams.

1.  Click on the **... More added apps**, search for power apps and select **Power Apps**.

![A Screenshot with an arrow pointing to the ellipsis icon for more added apps on the left side of the page and a box around power apps button](03-1/Media/ex1-t2-image1.png)

2.  Click **Add**.

3.  Right click on the Power Apps tab and select  **Pin**.

![A Screenshot with an arrow pointing to the power apps icon and a box around the pin button](03-1/Media/ex1-t2-image2.png)


### Exercise 2: Create application
In this exercise, you will provision Dataverse for Teams by creating an application and you will also create a Dataverse table with columns.

#### Task 1: Create application
In this task, you will provision Dataverse for Teams by creating an application.
1. Navigate to [Microsoft Teams](https://teams.microsoft.com).

2. Select Power Apps and click **Start now**.

![A screenshot of the power apps home page](03-1/Media/ex2-t1-image1.png)

3. Select the **Green** team you created and click **Create**.
4. Enter **Upcycle** for App name and click **Save**.
5. Do not navigate away from this page.

#### Task 2: Create table
In this task, you will create a table and columns.

1. Click **With data** and select **+ Create new table**.

![A Screenshot with an arrow pointing to the with data option and a box around the create new table button from the select a data source prompt](03-1/Media/ex2-t2-image2.png)

2. Enter **Gadget** for Table name and click **Create**.
3. Click **+ Add column**.
4. Enter **Description** for Name select **Text** for Type, and click to expand the **Advanced options** section.

![A Screenshot with an arrow pointing to the advanced options button](03-1/Media/ex2-t2-image3.png)

5. Change the **Max length** to **500** and click **Create**.
6. Click **+ Add column** again.
7. Enter **Availability** for Name, select **Choice** for Type, enter **Available** for the first choice and click **+ New choice**.

![A Screenshot with an arrow pointing to the new choice button](03-1/Media/ex2-t2-image4.png)

8.  Enter **Reserved** for the second choice and click **+ New choice**.
9.  Enter **Picked up** for the third choice and click **Create**.
10.  Your table screen should now look like the image below.
     ![A Screenshot with an arrow pointing to the word saved in the right hand corner of the window](03-1/Media/ex2-t2-image5.png)
11.  Close the table editor by clicking on the **Close** button.
12.  Do not navigate away from this page.


#### Task 3: Add columns
In this task, you will add new columns to the table.

1. Select the **Home** tab and click **See more**.

![A screenshot of a box around the home button and an arrow pointing to the see more button in the recent apps window of the home page of power apps](03-1/Media/ex2-t3-image1.png)

2. Click to open the **Gadget** table.
3. Click  **+ Add column** column.
4. Enter **Location** for Display name, select **Text** for Data type, make the column **Required** and click **Done**.

![A screenshot of the add column window with the relevant text in each field](03-1/Media/ex2-t3-image.png)

5. Click **+ Add column**.
6. Enter **Photo** for Display name, select **Image** for Data type, check the **Primary image** checkbox and click **Done**.

![A screenshot of the add column window with the relevant text in each field](03-1/Media/ex2-t3-image3.png)

7.  Click **+ Add column**.
8.  Enter **Reserved by** for Display name, select **Lookup** for Data type, select **User** for Related table and click **Done**.

![A screenshot of the add column window with the relevant text in each field](03-1/Media/ex2-t3-image4.png)

9.  Select the **Availability** column.
10. Select **Available** for Default value and click **Done**

![A screenshot with a box around available selected as the default value option](03-1/Media/ex2-t3-image5.png)

11. Click the **Save table** button located on the bottom right of the screen.
12. Do not navigate away from this page.


#### Task 4: Edit the application
In this task, you will edit the application by filters for gadgets that are available and edit the form.

1. Select the **Home** tab and click to open the **Upcycle** application you created.
2. Select **Screen1**. If the screen already contains the form, move to the next step, otherwise click **With data** and select **Gadgets** table under **Current environment**. That will create the screen elements including the form.
3. Make sure **RightContainer1** is expanded and select the **EditForm1** control from tree view.

![A screenshot with a border around the edit form button under screen 1](03-1/Media/ex2-t4-image1.png)

3. Go to the **Properties** pane and click **Edit fields**

![A Screenshot with an arrow pointing to the edit fields button](03-1/Media/ex2-t4-image2.png)

4. Click on the **+ Add field** button.
5. Select the fields that does not exist on the EditForm control from the below list and click **Add**.
   1. **Name**
   2. **Description**
   3. **Availability**
   4. **Location**
   5. **Reserved by**
   6. **Photo**

![A screenshot of the add field window](03-1/Media/ex2-t4-image3.png)

6. Remove any extra fields and close the **Fields** pane. Your form should only have **Name, Description, Availability, Location, Reserved By and Photo** columns.
7. Change **Columns** for Snap to columns to **1**.

![A screenshot with a border around the columns field and the value of 1 in the field itself](03-1/Media/ex2-t4-image4.png)

8. Select the **Photo** inside the canvas and change **Width** to **400**.

![A screenshot of the photo selected inside the canvas and a border around the size field changed to 400 in the properties pane](03-1/Media/ex2-t4-image5.png)

9.  Expand the form and select the **Reserved by** data card.

![A screenshot of a border around reserved by data card selected under edit form 1](03-1/Media/ex2-t4-image5_1.png)

10.  Go to the **Properties** pane, select the **Advanced** tab and click **Unlock**.

![A Screenshot with an arrow pointing to the lock icon under the advanced tab](03-1/Media/ex2-t4-image5_2.png)

11.   Search for display and change the **DisplayMode** value to **DisplayMode.View**.

![A screenshot with a border around the display mode field](03-1/Media/ex2-t4-image5_3.png)

12.  Select the **Browse gallery**.
13. Select **Items** form the formula bar and replace the value with formula below. This formula will filter the gadgets to show only the available gadgets

    ```Filter(Gadgets, Availability <> 'Availability (Gadgets)'.'Picked up')```

![Filter data - screenshot](03-1/Media/ex2-t4-image6.png)

14.  Select the **Image** inside the gallery.

![A Screenshot with an arrow pointing to image 1 inside the gallery](03-1/Media/ex2-t4-image7.png)

15.  Go to the formula bar and change the value of the Image to the formula below.

```ThisItem.Photo```

![A screenshot of the relevant command put into the formula bar](03-1/Media/ex2-t4-image8.png)

16.   Select the **Data** tab, click on the **...More actions** button of the **Gadgets** table and select **Refresh**.

![A Screenshot with an arrow pointing to the ellipsis icon for more actions and a border around the refresh button](03-1/Media/ex2-t4-image9.png)

17.  Click **Save** and wait for the app to be saved.
18.  Click **Preview**.
19.  Click **+ New record**.

![A screenshot of a border around the new record button](03-1/Media/ex2-t4-image10.png)

20.  Fill out the form and click **Tap or click to add a picture**.

![A Screenshot with an arrow pointing to the tap or click to add a picture button](03-1/Media/ex2-t4-image11.png)

21.  Provide your own photo or select one from the lab resources folder.
22.  Click **Save**.

![A Screenshot with an arrow pointing to the tick icon to save](03-1/Media/ex2-t4-image12.png)

23.  Add few more items.
24.  Your app should now look like the image below. Close the preview.

![A screenshot of the running app with an arrow pointing to the cross icon to close the preview](03-1/Media/ex2-t4-image13.png)

25.  Do not navigate away from this page.


#### Task 5: Update Dataverse rows
In this task, you will add buttons that will let users reserve and/or pick up item, you will also update the rows in Dataverse as reserved or picked up.

1. Select **App** from the Tree view and set the **OnStart** value to the formula below. This formula will create a variable named CurrentUser and set its value to the first user that matches the logged in user's email.

```Set(CurrentUser, First(Filter(Users, 'Primary Email' = User().Email)))```

![A screenshot with a border around app selected in the screens tab on the left and another border around the formula bar with the relevant command typed in](03-1/Media/ex2-t5-image1.png)

2. Select App, select **ellipsis** and select **Run OnStart**.
3. Select the **RightContainer**.

![A screenshot with a border around the RightContainer1 element selected](03-1/Media/ex2-t5-image2.png)

3. Click on the **+** Insert button and select **Button**.

![A Screenshot with an arrow pointing to the plus icon to insert and a border around the button option](03-1/Media/ex2-t5-image3.png)

4. Select the **Tree view**, double click on the button you just added and rename it **Reserve Button**.

![A screenshot with the text "Reserve Button" highlighted as the new name for the button you added](03-1/Media/ex2-t5-image4.png)

5. Set the **Text** value of the Reserve Button to **Reserve**.
6. Move the Reserve Button and place it next to the Image.

![A screenshot of the Reserve button selected and moved next to the image on the right hand side](03-1/Media/ex2-t5-image5.png)

7. Set the **DisplayMode** value of the Reserve Button to the formula below. This formula will disable the button if the selected item is not available.

```If(BrowseGallery1.Selected.Availability = 'Availability (Gadgets)'.Available, DisplayMode.Edit, DisplayMode.Disabled)```

8. Set the **OnSelect** value of the Reserve Button to the formula below. This formula will update the selected record by setting the reserved by value to the current user and the availability value to reserved.

```Patch(Gadgets, BrowseGallery1.Selected, {Availability: 'Availability (Gadgets)'.Reserved, 'Reserved by': CurrentUser})```

9. Set the **Visible** value of the Reserve Button to the formula below. This formula will hide the button if the user is creating a new record.

```If(EditForm1.Mode = FormMode.View, true, false)```

10. Select the **RightContainer** again.
11. Click on the **+** Insert button and select **Button** again.
12. Select the **Tree view**, double click on the button you just added and rename it **Picked Up Button**.

![A screenshot with the text "Picked Up Button" highlighted as the name new for button you added](03-1/Media/ex2-t5-image6.png)

12. Set the **Text** value of the Reserve Button to **Picked up**.
13. Adjust the width and move the Picked Up Button and place it to the right of the Reserve Button.

![A screenshot showing the Picked Up button selected and moved to the right of the Reserve button](03-1/Media/ex2-t5-image7.png)

14. Set the **DisplayMode** value of the Picked Up Button to the formula below. This formula will disable the button if the selected item is reserved and the reserved by user is not the current user.

 ```If(BrowseGallery1.Selected.Availability = 'Availability (Gadgets)'.Reserved And BrowseGallery1.Selected.'Reserved by'.'Primary Email' <> CurrentUser.'Primary Email', DisplayMode.Disabled, DisplayMode.Edit)```

15. Set the **OnSelect** value of the Picked Up Button to the formula below. This formula will update the selected record by setting the reserved by value to the current user and the availability value to picked up. The second formula will select the first item of the gallery.

```Patch(Gadgets, BrowseGallery1.Selected, {Availability: 'Availability (Gadgets)'.'Picked up', 'Reserved by': CurrentUser});Select(BrowseGallery1,1)```

16. Set the **Visible** value of the Picked Up Button to the formula below. This formula will hide the button if the user is creating a new record.

```If(EditForm1.Mode = FormMode.View, true, false)```

 17. Click **Save** to save your changes.
 18. Do not navigate away from this page.


#### Task 6: Add search
In this task, you will add search capability to your application.

1. Select the **RightContainer**.
2. Click on the **+** Insert menu and select **+ Add icon**.
3. Place the icon above the form.

![A screenshot of the plus icon selected](03-1/Media/ex2-t6-image1.png)

4. Select the icon, go to the **Properties** and select **Search** for Icon.

![A screenshot with a border around the Search option selected as the icon](03-1/Media/ex2-t6-image2.png)

5. Click on the **+** Insert menu and select **Text box**.
6. Select the **Tree view**.
7. Select the text box you just added and rename it **Search box**.

![A screenshot of the words "Search Box" highlighted as the new name for the text box you added](03-1/Media/ex2-t6-image3.png)

8. Place the Search Box to the right of the icon.

![A screenshot of the Search Box placed to the right of the icon](03-1/Media/ex2-t6-image4.png)

9.  Select the **Search Box** and set **OnChange** value to the formula below. This formula will reset the gallery.

```Reset(BrowseGallery1)```

10. Select the **BrowseGallery** and change the **Items** formula to the formula below. The formula is incomplete, we will complete it in the next step.

```Filter(Search(Gadgets, 'Search Box'.Value, ), Availability <> 'Availability (Gadgets)'.'Picked up')```

11. Place your cursor after **'Search Box'.Value** and type name. You should see a suggestion with crxxx_name, select the suggested column.

![A screenshot with a border around the words "crefe4_name"](03-1/Media/ex2-t6-image5.png)

12. Add comma after the name column you just selected and type **description** and select the suggested column again.

![A screenshot with a border around the worlds "crfe4_description"](03-1/Media/ex2-t6-image6.png)

13. Your formula should now look like the image below. This formula will search the name and description columns of the gadgets table for whatever the user types in the text box and filter out the picked up items.

![Suggested description column - screenshot](03-1/Media/ex2-t6-image7.png)

14.  Select the **Search Box**.
15.  Go to the formula bar and remove the **Value** text.

![A screenshot with a border around the formula bar](03-1/Media/ex2-t6-image8.png)

16.  Click **Save** to save your changes.

### Exercise 3: Test and publish application
In this exercise, you will test, publish and give colleagues permission to use the application.

#### Task 1: Test application
In this task, you will test the application.

1. Click on the **Preview** button.

![A screenshot with an arrow pointing to the Preview button](03-1/Media/ex3-t1-image1.png)

2. The **Reserve** and **Picked up** button should be visible and enabled.
3. Search for cable. The gallery should show items that have the text **cable** in the name or description column.

![A screenshot with the word cable in the search bar and a gallery showing items that have the text cable in their name or description column on the left side of the window](03-1/Media/ex3-t1-image2.png)

4. Select one of the items, the **Reserved by** column value should be empty.
5. Click on the **Reserve** button.

![A screenshot of a border around the Reserved by field and an arrow pointing to the Reserve button](03-1/Media/ex3-t1-image3.png)

6. The **Reserve** button should become disabled and the **reserved by** value will be set to your username. Click on the **Picked up** button.

![A screenshot with a border around the reserved by field with your username and another border around the now-disabled reserve button](03-1/Media/ex3-t1-image4.png)

7. The item should no longer show up on the gallery and the first item of the gallery should get selected.
8. Close the preview.
9. Do not navigate away from this page.


#### Task 2: Publish application
In this task, you will publish the application to Teams.

1. Click on the **Publish to Teams** button.

![A Screenshot with an arrow pointing to the publish to teams button](03-1/Media/ex3-t2-image1.png)

2. Click **Next**.
3. Click **+** add app as a tab.

![A Screenshot with an arrow pointing to the plus icon for add app as a tab in the general box](03-1/Media/ex3-t2-image2.png)

4. Click **Save and close**
5. Select **Teams** and select the new **Upcycle** tab.

![A Screenshot with an arrow pointing to the upcycle button](03-1/Media/ex3-t2-image3.png)

6. The app should load. If the app is not loaded, refresh the page.

![A screenshot of the loaded app](03-1/Media/ex3-t2-image4.png)

7. Test the application in Teams and make sure it behaves as you expected.


#### Task 3: Give permissions
In this task, you will give your colleagues permission to create new items, edit items they created, delete items they created and read items created by other people.

1. Select **Power Apps** and click on the **See more** link.

![A screenshot with a border around the power apps button on the left side of the window and an arrow pointing to the see more link in the recent apps](03-1/Media/ex3-t3-image1.png)

2. Click to open the **Gadget** table.
3. Click **Manage permissions**.

![A Screenshot with an arrow pointing to the manage permissions button](03-1/Media/ex3-t3-image2.png)

4. Select **Members**, select **Collaborate** permission and click **Save**

![A screenshot of the collaborate permission selected](03-1/Media/ex3-t3-image3.png)

5. You may test the application with another user and see how it behaves.

