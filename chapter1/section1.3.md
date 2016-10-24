# Section1.3 Thumbnail 图片

- GET `http://{domain_name}/{rest_context_name}/private/thumbnailImage/{small|medium|big|large}/{repoName}/{workspaceName}/{nodePath:.*}/`

- GET `http://{domain_name}/{rest_context_name}/private/thumbnailImage/custom/{size}/{repoName}/{workspaceName}/{nodePath:.*}/`



**示例**：
`http://localhost:8080/rest/private/thumbnailImage/origin/repository/collaboration/Groups/spaces/space0/Documents/folder1/4b90f603738da977c76fb500b351f8198618e35d.jpg`

小图：32*32
`http://localhost:8080/rest/private/thumbnailImage/small/repository/collaboration/Groups/spaces/space0/Documents/folder1/4b90f603738da977c76fb500b351f8198618e35d.jpg`

中图：64*64
`http://localhost:8080/rest/private/thumbnailImage/medium/repository/collaboration/Groups/spaces/space0/Documents/folder1/4b90f603738da977c76fb500b351f8198618e35d.jpg`

大图：300*300
`http://localhost:8080/rest/private/thumbnailImage/big/repository/collaboration/Groups/spaces/space0/Documents/folder1/4b90f603738da977c76fb500b351f8198618e35d.jpg`

特大图：300*300
`http://localhost:8080/rest/private/thumbnailImage/large/repository/collaboration/Groups/spaces/space0/Documents/folder1/4b90f603738da977c76fb500b351f8198618e35d.jpg`

原图：
`http://localhost:8080/rest/private/thumbnailImage/origin/repository/collaboration/Groups/spaces/space0/Documents/folder1/4b90f603738da977c76fb500b351f8198618e35d.jpg`

用户设定大小
`http://localhost:8080/rest/private/thumbnailImage/custom/1024x1024/repository/collaboration/Groups/spaces/space1/Documents/image/Cg-4V1GHI2eIRDh6AAVUy4aA1VMAAIRaQNmg2IABVTj855.jpg`

**这个custom/{size} 的参数真心非常坑，两个数字之间是x **