# Section1.1
##Drive

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

