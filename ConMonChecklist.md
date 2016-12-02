# Continuous Monitoring Checklist

## Instructions

After delivery of a monthly ConMon report:

1. Create a new issue in `cg-product` called "Deliver ConMon report for [due date]"
1. View the raw source of this file
1. Copy everything below the line into the new issue's body
1. Replace [due date] in title and body with the next due date
1. Put it into the "Ready" pipeline, add the HighBar label, and add it to the FedRAMP-related-work epic for that quarter
1. Submit the issue

---

In order for us to update the JAB on our compliance in a consistent way, we need to deliver a Continuous Monitoring report on [due date].

**Acceptance criteria**

* By COB on [1 work day before the due date], we've done the following:
	-  [ ] Uploaded our POA&M to [this folder](https://community.max.gov/pages/viewpage.action?pageId=1034682621)
	-  [ ] Uploaded our web scans to [this folder](https://community.max.gov/display/FedRAMPExternal/GSA+18F+Cloud.gov+Web+Scans)
	-  [ ] Uploaded our OS scans to [this folder](https://community.max.gov/pages/viewpage.action?pageId=1034682662)
	-  [ ] Uploaded our database (RDS) scans to [this folder](https://community.max.gov/pages/viewpage.action?pageId=1034682662)
	-  [ ] Emailed our PMO to let them know that's done

**Implementation sketch**

As soon as possible:

- [ ] We've scheduled a 30 min Highbar squad meeting for approximately a week before [due date] (adjusted for any holidays or squad OOO).

Starting approximately at that meeting:

- [ ] We had a 30 min Highbar squad meeting to go over the checklist, assign sub-tasks, and adjust the checklist as necessary. When possible, assign a pair of people for each scanning task so that more of us learn how to grab these.

* We ran OWASP ZAP on the following domains (using [these manual scanning instructions](https://pages.18f.gov/before-you-ship/security/dynamic-scanning/#manual-scanning), authenticated, passive):
	- [ ] https://ci.fr.cloud.gov/ - requires Cloud Ops auth
	- [ ] https://community.fr.cloud.gov/	
	- [ ] https://dashboard.fr.cloud.gov/
	- [ ] https://account.fr.cloud.gov/
	- [ ] https://landing.app.cloud.gov/
	- [ ] https://login.fr.cloud.gov/
	- [ ] https://logs.fr.cloud.gov/
	- [ ] https://metrics.fr.cloud.gov/ - requires Cloud Ops auth
- [ ] We uploaded those fresh OWASP ZAP results in XML format to [a folder in this folder](https://drive.google.com/drive/u/0/folders/0B5fn0WMJaYDnaFdCak5WNWRGb1U) (upload one XML file instead of separate files).
	- [ ] We also grabbed the OWASP ZAP scans in human-readable HTML format and uploaded them to that folder.

- [ ] We grabbed a fresh set of Nessus scans (both OS and database/RDS) from https://nessus.fr.cloud.gov/ in .nessus format and uploaded the fresh results to [a folder in this folder](https://drive.google.com/drive/u/0/folders/0B5fn0WMJaYDnaFdCak5WNWRGb1U) - requires Cloud Ops auth
	- [ ] We also grabbed the [Nessus HTML export](https://docs.tenable.com/nessus/6_8/Content/Exported_Results.htm) for those scans and uploaded them to that folder.

- [ ] If appropriate, email Veris to ask if they have verification adequate to close any of the POAM items.

* We updated [our Google Drive POA&M right here](https://docs.google.com/spreadsheets/d/16igVl8cD3SqeX5_SOn5Su34KmwMRnP20gPbfQlqIwfM/edit#gid=1701775784):
	- [ ] We updated all columns to include the most recent info about remediations, milestones, statuses, etc., including updating the status date column.
	- [ ] We corrected any items that our process indicated were incorrect last time.
	- [ ] We moved any web scanner items that should be moved to closed (in other words, items originally found by a scanner where we have new scans that prove these things are fixed.
	- [ ] We moved any OS and database scanner items that should be moved to closed (in other words, items originally found by a scanner where we have new scans that prove these things are fixed).
	- [ ] We listed any new identified web vulnerabilities are listed. (Discard the ones listed as false positives in the SAR, table E-2.)
	- [ ] We listed any new identified OS and database vulnerabilities.
	- [ ] We did a final check to make sure all columns include recent and accurate info.

- [ ] We opened a PR to update our [ConMon checklist template](https://github.com/18F/cg-product/blob/master/ConMonChecklist.md) with any changes from this month.