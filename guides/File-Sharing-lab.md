# File Sharing Lab with Workplace Scenarios on Windows Server VM

## Granting Read-Only Access to a Shared Folder
### Scenario:
A Marketing Intern needs access to the Marketing Team’s shared folder
(\Server Name\Marketing) to view content but should not modify or delete files.


### 1. Modify Share Permissions

1. in File Explorer, Right-click Marketing Folder -> Properties -> Sharing tab -> Advanced Sharing
![Grant Read-Only Access](../docs/screenshots/grant-r-access.png)

2. Set Share Permissions:
    - MarketingTeam -> Full Control
    ![Grant Read-Only Access](../docs/screenshots/grant-r-access-2.png)

    - MarketingInterns -> Read
    ![Grant Read-Only Access](../docs/screenshots/grant-r-access-3.png)

### 2. Modify NTFS Permissions

1. Properties -> Security tab -> Edit
![Grant Read-Only Access](../docs/screenshots/grant-r-access-4.png)

2. Add MarketingInterns -> Set only Read permissions
![Grant Read-Only Access](../docs/screenshots/grant-r-access-5.png)
![Grant Read-Only Access](../docs/screenshots/grant-r-access-6.png)

### 3. Test Access

1. Log in as a Marketing Intern and try to open a file (It Should work)
2. Try to edit or delete a file (Should be denied)


## Creating a Private Department Folder
### Scenario:
The HR Department needs a secure folder (\Server\HR) that only HR staff can
access. Other employees should not see the folder at all.


### 1. Modify Share Permissions
1. Remove Everyone
![Create Private Folder](../docs/screenshots/create-private-folder.png)
2. Add HRGroup -> Set Full Control
![Create Private Folder](../docs/screenshots/create-private-folder-2.png)
![Create Private Folder](../docs/screenshots/create-private-folder-3.png)

### 2. Modify NTFS Permissions

1. Add HRGroup -> Set Full Control
![Create Private Folder](../docs/screenshots/create-private-folder-4.png)
![Create Private Folder](../docs/screenshots/create-private-folder-5.png)

### 3. Test Access

1. Log in as an HR employee and open the folder (It Should Work)
2. Log in as a non-HR employee and try to access \\Server\HR (It Should Be Denied)


## Temporary File Access for a Vendor
### Scenario:
A third-party vendor needs access to a temporary folder (\Server\VendorFiles) to
upload reports but should not see other files.


### 1. Create a VendorFiles Folder
1. C:\Shared\VendorFiles
![Temp File Access](../docs/screenshots/temp-file-access.png)

### 2. Set Share Permissions
1. Add VendorUser -> Set Full Control
![Temp File Access](../docs/screenshots/temp-file-access-2.png)
![Temp File Access](../docs/screenshots/temp-file-access-3.png)
![Temp File Access](../docs/screenshots/temp-file-access-4.png)

### 3. Set NTFS Permissions
1. Add VendorUser -> Set Modify (but Uncheck Delete)
![Temp File Access](../docs/screenshots/temp-file-access-5.png)
![Temp File Access](../docs/screenshots/temp-file-access-6.png)
![Temp File Access](../docs/screenshots/temp-file-access-7.png)

### 4. Test Access
1. Log in as VendorUser, upload a file (It Should Work)
2. Try deleting an existing file (Should be denied)

## Restricting Access to Specific Files Inside a Shared Folder
### Scenario:
In the IT Department, all techs need access to the Software Repository
(\Server\Software), but only senior IT staff should be able to access the "Licenses" subfolder.

### 1. Set Folder Permissions for \\Server\Software
1. ITStaff -> Modify (can add and edit files)
![Restrict Access to Specific File](../docs/screenshots/Restrict-Specific-file-In-Shared-Folder.png)
![Restrict Access to Specific File](../docs/screenshots/Restrict-Specific-file-In-Shared-Folder-2.png)
![Restrict Access to Specific File](../docs/screenshots/Restrict-Specific-file-In-Shared-Folder-3.png)

### 2. Set NTFS Permissions for \\Server\Software\Licenses
1. Remove inherited Permissions
![Restrict Access to Specific File](../docs/screenshots/Restrict-Specific-file-In-Shared-Folder-4.png)
![Restrict Access to Specific File](../docs/screenshots/Restrict-Specific-file-In-Shared-Folder-5.png)

2. Add SeniorIT -> Full Control
![Restrict Access to Specific File](../docs/screenshots/Restrict-Specific-file-In-Shared-Folder-6.png)
![Restrict Access to Specific File](../docs/screenshots/Restrict-Specific-file-In-Shared-Folder-7.png)
![Restrict Access to Specific File](../docs/screenshots/Restrict-Specific-file-In-Shared-Folder-8.png)


### 3. Test Access
1. Log in as a junior IT tech and open \\Server\Software (It Should Work)
2. Try accessing Licenses subfolder (Should be denied)
