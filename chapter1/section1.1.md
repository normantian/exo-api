# Section1.1 Drivers

* **Returns a list of drives for the current user.返回当前用户有权限的驱动列表**

GET `http://{domain_name}/{rest_context_name}/private/wcmDriver/getDrivers/`

参数：

param | description | required
------------ | ------------- | ------------
lang | The language of the drive name  | true

示例：
	`http://localhost:8080/rest/private/wcmDriver/getDrivers?lang=zh_CN`
    
	
结果样例：

	<?xml version="1.0" encoding="UTF-8"?>
	<Connector isUpload="false">
    <Folders isUpload="false" name="General Drives"/>
    <Folders isUpload="false" name="Group Drives">
        <Folder folderType="exo:drive" hasFolderChild="false" isUpload="true" label=".platform.users" name=".platform.users" nodeTypeCssClass="uiIcon16x16FolderDefault uiIcon16x16nt_unstructured" path="/Groups/platform/users/Documents" repository="repository" url="/portal/rest/jcr/repository/collaboration/Groups/platform/users/Documents" workspace="collaboration"/>
        <Folder folderType="exo:drive" hasFolderChild="false" isUpload="true" label=".spaces.space0" name=".spaces.space0" nodeTypeCssClass="uiIcon16x16FolderDefault uiIcon16x16nt_unstructured" path="/Groups/spaces/space0/Documents" repository="repository" url="/portal/rest/jcr/repository/collaboration/Groups/spaces/space0/Documents" workspace="collaboration"/>
        <Folder folderType="exo:drive" hasFolderChild="false" isUpload="true" label=".spaces.space1" name=".spaces.space1" nodeTypeCssClass="uiIcon16x16FolderDefault uiIcon16x16nt_unstructured" path="/Groups/spaces/space1/Documents" repository="repository" url="/portal/rest/jcr/repository/collaboration/Groups/spaces/space1/Documents" workspace="collaboration"/>
    </Folders>
    <Folders isUpload="false" name="Personal Drives">
        <Folder folderType="exo:drive" hasFolderChild="true" isUpload="true" label="Personal Documents" name="Personal Documents" nodeTypeCssClass="uiIcon16x16FolderDefault uiIcon16x16exo_privateFolder" path="/Users/u___/us___/use___/user1/Private" repository="repository" url="/portal/rest/jcr/repository/collaboration/Users/u___/us___/use___/user1/Private" workspace="collaboration"/>
    </Folders>
	</Connector>

---

* **Returns all folders and files in a given location. 返回一个位置的所有文件和文件夹**

GET `http://{domain_name}/{rest_context_name}/private/wcmDriver/getFoldersAndFiles/`
 
参数：

 param | description | required
------------ | ------------- | ------------
**driverName** | the driver name.  | true
**currentFolder** | the current folder. | true
currentPortal | the current portal. | false
repositoryName | the repository name. | false
workspaceName | The workspace name. | false
filterBy | the type of filter. etc. "All", "Medias", "Image"| false
type | |


示例：
`http://localhost:8080/rest/private/wcmDriver/getFoldersAndFiles?repositoryName=repository&currentFolder=image/filterBy=All&currentPortal=intranet&workspaceName=collaboration&driverName=.alibaba`

或者 

`http://localhost:8080/rest/wcmDriver/getFoldersAndFiles?currentFolder=&filterBy=All&driverName=.spaces.space1`

结果xml样例：

    <?xml version="1.0" encoding="UTF-8"?>
    <Connector command="" resourceType="Node">
    <CurrentFolder folderType="nt:unstructured" isUpload="true" name="Documents" path="/Groups/alibaba/Documents/" url="/portal/rest/jcr/repository/collaboration/Groups/alibaba/Documents"/>
    <Folders isUpload="true">
        <Folder folderType="nt:folder" hasFolderChild="true" isUpload="true" name="doc" nodeDriveName=".alibaba" nodeTypeCssClass="uiIcon16x16FolderDefault uiIcon16x16nt_folder" path="/Groups/alibaba/Documents/doc" title="doc" url="/portal/rest/jcr/repository/collaboration/Groups/alibaba/Documents/doc"/>
        <Folder folderType="nt:folder" hasFolderChild="true" isUpload="true" name="image" nodeDriveName=".alibaba" nodeTypeCssClass="uiIcon16x16FolderDefault uiIcon16x16nt_folder" path="/Groups/alibaba/Documents/image" title="image" url="/portal/rest/jcr/repository/collaboration/Groups/alibaba/Documents/image"/>
    </Folders>
    <Files isUpload="true">
        <File creator="root" dateCreated="9/28/16 6:00 PM" dateModified="9/28/16 6:00 PM" isVersionSupport="true" isVersioned="true" linkTarget="/Groups/alibaba/Documents/2143_1.jpg" name="2143_1.jpg" nodeType="image/jpeg" path="/Groups/alibaba/Documents/2143_1.jpg" size="102" url="/portal/rest/jcr/repository/collaboration/Groups/alibaba/Documents/2143_1.jpg"/>
    </Files>
    </Connector>

