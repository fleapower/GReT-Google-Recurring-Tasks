# GReT (Google Recurring Tasks)
A Google script to create recurring tasks without relying upon a Chrome extension, or an Android or iOS app.  Since the recurrence is managed by Google scripts, the recurrence is is universal.  That is, it will work regardless of app or even without an app.

## Setup
1)  Copy the Google sheet with the GReT script into your Google Drive:
	1. Go to https://docs.google.com/spreadsheets/d/1vmQA7QvmNIPwdK_KUAfLXzmd7rwMb5F9PryI5Eg6vJI/edit?usp=sharing
	2. File -> Make a Copy...
	3. (Optional) Change the Name and/or Folder
2)  Set up your preferences:
	1. Tools -> Script editor
	2. In the DuplicateRecTask function:
		- Set your time zone (TZOffset): 5 is EST, 8 is PST
		- Set Archive variable (1 will archive your tasks to the Archive spreadsheet and delete them from Google tasks, 0 will do nothing)
3)  Set and allow the trigger:
	The function createDailyTrigger will automatically set up a trigger to run at midnight and recur the tasks.  You may modify the function below to set up a trigger at a different time and/or interval or set up the trigger manually.  To have the trigger set up automatically:
	1. Run -> Run Function -> createDailyTrigger
	2. Authorization Required -> Review Permissions
	3. Select the appropriate account
	4. Allow
4)  Allow (verify) Task API's.
	1. Run -> Run Function -> DuplicateRecTask
	2. If an error message pops up, select "Details."  If no error message pops up, skip to step 7.
	3. Copy the URL in the dialog box and paste it into a new browser window
	4. Accept terms of service if necessary
	5. Select Enable.
	6. Go back to step 1 to ensure Task API is working correctly.
	7. Task API is enabled and working correctly!
	
## Syntax
* To recur on a set interval after task completion, use r:##x
* For a specific day of the week or month, use r:xDD
* For a specific date of the year, use r:yMMDD
* To keep the annotation order straight in your mind, think of the syntax this way:
	- Recur after task completion, "Recur every 4 days."  The string would be r:04d ('d' is last, just like in the sentence)
	- Recur on the same day of the week, "Recur weekly on the 5th day."  The string would be r:w05 ('w' is first)
### More examples:
	- Every day:  r:01d
	- Every two days:  r:02d
	- Every three weeks:  r:03w
	- Every three months:  r:03m
	- Every Tuesday:  r:w03
	- 28th of each month:  r:m28
	- Every two years:  r:01y
	- Every year on a August 10th:  r:y0810
