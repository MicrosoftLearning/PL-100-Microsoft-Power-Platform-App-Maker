---
lab:
    title: 'Lab 08.1: Test & deploy'
    module: 'Module 08: Get started with AI Builder'
---

# Lab 08.1: Test & deploy

In this lab you will complete solution configuration by adding security roles for the users. Then you will verify, test, and deploy the solution in the production environment.

## What you will learn

  - How to deploy a solution to another environment

## High-level lab steps

-   Exercise 1 – Export and import solution

-   Exercise 2 – Create security roles for users

    -   Company 311 User – read all on Building, user owned on Problem Reports

    -   Company 311 Admin – All access for Buildings, Departments, Problem
        Reports

    -   Associate Company 311 Admin role with model-driven app


## Prerequisites

Must have completed the following labs:

-   02.1: Data model

-   02.2: Work with forms and views

-   02.3: Compose a model-driven app

-   02.4: Import data

## Detailed steps

### Exercise 1: Import export

In this exercise, you will export the company 311 solution and import it into a new environment.

#### Task 1: Export solution

1.  Navigate to the `https://make.powerapps.com` 
    and make sure you are in the correct environment.

2.  Select **Solutions**, and open the **Company 311** solution.

3.  Select **+ Add existing**, select **More**, then select **Connection Reference**.

    ![A screenshot of the expanded Add existing menu with add connection reference menu item selected](06/media/Lab6-Ex1-Task1-1.png)

4.  Select all of the connection references and select **Add**.

5.  Select **+ Add existing**, select **More**, then select **Component Library**.

6.  Select the **Shared Components A** connection library and select **Add**.

7.  Select **Publish all customizations** and wait for the publishing to complete.

8.  Navigate back to the **Solutions** list. 

9.  Select the **Company 311** solution and select **Export Solution** from the toolbar.

    ![A Screenshot with cursor pointing to the Export Solution button](06/media/Lab6-Ex1-Task1-2.png) 

10. Select **Next**.

11. Select **Managed** and select **Export**. Wait for the solution to be packaged and exported.

12. When it has exported successfully, select **Download** to save the solution to your computer. 

13. Select **Export solution** again. 

14. Select **Next**. 

15. Select **Unmanaged**, change the **version** to match the managed solution version and select **Export**. 

16. You should have the **Managed** and **Unmanaged** versions of the solution exported and downloaded.


#### Task 2: Create new environment and import solution

1.  Navigate to the Power Platform admin center, `https://aka.ms/ppac`

2.  Using the navigation on the left, select **Environments**.

3.  Select **New**.

4.  Name the New Environment `Prod`

5.  Set the **Type** to **Developer**.

6.  Select **Next**.

7.  Select **Save**. 

8.  Navigate to the Power Apps maker portal `https://make.powerapps.com` 
    and select the environment you just created.

9.  Select **Solutions** and select **Import solution**.

10. Select **Browse**.

11. Select the managed solution you exported and select **Open**.

12. Select **Next**. 

13. Select **Next** again. 

14. Select **Select connection** for outlook and then select **+ New connection**.

    ![A Screenshot with an arrow pointing to the drop down icon and a border around the plus new connection button](06/media/Lab6-Ex1-Task2-2.png)

15. It will open a new window. Select **Create**.

16. Provide your **credentials**.

17. **Close** the connections browser window or tab.

18. Select **Refresh**.

19. Repeat steps 12 - 16 for the rest of the of the connections.

20. Select **Import** and wait for the import to complete.

21. Select **Publish all customizations** and wait for the publishing to complete.

22. Open the **Company 311** solution you just imported.

23. Review the components in solution.

24. Select **Apps** and make sure you have both the Canvas and Model-driven apps.

25. Open the **Company 311 Admin** application.

26. The application should load without issues.

27. Close the Company 311 Admin application browser window or tab.

28. Open the **Company 311 Phone** application.

29. The application should load without issues.

30. Close the **Company 311 Phone App** browser window or tab.


### Exercise 2: Create security roles

In this exercise, you will create security roles for users.

#### Task 1: Create security roles

1.  Navigate to the Power Apps maker portal, `https://make.powerapps.com` 
    and make sure you are in the correct environment. 

2.  Select **Solutions** and open the **Company 311** solution.

3.  Select **+ New \> Security** and select **Security Role**.

4.  Enter **Company 311 User** for **Role Name** and select the **Custom
    Entities** tab.

5.  Set the read privilege of the **Building** table to **Organization**.

6.  Set the read privilege of the **Problem Report** table to **User**.

7.  The read privileges for the **Building** and **Problem Report** Tables
    should now look like the image below. Select **Save Create New**.

    ![A Screenshot with an arrow pointing to the save create new icon in the topmost part of the window and borders around the building and problem report on the list of custom entities](06/media/Lab6-Ex2-Task1-1.png)

8.  Enter **Company 311 Admin** for **Role Name** and select the **Custom
    Entities** tab.

9.  Set all privileges of the **Building**, **Department**, and **Problem
    Reports** tables to **Organization**.

    ![A screenshot of building, department, and problem report having all privileges selected in the custom entities tab](06/media/Lab6-Ex2-Task1-2.png)

10. Select the **Customization** tab.

11. Set all privileges for **Model-driven app**.

    ![A screenshot of the security role edit dialog with all privileges selected for Model Driven app table](06/media/Lab6-Ex2-Task1-3.png)

12. Select **Save and Close**.

13. Select **Done** on the pop-up.

14. Select **All** from the **Objects** pane.

15. Select **Publish all customizations** and wait for the publishing to
    complete.

