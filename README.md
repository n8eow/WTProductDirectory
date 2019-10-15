# WTProductDirectory

This is where you include your WebPart documentation.

Followed this guide:
https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/build-a-hello-world-web-part

How to set up your SharePoint Framework development:
https://docs.microsoft.com/en-us/sharepoint/dev/spfx/set-up-your-development-environment

If you get a gulp "internalBinding is not defined" error:
https://stackoverflow.com/questions/54433794/gulp-internalbinding-is-not-defined




### Building the code

```bash
git clone the repo
npm i
npm i -g gulp
gulp
```

This package produces the following:

* lib/* - intermediate-stage commonjs build artifacts
* dist/* - the bundled script, along with other resources
* deploy/* - all resources which should be uploaded to a CDN.

### Build options

gulp clean - TODO
gulp test - TODO
gulp serve - TODO
gulp bundle - TODO
gulp package-solution - TODO



### Adding new Web Parts
To add a new web part to the project, use the Yoeman generator. I followed this article:
https://www.c-sharpcorner.com/article/add-multiple-webparts-to-single-spfx-solution-using-yeoman/

Steps:
1. In command line type "yo @microsoft/sharepoint"
2. Select "Webpart"
3. Select "React"


### Some Dev Notes

#### CSS specificity (https://docs.microsoft.com/en-us/sharepoint/dev/spfx/office-ui-fabric-integration#the-css-challenge-with-office-ui-fabric)

How CSS specificity applies to web UI. Higher specificity styles override lower specificity styles, but the key thing to understand is how the specificity rules apply. In general, the precedence order from highest to lowest is as follows:

    The style attribute (for example, style="background:red;")
    ID selectors (#myDiv { })
    Class selectors (.myCssClass{}), attribute selectors ([type="radio"]), and pseudo-classes (:hover)
    Type selectors (h1)

Loading order. If two classes are applied on an element and have the same specificity, the class that is loaded later takes precedence. As shown in the following code, the button appears red. If the order of the style tags is changed, the button appears green. This is an important concept, and if not used correctly, the user experience can become load order-dependent (that is, inconsistent).



#### List Data Access Notes
To get the access working, I followed this person's advice:
https://www.ktskumar.com/2017/01/access-sharepoint-online-using-postman/

And, I used the following article, too:
https://blogs.technet.microsoft.com/fromthefield/2013/09/05/working-with-sharepoint-list-data-odata-rest-and-javascript/



https://wppdigital.sharepoint.com/sites/productdirectory/_api/web/lists/GetByTitle('Products')/items


WT Product Directory Tenant ID "(Bearer realm")
72a7869c-4ceb-4851-914f-53417f3f2c69

WT Product Directory Client Id:
5ea69560-4340-4fd0-a7b2-fe6daf2c1a00

WT Product Directory Client Secret:
K/ECDK5nX+d3qyowmJ1nuFkdx3A1SO4FTC5RNlY8Do4=

WT Product Directory Resource Information
client_id="00000003-0000-0ff1-ce00-000000000000

example authentication call (used in Postman, but I forget exactly for which field)
00000003-0000-0ff1-ce00-000000000000/wppdigital.sharepoint.com@72a7869c-4ceb-4851-914f-53417f3f2c69

WT Product Directory Sample access_token:

{
    "token_type": "Bearer",
    "expires_in": "28800",
    "not_before": "1562352511",
    "expires_on": "1562381611",
    "resource": "00000003-0000-0ff1-ce00-000000000000/wppdigital.sharepoint.com@72a7869c-4ceb-4851-914f-53417f3f2c69",
    "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIng1dCI6IkN0ZlFDOExlLThOc0M3b0MyelFrWnBjcmZPYyIsImtpZCI6IkN0ZlFDOExlLThOc0M3b0MyelFrWnBjcmZPYyJ9.eyJhdWQiOiIwMDAwMDAwMy0wMDAwLTBmZjEtY2UwMC0wMDAwMDAwMDAwMDAvd3BwZGlnaXRhbC5zaGFyZXBvaW50LmNvbUA3MmE3ODY5Yy00Y2ViLTQ4NTEtOTE0Zi01MzQxN2YzZjJjNjkiLCJpc3MiOiIwMDAwMDAwMS0wMDAwLTAwMDAtYzAwMC0wMDAwMDAwMDAwMDBANzJhNzg2OWMtNGNlYi00ODUxLTkxNGYtNTM0MTdmM2YyYzY5IiwiaWF0IjoxNTYyMzUyNTExLCJuYmYiOjE1NjIzNTI1MTEsImV4cCI6MTU2MjM4MTYxMSwiaWRlbnRpdHlwcm92aWRlciI6IjAwMDAwMDAxLTAwMDAtMDAwMC1jMDAwLTAwMDAwMDAwMDAwMEA3MmE3ODY5Yy00Y2ViLTQ4NTEtOTE0Zi01MzQxN2YzZjJjNjkiLCJuYW1laWQiOiI1ZWE2OTU2MC00MzQwLTRmZDAtYTdiMi1mZTZkYWYyYzFhMDBANzJhNzg2OWMtNGNlYi00ODUxLTkxNGYtNTM0MTdmM2YyYzY5Iiwib2lkIjoiMTQ2YzVhYTctYTcxYS00YjhjLTk4N2ItZjM5YzhjZDE1NGFmIiwic3ViIjoiMTQ2YzVhYTctYTcxYS00YjhjLTk4N2ItZjM5YzhjZDE1NGFmIiwidHJ1c3RlZGZvcmRlbGVnYXRpb24iOiJmYWxzZSJ9.Y57SLG5LjVMlho0gW6oJ6eNvKmU_HOTKbZjchMyRvWMuzZRV19Phvr5T0vKZ2TgXFO1zODthhjHuQxKn2PJhGPuqi5c0SGo3VlI3BiX2K1O4mo37n1ZMos4Nf9yIxeQExHi-5eldIyx-LTylAwuVHtaTTP1LGgM7nVEvsvqiZ1bzWwOtNk8mDaLXuhl328CMI9Gl8tB6hQAYyAehaq_8mfXkpTIbD4mkwFSv3IZZ0gsHjiaw9yBramNNRAeFmjModRFz_lgok-vKMmxgLabMwtKf8oOuWaqU1vXYAmdmB4FzXOSWg4N3JyDU86nMxXTtyZkcxS-hmxqssUIrVVtdng"
}
