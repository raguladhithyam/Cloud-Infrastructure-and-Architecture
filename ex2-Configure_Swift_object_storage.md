# Exercise 2: Configure Swift Object Storage

## Aim
To configure Swift Object Storage in OpenStack.

## Procedure

### Create and Manage Object Containers
OpenStack Object Storage (Swift) provides redundant, scalable data storage using clusters of servers. It is ideal for storing large amounts of static data that can be retrieved and updated, such as VM images, backups, archives, or media files. Swift offers a distributed, API-accessible platform that can be directly integrated into applications. In the OpenStack dashboard, containers are used to manage storage for objects similar to folders in operating systems.

### Steps

#### 1. Create a Container
1. Log in to the OpenStack dashboard.
2. Select the appropriate project from the dropdown menu at the top left.
3. Go to `Project > Object Store > Containers`.
4. Click on `Container`.
5. In the **Create Container** dialog box, enter a name for the container, and click **Create**.

> **Note:** To delete a container, click the **More** button and select **Delete Container**.

#### 2. Upload an Object
1. Log in to the OpenStack dashboard.
2. Select the appropriate project from the dropdown menu.
3. Go to `Project > Object Store > Containers`.
4. Select the container where you want to store your object.
5. Click the **Upload File** icon.
6. In the **Upload File To Container: <name>** dialog box, enter a name for the object.
7. Browse to select the file you want to upload and click **Upload File**.

> **Note:** To delete an object, click the **More** button and select **Delete Object**.

---

### Manage an Object

#### Edit an Object
1. Log in to the OpenStack dashboard.
2. Select the appropriate project from the dropdown menu.
3. Go to `Project > Object Store > Containers`.
4. Select the container holding your object.
5. Click the **Menu** button and choose **Edit** from the dropdown list.
6. In the **Edit Object** dialog box, browse to select the file you want to upload.
7. Click **Update Object**.

> **Note:** To delete an object, click the **Menu** button and select **Delete Object**.

#### Copy an Object from One Container to Another
1. Log in to the OpenStack dashboard.
2. Select the appropriate project from the dropdown menu.
3. Go to `Project > Object Store > Containers`.
4. Select the container with the object you want to copy.
5. Click the **Menu** button and choose **Copy** from the dropdown list.
6. In the **Copy Object** dialog box, provide:
   - **Destination Container**: Choose the destination container.
   - **Path**: Specify a path for the new copy within the destination container.
   - **Destination Object Name**: Enter a name for the copied object.
7. Click **Copy Object**.

---

#### Create a Metadata-Only Object (Placeholder)
This option allows you to create an object without a file, which can be uploaded later when ready. This placeholder allows metadata and URL sharing in advance.

1. Log in to the OpenStack dashboard.
2. Select the appropriate project from the dropdown menu.
3. Go to `Project > Object Store > Containers`.
4. Select the container for the placeholder object.
5. Click **Upload Object**.
6. In the **Upload Object To Container: <name>** dialog box, enter a name for the object.
7. Click **Update Object**.

#### Create a Pseudo-Folder
Pseudo-folders organize objects using a common prefix in their names, similar to folders in an operating system.

1. Log in to the OpenStack dashboard.
2. Select the appropriate project from the dropdown menu.
3. Go to `Project > Object Store > Containers`.
4. Select the container where you want to create a pseudo-folder.
5. Click **Create Pseudo-folder**.
6. In the **Create Pseudo-Folder in Container <name>** dialog box, enter a name for the pseudo-folder (use `/` as a delimiter for subdirectories).
7. Click **Create**.
