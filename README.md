# backitude2GoogleSheet
backitude server side implementation. Send location directly to google sheet.

Idea
---------------
1. Create a Google Form.
2. Obtain names of text fields on form and the form action URL.
3. Configure backitude to POST data to Google form.
4. Plot location data to Google Map from Google Sheet.

I stuck
-------------
backitude should allow me to add custom HTTP headers. I need `Content-Type": "application/x-www-form-urlencoded` this header to go along with request.

Features
----------------
The google sheet can be exclusively shared with some google users, Say friends Circle.
A Google user can obtain JSON or XML feeds from google sheet, obviously user must have read access to sheet.
Using above 2 rules we can program goole app / web app which can plot those points on map.

How to obtain Feeds URL from Unpublished google sheet.
-------------------------------------------
Go To
```
https://spreadsheets.google.com/feeds/worksheets/[WORKBOOK_ID]/private/full?v=3.0
```
Here you see Sheets in workbook
View Source, and search for Sheet Name

Eg, Form Responses 1
```
<title>Form Responses 1</title>
<content type='application/atom+xml;type=feed' src='https://spreadsheets.google.com/feeds/list/[WORKBOOK_ID]/[WORKSHEET_ID]/private/full?v=3.0'/>
```
Above is the link of form responses.

--Search for `<content>` tag in this page =
```
https://spreadsheets.google.com/feeds/list/[WORKBOOK_ID]/[WORKSHEET_ID]/private/basic?v=3.0
```
There you will see comma separated fields
field1:value,field2:value
