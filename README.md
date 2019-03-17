# Kibana_ForensicDashboards
The purpose of this project is to provide a collection of dashboards that are useful for quickly conducting a forensic investigation on a host, user, or processes using centralized collection of Sysmon logs. These dashboards were created using Sysmon data injested through Kafka, you may need to adjust the field names if you are using a different forwarder.

## Usage
Log into your Kibana instance navigate to Management -> Kibana -> Saved Objects
Import the JSON file

## Host Investigation Dashboard
Enter a hostname in the search bar to investigate activity on that host.
* Timelion Network Events by user 
* Timelion Process Creation events by user 
* elastalert alerts for this host
* executed commands - events where the parent process is Cmd.exe, PowerShell.exe, wscript.exe, or cscript.exe
* EventId 1 - Process Execution events on the host
* EventId 3 - Network events on the host
* EventId 11 - File creation events on the host
* EventId 15 - Downloaded files
* EventId 12,13,14 - Registry Modification events
* EventId 19,20,21 - WMI Subscription modifications
* Login events - Windows Security Event 4624, local authentication events

## User Investigation Dashboard
Enter a username in the search bar to investigate activity on that host.
* Timeline of all events split by hostname
* count of user related events per hostname
* Processes excuted by the user
* Network Connections by the user
* Files Created by the user
* Files Downloaded by the user
* Registry modifications by the user
* Local authentication events by the user

## Sysmon-ProcessInvestigation
Dashboard for investigating individual processes using the ProcessGuid in Sysmon events. Every executing process has a unique process_guid that can be used to show every sysmon event related to that process. Process Creation events also contain the parent_process_guid which can be used to track the lineage of a processes.
