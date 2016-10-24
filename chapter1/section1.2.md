# Section1.2
## Comment

* **Gets all comments for a specific content. 获取一个内容的所有评论**

GET `http://{domain_name}/{rest_context_name}/private/contents/comment/all`

参数：


param | description | required
------------ | ------------- | ------------
jcrPath | The JCR path of the content. | true

   示例：
`http://localhost:8080/rest/private/contents/comment/all?jcrPath=/repository/collaboration/Groups/spaces/space1/Documents/image/Cg-4V1GHI2eIRDh6AAVUy4aA1VMAAIRaQNmg2IABVTj855.jpg`
 
**注意jcrPath必须从repository开始，一直到文件名称结束。格式如下：
	／{repository}/{collaboration}/Groups/{driverName}/Documents/{folder}/	{fileName}
**

结果样例：

	<?xml version="1.0" encoding="UTF-8"?>
	<comments>
    	<comment>
        	<commentor>user0</commentor>
        	<email>user0@example.com</email>
        	<date>Sep 29, 2016 10:00:54 AM</date>
        	<content>&lt;p&gt;user0 test&lt;/p&gt;&#13;</content>
    	</comment>
    	<comment>
        	<commentor>root</commentor>
        	<email>root@gatein.com</email>
        	<date>Sep 29, 2016 9:59:06 AM</date>
        	<content>&lt;p&gt;cools &lt;/p&gt;&#13;</content>
    	</comment>
	</comments>

---