---

* **Checks if the drive can upload a new file. 检查drive是否可以上传一个新的文件**

示例：
`http://localhost:8080/rest/private/wcmDriver/uploadFile/checkUploadAvailable/`

参数： 无

结果xml：

    <?xml version="1.0" encoding="UTF-8"?>
    <uploadAvailable/>

---

* ** 上传文件前查看文件是否存在 **

GET `http://{domain_name}/{rest_context_name}/private/wcmDriver/uploadFile/checkExistence/`

参数：

 param | description | required
------------ | ------------- | ------------
repositoryName | The repository name.  | true
workspaceName | The workspace name. | true
driverName | The drive name. | true
currentFolder | the current folder. | true
currentPortal | the current portal. | true
language | language. | true
fileName | the file name. | true

示例：

`
http://localhost:8080/rest/private/wcmDriver/uploadFile/checkExistence?language=zh_CN&currentPortal=intranet&repositoryName=repository&workspaceName=collaboration&driverName=.spaces.space1&currentFolder=/image&fileName=Cg-4V1GHI2eIRDh6AAVUy4aA1VMAAIRaQNmg2IABVTj855.jpg`

结果样例：
    
    //存在
    <?xml version="1.0" encoding="UTF-8"?>
    <Existed>
        <Versioned/>
    </Existed>
    
    //不存在
    <?xml version="1.0" encoding="UTF-8"?>
    <NotExisted/>

---

* ** upload a file 上传文件 **

POST `http://{domain_name}/{rest_context_name}/private/wcmDriver/uploadFile/upload/`

参数：

 param | description | required
------------ | ------------- | ------------
uploadId | The Id of the uploaded file.  | true

---

* ** Controls the process of uploading a file **

GET `http://{domain_name}/{rest_context_name}/private/wcmDriver/uploadFile/control/` 

参数：

 param | description | required
------------ | ------------- | ------------
repositoryName |  The repository name. | true
workspaceName |  The workspace name. | true
driverName |  The driver name. | true
currentFolder |  The current folder. | true
currentPortal |  The current portal. | true
userId | The user identity. | false
jcrPath | the path of the file | false
action | the action | false
language | the language | false
fileName | the file name | false
uploadId | the id of upload | true
existenceAction | checks if an action exists or not | false


示例：
查看上传状态：
`http://localhost:8080/portal/rest/wcmDriver/uploadFile/control?repositoryName=repository&workspaceName=collaboration&driverName=.spaces.space0&currentFolder=/folder1&currentPortal=intranet&userId=root&action=progress&uploadId=1553259954503714`

上传新的版本：
`http://localhost:8080/portal/rest/wcmDriver/uploadFile/control?repositoryName=repository&workspaceName=collaboration&driverName=.spaces.space0&currentFolder=/folder1&currentPortal=intranet&userId=root&uploadId=488953287235556&fileName=8718367adab44aedc0a4903cb51c8701a08bfb04.jpg&language=en&existenceAction=createVersion&action=save`


上传文件流程：

1. 先检查是否存在（/wcmDriver/uploadFile/checkExistence/）
2. 检查是否可以上传文件（/wcmDriver/uploadFile/checkUploadAvailable/）
3. 用uploadid去查上传状态，如果percent=0,则未上传（/wcmDriver/uploadFile/control/   **action=progress**）
4. 上传（/wcmDriver/uploadFile/upload   通过表单上传）
5. 真正的上传（/wcmDriver/uploadFile/control/  **action=save**）  **注意：这时候才是真正去上传文件**

---

* **Clean file name 去除文件名乱码**

GET `http://{domain_name}/{rest_context_name}/private/wcmDriver/uploadFile/cleanName`

参数：

 param | description | required
------------ | ------------- | ------------
fileName |  original file name. | true

示例：

`http://localhost:8080/rest/private/wcmDriver/uploadFile/cleanName?fileName=Cg-4V1GH田飞I2eIRDh6AAVUy4aA1VMAAIRaQNmg2IABVTj855.jpg`

结果样例：

    <name>
        Cg-4V1GH tian feiI2eIRDh6AAVUy4aA1VMAAIRaQNmg2IABVTj855.jpg
    </name>
    
---
* **return to brower a stream got from jcr:content/jcr:data for downloading the content of the node.**
`http://localhost:8080/rest/private/contents/download/collaboration/Groups/spaces/space0/Documents/folder1/4b90f603738da977c76fb500b351f8198618e35d.jpg?version=2`


