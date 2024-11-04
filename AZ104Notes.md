# AZ-104 Notes

## Day 0

Instructor: Greg Lojek
<br/>
Teams meeting link: https://tinyurl.com/368f25nz


## Day 1

### SkillUp Labs

URL: https://firebrand-uk.learnondemand.net/Class/645637
<br/>
Username: Deloitte Email
<br/>
Password: Pa$$w0rd

- Labs are valid for 6 months.
- You have 10 attempts for each lab.
- Each session has an expiration time so keep an eye on the timer. There will be a popup warning when the time nears, you will have a option to extend your session if needed.
- Labs can not be saved midway through.

If you get a dropout there is a button at the top with a reconnect option to refresh the RDP connection
If no Internet access then click the lightning log and click reset Internet gateway
If it totally fails contact the support on the portal to log the issue

In the instructions tab, tick off the steps as you go. This tells you how long is left and also acts as a bookmark if the machine has to be rebooted.

The cleanup resources task do not need to be run if it is using the lab's VM as the subscription gets auto scrubbed on ending the lab. These instructions are for those using their own subscriptions.

It is not possible to copy paste. If you need to copy paste, you can click on the lightning bolt go to copy text and select copy clipboard text to open a dialog box you can paste into

**Confirm in teams meeting when you have completed the lab.**

### Administer Identity
Q: What is the difference between Office 365 and Microsoft 365?
A: There are lots of differences such as:
- Information protection plans.
- **Different Entra plans**.
- Intune is not in Office 365.
- Threat protection.
- Data lifecycle management.
- Insider risk management
- Microsoft Purview
  - Adaptive Protection.

A full breakdown of differences can be found here: https://go.microsoft.com/fwlink/?linkid=2139145&clcid=0x409&culture=en-us&country=us

The biggest differences we need to know about for this course is: for Office 365 you pay for all the licenses you have obtained. In Microsoft 365 you pay by usage. They also have different Entra Plans:
- Plan 1 (E3)
- Plan 2 (E5)

To help with ever chaining Microsoft ecosystem there is a place where name changes are published. In the exam the newest branding should always be used which for those experienced may struggle with if they are not fully up to date with name changes.

Microsoft product name changes: https://m365maps.com/renames.htm

There is also a useful link here that describes the differences between Microsoft 365 Apps for Enterprise and Office 2019: https://learn.microsoft.com/en-us/archive/technet-wiki/52127.office-365-proplus-and-office-2019-comparison

**Entra**

Domain controller

AD Database
sysval folder?

Authentication
Authorization
Auditing
Accounting
something else

user@domain.com is a UPN - User Principal Name: They can look like email addresses but only become so if linked to exchange

SIP - Session initiation protocol

In on prem you can have .local, .intranet etc domain which are not globally routable. in Entra we need to use globally routable domains (.com, .edu etc...)

DNS - Dynamic naming server 

In the old world we used to have DNS on the DC for internal and then DNS in DMZ to resolve external names
When shifting to using globally routed the two DNS servers. which will respond with different names. This is Split DNS, Slit Horizon or Split Brain DNS.


When going hybrid you should look to get rid of local domains.

Kerberos, NTLM are authentication methods on Active Directory the default session validation length is 10 hours
In Entra we have different protocols for authentication:
- SAML
- Oauth
- OpenID
- WS-Federation

The reason we have so many different protocols is because of the way cloud distributes the data.

- Identity: An object that can be authenticated
- Account: And identity that has data associated with it
- An identity created through Microsoft Entra ID or another Microsoft cloud service
- Tenant/directory: A dedicated and trusted instance. A tenant is automatically created when your organisation signs up for Microsoft cloud service subscription
  - Additional instances can be created
  - Microsoft Entra ID is the underlying product providing identity services
  - The term Tenant means a single instance representing a single organisation
  - The terms Tenant and Directory are often used interchangeably
- Azure Subscription: Used to pay for Azure cloud services

Entra ID includes Federation Services and many third party services such as Facebook, Apple etc.

**ADDS  - Active Directory Domain Services**
**EidDS - EntraID Domain Service**

AD = On Prem
EntraID = On Cloud
Hybrid = Entra Connect to sync between AD and EntraID
EntraId Domain Services = For apps that need legacy protocols but want to use cloud (this is PaaS)

https://www.apps4rent.com/azure-active-directory-pricing.html

Delegate group creation permissions, this allows you to have security groups to alow or disable the options for example allowing a group of manages to create teams channels but others to not be able to do this.

Dynamic Group Creation - Allows us to create groups that are based on rules rather than manually managed. Be this users or things like devices. For example you could have a registered devices group for Android and another ofr Apple. You can drive this dynamically to help with intune management.

Conditional Access Policies - Rules in which Users, Devices or Applications have to be satisfies to be able to connect.

Identity Protection and Governance Features are only in EntraId Option 2
This includes:
- Conditional Access Policies for Risks: Behavioral rule customisation, for example you can have rules like if user has moved locations from outside of the norm like login attempt in UK, then Paris then New York you can pick at which point to fire the additional check, or you can have IP range checks and many other options.
- Entitlement Management: Design workflows to decide what happens after x amount of time/promotion of users
- Privileged Identity Management (PIM): Eligible users can activate certain roles for x time rather than just being Admins off the bat.
- Access Reviewing: Snapshot of our organisation (usually monthly), helps for monitoring of user's behavior, access and a lot of other options to help with maintenance of roles, groups etc.

Win32 apps - a application that is designed to run on the Windows operating system using the Win32 API.

**Configure Device Identities**
- Registered devices
  - Supports bring your own device
  - Registered devices sign-in using a Microsoft account
- Joined devices
  - Intended for cloud-first or cloud-only organisations
  - Organisation owned devices
  - Joined only to Azure - organisation account required
  - Can use conditional access policies
  - Windows 10+ devices
- Hybrid joined devices
  - You have Win32 apps deployed to these devices
  - You want to continue to use Group Policy to manage the device
  - You want to use existing image solutions to deploy services
  - Windows 7+ devices

**Self-Service Password Reset (SSPR)**
Microsoft now recommends having passwords that never expire: This is because studies have shown that enforcing this rule actually results in weaker passwords. Using things like MFA and conditional access firm things up a lot more. This needs P1 or P2.

1. Determine who can use self-service password reset
2. Chose the number of authentication methods required and the methods available (email, phone, questions etc.)
3. You can require users to register for SSPR (same process as MFA)

### Configure User and Group Accounts
**Users**
- All users must have and account
- The account is used for authentication and authorization
- Each users account has additional properties

Manage User Accounts
- Must be Global Administrator or User Administrator to manage users
- User Profile (Picture, job, contact info) is optional
- Deleted users can be restored for 30 days
- Sign in and audit log information is available


*Powershell*

- Get MsolUser - Microsoft 365 Users^
- Get-AZADUser - Users in Azure^
- Get-AzureADUser - EntraId^
- Get-MGUser - MG Graph (recommended for user functions going forward)

  ^Deprecated

All of these methods use a different way of managing the passing of the password to the command

**AZ-040 (Powershell course)**

**Create Group Accounts**
Group Types:
- Security groups
- Microsoft 365 groups

Assignment Types:
- Assigned
- Dynamic Users
- Dynamic Device (security groups only)

On prem security groups
- Domain Local Groups: Groups resources
- Global Groups: Groups Users and devices
- Universal Groups

On prem:
Account > Global Group > Domain Local > Permission

Entra:
Identity > Groups > Sharepoint/Teams Groups > Access control

**Assign Licenses to Users and Groups**

**Create Administrative Units**


