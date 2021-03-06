---
title: Yet another mail merge using Gmail and Google Sheets
description: Yet another Gmail Mail Merge, based on the script by Martin Hawksey.  https://github.com/gsuitedevs/solutions/tree/master/mail-merge
labels: Sheets, Gmail
material_icon: merge_type
create_time: 2020-05-22
update_time: 2020-05-22
---

Yet another Gmail Mail Merge, based on the script by Martin Hawksey.
https://github.com/gsuitedevs/solutions/tree/master/mail-merge

* It uses a separate sheet for metadata to control the merge process, so that you can list and reference multiple merges, using the "Merge Sheet Name" variable. Just use this one sheet for all of your merges, and keep historic ones around.  There are two modes of operation:
  * _Send Scheduled Emails_: You can have it send all merge mails that need to be sent after a certain date.  
  * _Run Specific Row Mail Merge_: Run a specific mail merge corresponding to a row of the Metadata sheet.
* The above is also useful for connecting with Google Form output, where responses come in a separate "Form Responses 1" sheet.
* It also draws the template email from the user's emails using standard Gmail search queries.  This allows you to use both sent-mail, mail using a particular label (_e.g._, `label:mail-merge`) or drafts (_e.g.,_ `in:drafts`) all as ways for finding the template to use.
* It adds a debugging variable which should send the email only to a debugging email address, with pop-up alerts for checking the status of the merge process.
* It enables the sending of emails with emoji in both the text and subject lines.
* It can customize the subject line, feeding the subject line through the mail merge variable replacement process.
* Local (per email) merge sheet overrides of values from the metadata sheet, for "CC" (appends), "Reply To" and "Sender Name" columns.

## Try it
Create a copy of the sample [Gmail Mail Merge++](https://docs.google.com/spreadsheets/d/11dS1-kunj-sHA49WVtyACIqmCYOGn3Y5N1lIPPIQZoU/edit?usp=sharing) spreadsheet.

Update the **Recipient Email Address** in the column with email addresses you would like to use in the mail merge in the **Mail Merge** sheet.

Create a message in your Gmail account using markers like `{{First name}}`, which correspond to column names, to indicate text you’d like to be replaced with data from the copied spreadsheet.

In the **Metadata** worksheet, specify the template email (commonly in Drafts, specified by `in:draft` using the **Search Restriction** and the **Search Subject Line**) that you want to use a source for the mass mailing.

In the copied spreadsheet, click on custom menu item `Mail Merge` > `Run Specific Row Mail Merge`.  For example, to run the example mail merge partially completed, type `2`. 

A dialog box will appear and tell you that the script requires authorization. Read the authorization notice and continue.

The Email Sent column will update with the message status, in both the **Metadata** and **Mail Merge** sheets.

## Next steps

Additional columns can be added to the spreadsheet with other data you would like to use. Using the `{{}}` annotation and including your column name as part of your Gmail draft will allow you to include other data from your spreadsheet. If you change the name of the Recipient or Email Sent columns this will need to be updated by opening `Tools` > `Script Editor`.

The source code includes a number of additional parameters, currently commented out, which can be used to control the name of the account email is sent from, reply to email addresses, as well as bcc and cc'd email addresses. If you would like to find out more about the features of this solution including some modifications you can make for additional functionality like setting up scheduled sending here is a related blog post.

## Known Bugs
* BCC doesn't seem to work currently.

## Development Plans
* Add BCC.
* Debug the prompt box for cancel button.
* Allow Triggers to send Scheduled Emails on cron job.
* Needs better installation instructions.
