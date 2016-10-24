# Section2.1 检索api

* **Search for a query 查询**

GET `http://{domain_name}/{rest_context_name}/private/search/`

参数：

param | description | required
------------ | ------------- | ------------
q | Searches for a query which is entered by the user.  | true
sites | Searches in the specified sites only (for example, ACME or Intranet). | true
types | Searches for these specified content types only (for example, people, discussions, events, tasks, wikis, spaces, files, and documents). | false
offset | Starts the offset of the result set | false
limit | limit the max size fo the result set | false
sort | Defines the Sort type (relevancy, date, title). | false
order | Defines the Sort order (ascending, descending). | false

示例：
	`http://localhost:8080/rest/private/search?q=wusong&sites=intranet`

结果样例：

	{
  		"file": [],
  		"task": [],
  		"post": [],
  		"document": [],
  		"wiki": [],
  		"page": [],
  		"event": [],
  		"people": [],
  		"space": [
    		{
      			"url": "http://localhost:8080/portal/g/:spaces:wusong/wusong",
      			"detail": "wusong - 2 Member(s) - Register",
      			"date": 1475131912281,
      			"title": "wusong",
      			"imageUrl": "http://localhost:8080/eXoSkin/skin/images/system/SpaceAvtDefault.png",
      			"excerpt": "&#26080;&#35359;&#35752;&#35770;&#32452;",
      			"relevancy": 6982
    		}
  		]
	}