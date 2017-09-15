---
title: Rebuild the client cache | VSTS & TFS
description: Update the data cache on client computers after certain maintenance operations.
ms.prod: visual-studio-tfs-dev14
ms.technology: vs-devops-wit
ms.assetid: e110852a-ab93-4259-957e-47c2076c20bb
ms.manager: douge
ms.author: kaelli
ms.date: 02/14/2017
---
# Rebuild the client cache

[!INCLUDE [temp](../../_shared/version-header-tfs-only.md)]


>[!NOTE]  
>This topic applies to team project customization for the On-premises XML process model. You can't exercise the **witadmin rebuildcache** command against a VSTS account.   <br/><br/>
>For an overview of what features are supported for all three process models, see [Customize your work tracking experience](../../customize/customize-work.md).  

You can force a rebuild of the cache on each client computer the next time it connects to a team project collection by using the **witadmin rebuildcache** command.  
  
To prevent workspace errors from occurring during version control or build operations in Team Foundation, the data cache on client computers must be updated after certain maintenance operations. After you move, restore, rename, or fail over a data-tier or application-tier server, you must refresh the cache for tracking work items and users must refresh the version control cache on client computers.  
  
> [!IMPORTANT]
> To avoid server performance issues, you should not run this command during normal operating hours.  
  
[!INCLUDE [temp](../../_shared/witadmin-run-tool.md)]  
  
 **Requirements**  
  
-   To use the **witadmin rebuildcache** command, you must be a member of the **Team Foundation Administrators** security group or the **Project Administrators** security group for the project collection that you want to manage. See [Add an administrator](../../../security/set-project-collection-level-permissions.md).  
  
> [!NOTE]  
>  Even if you log on with administrative permissions, you must open an elevated Command Prompt window to perform this function on a server that is running Windows Server 2008. To open an elevated Command Prompt window, choose **Start**, open the shortcut menu for **Command Prompt**, and choose **Run as Administrator**. For more information, see the [Microsoft Web site](http://go.microsoft.com/fwlink/?LinkId=111235).  
  
## Syntax  
  
```  
witadmin rebuildcache /collection:CollectionURL [/noprompt]  
```  
  
#### Parameters  
  
|**Parameter**|**Description**|  
|-------------------|---------------------|  
|**/collection**:`CollectionURL`|Specifies the URI of the team project collection or Visual Studio Team Services (VSTS) account. For example:<br /> **On-premises TFS format:  http**://*ServerName:Port/VirtualDirectoryName/CollectionName*<br /><br /> If no virtual directory is used, then the format for the URI is the following: **http**://*ServerName:Port/CollectionName*.<br /> **VSTS format:  http://** *AccountName*.visualstudio.com.DefaultCollection|  
|**/noprompt**|Disables the prompt for confirmation.|  
|**/?** or **help**|Displays help about the command in the Command Prompt window.|  
  
## Remarks  
 The **witadmin rebuildcache** command invalidates cached data on all clients for a specified team project collection. This causes the cache for each client to be refreshed the next time the client connects to the project collection.  
  
## Example   
 The following command invalidates the metadata cache for all clients that connect to DefaultCollection that is defined on the server that is named AdventureWorksServer. The client caches are updated the next time they connect to the project collection.  
  
```  
witadmin rebuildcache /collection:http://AdventureWorksServer:8080/tfs/DefaultCollection  
```  
  
## Related notes
- [witAdmin: Customize and manage objects for tracking work](witadmin-customize-and-manage-objects-for-tracking-work.md)