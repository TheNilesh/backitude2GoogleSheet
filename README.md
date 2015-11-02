# backitude2GoogleSheet
backitude server side implementation alternative. Send location information directly to Google Drive - SpreadSheet.

Overview
---------------
1. Create a Google Form.
3. Configure backitude to POST data to Google form.
4. Plot location data to Google Map from Responses Spreadsheet, using Google-Script or Web App.

Concern
-----------------
It might be against Google TOS.

Advantage
----------------
 0. The spreadsheet can be exclusively shared with specific google users, Say friends Circle. Hence restricted location sharing is possible.
 1. We can obtain RSS, JSON or XML feeds from google sheet.
 2. Using above features we can program web app which can plot those points on map.

Create Google Form
--------------------
 0. Create Google Form with as many fields you wanted to record from backitude, say Latitude, Logitude, Accuracy, Speed.
 1. Click **View live form**
 2. View Source, note down **ACTION-URL** from `<form action="[ACTION-URL]"`.
 3. Also note down names of text fields. They are in format _entry.1234_

Configure backitude
-------------------------
 0. Settings > Custom Server Settings.
 1. Server URL = **ACTION-URL**
 2. Successful Response Code(s) = 200,201
 3. Request Type = POST
 3. Enter text field names we noted earlier into corresponding boxes, Latitude, Longitude, Accuracy.
 4. Hit Run Test and check into Responses Spreadsheet.

How to obtain Feeds from unpublished google sheet.
-------------------------------------------
 0. Open SpreadSheet linked to Google Form we created earlier, for Editing
 1. Grab `[WORKBOOK_ID]` from URL in address bar, ```https://docs.google.com/spreadsheets/d/[WORKBOOK_ID]/edit```
 2. Open `https://spreadsheets.google.com/feeds/worksheets/[WORKBOOK_ID]/private/full?v=3.0`
    Here you see list of sheets in workbook, View Source of this page, and search for Sheet Name.
    Eg, Form Responses 1

      ```
      <title>Form Responses 1</title>
      <content type='application/atom+xml;type=feed' src='https://spreadsheets.google.com/feeds/list/[WORKBOOK_ID]/[WORKSHEET_ID]/private/full?v=3.0'/>
      ```
 3. Use link `https://spreadsheets.google.com/feeds/list/[WORKBOOK_ID]/[WORKSHEET_ID]/private/full?v=3.0`.
 4. There you will see comma separated fields `field1:value,field2:value`

Conclusion
--------------------------------
This is an easy way to collect data from backitude app, as it does not involve creating server side application. The location data is stored in managable spreadsheet. It can be pulled easily from javascript and rendered on map.
