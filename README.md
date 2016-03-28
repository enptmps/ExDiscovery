This script, inspired by the output of an Exchange TAP tool, aims to automatically generate a report that gives you an overview of your environment, Exchange 2003, 2007, 2010, 2013 and 2016 servers and database availability groups – in particular:
•Total Servers per Exchange version & service pack
•Total Mailboxes per Exchange version & service pack, plus Office 365 remote mailboxes
•Totals for Exchange roles across the environment
•A site-by-site breakdown for the following: •Mailboxes per site
•HTTPS FQDNs used for Internal, External and SCP URLs
•CAS array names
•Exchange servers, version, update rollup and version, service level, highlighted installed roles, OS version and service pack
•A breakdown of each Database Availability Group including: •DAG name, member count and member list
•Database information such as •Name
•Mailboxes per database and Average Size
•Archive mailboxes per database and Average Size – only shown if a DB includes Archive mailboxes
•Database and whitespace size
•Database and log disk free space percentage
•Last full backup date/time (new) – only shown if at least one DAG DB has had a full backup
•Circular Logging state (new) – only shown if at least one DAG DB has circular logging enabled
•Server hosting the active copy
•List of servers hosting copies and copy count
•A breakdown of Non-DAG databases including Exchange 2007 and 2003 DBs, including the database information above, along with Storage Group name (where applicable).

The script doesn’t support detailed information about Exchange 2007/2003 CCR/SCC clusters, but these are shown as ClusMBX in the output. At the moment, the script doesn’t show Public Folder information.

To be able to execute the script, you need to use the Exchange Management Shell (the latest version for your environment, with Powershell 2.0) and be able to get information about AD Sites, Exchange Servers, Mailboxes, Database Availability Groups and Databases. It uses WMI to retrieve OS information and detect Exchange 2007 clusters and calculate Exchange 2007 database size and Remote Registy calls to get Update Rollup information. A normal Exchange administrator should be able to perform these tasks.

Executing the script is straightforward – the only setting you need is to specify where to write the HTML file:

.\Get-ExchangeEnvironmentReport -HTMLReport c:\report.html

If you want it to email the results, the follow parameters are available to allow the report to be sent directly from the script:

.\Get-ExchangeEnvironmentReport -HTMLReport c:\report.html -SendMail:$true -MailFrom:you@example.com -MailTo:you@example.com -MailServer:smtp.example.com

As usual, the script is provided to download as-is without any warranties

