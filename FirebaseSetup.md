# Firebase Guide

## Firebase Console Setup

Follow these steps in order to allow communication between Firebase and your Android application.

1. Create a project.
2. Click on the hamburger menu in the top-left corner,
    1. Click Database.
    2. Click "Create Database".
    3. Click "Start in Locked Mode".
    4. Click "Enabled".
5. Next to database, click "Cloud Firestore"
    1. Click "Realtime Database"
7. Click Rules
    1. Change the "false" values to "true".
8. Click Publish

Your Firebase database can (almost) now communicate with your Android application.

In order to enable the communication between Firebase and your application, you must link the two together. To do so,

1. Click `Tools > Firebase`.
2. In the new menu, click **Realtime Database**.
3. Click **Save and retrieve data**.
4. <font color=red>Click on **Connect to Firebase** FIRST</font>.
    1. A menu will appear, select **Choose an existing Firebase or Google project**.
    2. Click **Connect to Firebase**.
5. <font color=red>THEN click on **Add the Realtime Database to your app</font>**.
6. Click **Accept Changes**.


Your project is now linked.
