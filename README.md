# Azure Enterprise Identity Lab

A portfolio-ready Microsoft Azure and Windows Server lab that demonstrates how to deploy and manage a small enterprise identity environment. This project combines Azure infrastructure, Active Directory Domain Services, DNS, Group Policy, and file share permissions in a realistic corporate-style setup built around the `corp.local` domain.

This repository is designed to showcase hands-on systems administration and identity management skills in a clean, professional format suitable for GitHub, interviews, and resume projects.

## Project Overview

The lab was built to simulate a centralized enterprise identity environment hosted in Microsoft Azure. A Windows Server virtual machine named `DC01` was deployed inside the resource group `RG-EnterpriseLab` and promoted to a domain controller for the `corp.local` domain. From there, the environment was configured with organizational units, user accounts, security groups, Group Policy, DNS validation, and a shared folder with role-based access controls.

The result is a foundational enterprise lab that demonstrates how directory services, security policies, and access management work together in a Windows domain.

## Technologies Used

- Microsoft Azure
- Azure Resource Groups
- Azure Virtual Machines
- Azure Virtual Network
- Azure Network Security Groups
- Windows Server
- Active Directory Domain Services (AD DS)
- DNS
- Group Policy Management
- Active Directory Users and Computers
- SMB File Shares
- NTFS Permissions

## Azure Architecture

The Azure portion of the lab provides the infrastructure required to host the identity environment.

- Resource Group: `RG-EnterpriseLab`
- Virtual Machine: `DC01`
- Domain: `corp.local`
- Core supporting resources:
  - Virtual network
  - Network security group
  - Windows Server domain controller

`DC01` serves as the central identity and management server for the lab. It hosts Active Directory, DNS, Group Policy management, and the shared resource used for access control testing.

## Active Directory Configuration

The server was promoted to a domain controller for the `corp.local` Active Directory domain. Once AD DS was installed and configured, the environment was organized to reflect a simple enterprise structure that separates users and systems by function.

This setup demonstrates:

- Domain deployment and validation
- Active Directory object management
- Administrative delegation through security groups
- Centralized policy enforcement

## Organizational Units

The following organizational units were created to structure the environment:

- `HR`
- `IT`
- `Managers`
- `Servers`
- `Workstations`

Using OUs keeps administrative boundaries organized and allows Group Policy to be applied in a scalable and maintainable way.

## Users and Security Groups

### User Accounts

The lab includes the following sample domain users:

- `HRuser1`
- `Helpdesk1`
- `ITadmin1`
- `Manager1`
- `Manager2`

### Security Groups

The following groups were created to manage access by role:

- `HR_Users`
- `IT_Admins`
- `Management`

This structure reflects a role-based access control model where permissions are granted to groups rather than assigned directly to individual users.

## Group Policy Configuration

A domain-linked Group Policy Object named `Corp Security Policy` was created to enforce password standards across the environment.

Configured password policy settings:

- Minimum password length: `12`
- Complexity requirements: `Enabled`
- Maximum password age: `90 days`
- Minimum password age: `30 days`

This demonstrates centralized security enforcement and practical baseline hardening for an enterprise Windows domain.

## DNS Configuration

DNS was configured and validated on `DC01` as part of the domain services deployment. Proper DNS functionality is essential in Active Directory environments because authentication, domain joins, and service discovery depend on reliable name resolution.

This lab includes DNS console validation to confirm the domain services infrastructure was functioning as expected.

## CompanyData Shared Folder Permissions

A shared folder was created at:

- Local path: `C:\CompanyData`
- Network path: `\\DC01\CompanyData`

Access was assigned using domain security groups:

- `IT_Admins`: `Full Control`
- `Management`: `Change`
- `HR_Users`: `Read`

This portion of the lab demonstrates practical file server administration using both share permissions and role-based access design.

## Documentation

- Setup guide: [docs/setup-guide.md](docs/setup-guide.md)
- Screenshot index: [docs/screenshot-index.md](docs/screenshot-index.md)

## Screenshots

Project screenshots belong in [screenshots](screenshots/) using the final filenames documented in the screenshot index for easy review.

If any screenshot includes sensitive data such as usernames tied to personal identity, internal IP details, or other environment-specific information, it should be blurred or cropped before publishing publicly.

## Skills Demonstrated

- Azure infrastructure deployment
- Windows Server administration
- Active Directory domain setup and management
- OU and user provisioning
- Security group administration
- Group Policy configuration
- DNS validation and troubleshooting
- SMB share creation and permission assignment
- Enterprise access control design
- Technical documentation for portfolio presentation

## Future Improvements

- Add a client workstation and perform a domain join
- Create additional GPOs for desktop restrictions and audit settings
- Implement roaming profiles or folder redirection
- Add PowerShell automation for user and group provisioning
- Expand the lab with Azure AD Connect or hybrid identity components
- Add backup, monitoring, and patch management documentation

## Resume-Ready Project Summary

Built a Microsoft Azure-based enterprise identity lab using Windows Server and Active Directory Domain Services. Deployed a domain controller (`DC01`) in Azure, configured the `corp.local` domain, created organizational units and role-based security groups, enforced password policy through Group Policy, validated DNS functionality, and implemented a shared folder with group-based access controls. Documented the full environment with architecture screenshots and supporting technical notes for portfolio presentation.
