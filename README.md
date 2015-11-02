# backitude2GoogleSheet
backitude server side implementation alternative. Send location information directly to Google Drive - SpreadSheet.

Idea
---------------
1. Create a Google Form.
2. Obtain names of text fields on form and the form action URL.
3. Configure backitude to POST data to Google form.
4. Plot location data to Google Map from Google Sheet.

Features
----------------
 0. The google spreadsheet can be exclusively shared with some google users, Say friends Circle. Hence restricted location sharing is possible.
 1. We can obtain RSS, JSON or XML feeds from google sheet.
 2. Using above features we can program web app which can plot those points on map.

How to obtain Feeds from unpublished google sheet.
-------------------------------------------
 0. Open SpreadSheet for Editing
 1. Grab `[WORKBOOK_ID]` from URL in address bar, ```https://docs.google.com/spreadsheets/d/[WORKBOOK_ID]/edit```
 2. Open `https://spreadsheets.google.com/feeds/worksheets/[WORKBOOK_ID]/private/full?v=3.0`
    Here you see Sheets in workbook view Source, and search for Sheet Name.
    Eg, Form Responses 1
      ```
      <title>Form Responses 1</title>
      <content type='application/atom+xml;type=feed' src='https://spreadsheets.google.com/feeds/list/[WORKBOOK_ID]/[WORKSHEET_ID]/private/full?v=3.0'/>
      ```
 3. Use link `https://spreadsheets.google.com/feeds/list/[WORKBOOK_ID]/[WORKSHEET_ID]/private/full?v=3.0`.
 4. There you will see comma separated fields `field1:value,field2:value`
