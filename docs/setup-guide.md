# Setup Guide

## Purpose

This guide documents the main build steps used to create the Azure Enterprise Identity Lab. It is written as a concise walkthrough for reviewers, recruiters, or anyone recreating the environment at a high level.

## 1. Azure Infrastructure Deployment

The environment begins in Microsoft Azure with the creation of the base infrastructure.

- Created resource group `RG-EnterpriseLab`
- Deployed Windows Server VM `DC01`
- Configured the virtual network for internal communication
- Applied a network security group to control allowed traffic

These resources form the hosting platform for the Active Directory lab.

## 2. Windows Server and Domain Controller Setup

After deployment, `DC01` was configured as the central server for the lab.

- Installed Active Directory Domain Services
- Promoted `DC01` to a domain controller
- Created the domain `corp.local`
- Validated successful domain creation and service availability

This established the core identity infrastructure used throughout the lab.

## 3. Active Directory Structure

To organize users and systems in a realistic enterprise layout, the following OUs were created:

- `HR`
- `IT`
- `Managers`
- `Servers`
- `Workstations`

This structure supports clean administration and policy targeting.

## 4. User and Group Configuration

The following user accounts were created for testing and administration:

- `HRuser1`
- `Helpdesk1`
- `ITadmin1`
- `Manager1`
- `Manager2`

The following security groups were created:

- `HR_Users`
- `IT_Admins`
- `Management`

Users were placed into groups based on role to support role-based access control.

## 5. Group Policy Configuration

A Group Policy Object named `Corp Security Policy` was created and linked at the domain level.

Configured password settings:

- Minimum password length: `12`
- Complexity enabled
- Maximum password age: `90 days`
- Minimum password age: `30 days`

This demonstrates centralized enforcement of a basic enterprise security standard.

## 6. DNS Validation

DNS was reviewed on `DC01` to confirm that the Active Directory environment had proper name resolution support.

Validation focused on:

- Domain-aware DNS functionality
- DNS console visibility
- Basic infrastructure health after promotion

## 7. Shared Folder and Access Control

A shared folder was created for department-based access testing.

- Local folder path: `C:\CompanyData`
- Network share path: `\\DC01\CompanyData`

Assigned permissions:

- `IT_Admins`: `Full Control`
- `Management`: `Change`
- `HR_Users`: `Read`

This demonstrates both resource sharing and access control planning using security groups.

## 8. Validation

Final checks included:

- Reviewing AD domain structure
- Confirming user and OU creation
- Verifying GPO linkage
- Reviewing DNS configuration
- Confirming share access settings
- Running `gpupdate` validation

## Publishing Notes

Before making this repository public:

- Remove or blur any sensitive values visible in screenshots
- Do not publish passwords, subscription IDs, public IP addresses, or personal email addresses
- Keep sample usernames generic and portfolio-safe

## Related Files

- Main project summary: [README.md](/C:/Users/devan/Desktop/azure-ad-lab/README.md)
- Screenshot map: [docs/screenshot-index.md](/C:/Users/devan/Desktop/azure-ad-lab/docs/screenshot-index.md)
