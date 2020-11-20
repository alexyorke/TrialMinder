# TrialMinder
Automatically detects when you sign up for a free trial; get reminded before you are billed.

# Setup

- install Greasemonkey
- copy and paste the script into a new Userscript
- create a new Google form that has five fields: URL (short answer), when you signed up in milliseconds since epoch (short answer), how many days from now you would like to be notified (short answer), was the trial manually confirmed (multiple choice Yes/No), who is submitting the form (short answer)
- in Google forms, click on "Responses" then click on the Spreadsheet icon then click create a new spreadsheet
- go to IFFT and make a new action for on create new Google sheet row
- when the row is created, you can link it to making a new calendar event whose deadline is the date that the form was submitted plus the number of days you want to be notified by; this might require adding a new column to the spreadsheet which contains this date automatically computed
- save IFFT
- fill in your Google form id at the top of this script
- at the bottom, fill in the form components (try submitting the form in an incognito window then using the Dev Tools to find what the raw response is)
- save the script

When you visit a website, by default if it thinks it is a trial it will silently log the URL and when you visited the website (with the default trial days) to the Google form in the background. You can disable this feature. It also has an intentionally ugly yellow button where you can manually log the website.

# How it works

TrialMinder scans the URL of every website that you visit (the scanning process occurs locally) and tries to determine if it is a free-trial website. It uses a few rule-based heuristics that are common with free-trial websites, including the URLs of popular websites such as Netflix where the URL pattern is a bit different.

If TrialMinder suspects that a website is a trial, it will by default submit the URL to the Google form that you provided. The auto-submission feature can be turned off. It also shows a super ugly yellow button where you can manually log the trial. After linking the Google spreadsheet (which is linked to the form), IFFT can automatically schedule Google calendar events so that you are reminded to cancel.
