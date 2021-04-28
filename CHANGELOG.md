# RevApp Changelog

All notable changes for the private product RevApp will be documented in this file.

## [development release]
### Added
- Add support for basic auth
- Set display limitation parameter to have folowing posibile values 15, 25 ,50 ,75 ,101 for each table view
- Add a change user password request on login view
  - User will receive a password reset email that leads him to a password reset page, where he can reset his password
- Add audit logging in backend (backend:1.0.0.8)
- Add browser support description and known issue with edge into the public github repo
- Add translation for the job access rights (frontend:1.0.0.10, backend:1.0.0.11)
- Add endpoint for new Helmut Node (backend:1.0.0.11, streams: 4.0.4.105 (4.0.4-release-4))
  - The node is a merged version of the two share nodes with a comma separated list of emails as input. The decision wheather a public link will be send or the assignment to 
    an internal group is made RevApp internally 
- Add "*" as indicator which language is currently active and fixed the english as master language setting update (frontend:1.0.0.10)
- Add Endpoint for requesting the worker openapi documentation. It's reachable at <IP>/worker/v1/openapi.yaml (worker:1.0.0.3)
- Add preference entry for overwriting the domain of links in emails (backend:1.0.0.12)
- Add email notfication for internal users (frontend:1.0.0.11, backend:1.0.0.12)
  - Whenever the Access right VIEW is given to a user or group all users will be informed via email ones. If they loose the right and recover it again, no additional email 
    will be send.
- Add custom image support (frontend:1.0.0.11, backend:1.0.0.12)
  - Add Entry in Admin page to upload an image (filechooser or drag & drop). Limitations are 5MB size and the extensions .png, .jpg, .jpeg
  - Add Option to download the currently set image and to restore the default RevApp logo
  - Add Logo to Toolbar to make it more present
  - Add Logo to email template
### Fixed
- Reset page of Active Directory browse dialog when browsing back and forth with the breadcrumb
- Removing a namespace removes it also in from the "Select Namespace" dialog
- Upload does not break up after 120 seconds
- Fix upload for different storage paths (worker:1.0.0.1)
- Level and type attribute are now shown in the users admin tab for syncronized active directory users (frontend:1.0.0.7)
- Fix "Invalid right 0" bug in share with internal groups dialog (frontend:1.0.0.7)
- Fix search public links (frontend:1.0.0.8)
- Change click event from list tile to list item to allow clicking outside of the text in context menu of jobs and token resend link/delete (frontend:1.0.0.8)
- Add/Remove user to/from group will now update the frontend status properly (frontend:1.0.0.8)
- Add more logging and improve error handling of worker (worker:1.0.0.2)
- Fix Active Directory login into selected namespace (backend:1.0.0.9)
- Placeholder appears after upload asset for users of type USER (frontend:1.0.0.8, backend:1.0.0.9)
- Search for emails and groups in edit users/ groups dialogs is now key insensitive (frontend:1.0.0.10)
- Active Language will now be updated properly when the namespace is changed (frontend:1.0.0.11)
- Fix parallel file upload (worker:1.0.0.4)
- Fix cleanup after deletion of a job or a namespace (backend:1.0.0.14)
- Delete namespace will now be updated correctly so that a selection of the deleted namespace isn't possible anymore (frontend:1.0.0.12)
- Fix the active directory browse dialog on first opening where it gets stuck in a loading state (frontend:1.0.0.12) 
- Improve validation of every email provided in add public link dialog (frontend:1.0.0.12)
  - previously it was possible to have only one email address correctly inserted
- Improved public link behaviour on landing, page refresh and token error page (frontend:1.0.0.12)
- Clicking on RevApp text at top left in the app bar will now navigates the user back to dashboard (frontend:1.0.0.12)
- Fix share dialog error where items won't be displayed on dialog open (item.rights = undefined) (frontend:1.0.0.12)
- Remove creator from share internal dialog that popped up whenever the search toolbar was used and did match with the creator email (frontend:1.0.0.12)
- Add loading overlay after successful login to avoid short visibility of last session (frontend:1.0.0.12)
- Fix email image appearance (backend:1.0.0.14)
  - Completely remove RevApp logo whenever there is a custom logo defined
  - Resizing custom logo to 150px, larger logos might still be distorted
  - Size of image is now defined by the image itself
  - Shrinked the size of the heard in footer to be 32px and directly included it as base64 string into the email
- AD users to group assingment now working properly (backend:1.0.0.16,frontend:1.0.0.13)
  - Import users into group, remove user from group and reimport them will now readd users to revapp group
- Change Worker preference request to avoid grabbing preferences from wrong namespace and improve error handling (frontend:1.0.0.13,worker:1.0.0.6)
- Defined that usergroup rights weights more than normal group rights (backend:1.0.0.16,frontend:1.0.0.13)
- Fix access rights setting whenever job right translations are not set for a custom language (backend:1.0.0.16,frontend:1.0.0.13) 
- Add proper email input validation and avoid error page navigation when inserting invalid data in email field of login page (frontend:1.0.0.13)
- Error where "x-webdoc" prefix is added to the link url of a mail can be avoided by providing the transfer protocol http:// or https://
- Remove duplicate group assingment to jobs (backend:1.0.0.16)
### Changed
- Change upload to be direct upload to storage rather than upload to temp folder and move to storage
- Refactor whole user interface and made it mobile ready
- Limit display lenght of email in tile view to avoid variable tile hights
- Add Active Directory short name support for authentication
  - The user must still provide his email at login page, but in background the authentication will be performed using sAMAccountName attribute
- Move Upload and Preview creation to separate container called worker
  - It's possible to spin up new worker container whenever the upload requests increase
- Add a clear search when using breadcrumb navigation in active directory browse dialog (frontend:1.0.0.7)
- Change super admin password (backend:1.0.0.8)
- Freetext search in jobs dashboard is now also searching in creator field (frontend:1.0.0.7)
- Add token when email input is still highlighted is now possible (frontend:1.0.0.8)
- Login with email is now case-insensitive (backend:1.0.0.9)
- Add query parameter "creator" to add job endpoint to enable overwriting creator when using third party (backend:1.0.0.9)
  - The creator must be a valid RevApp user
- Simplified confirm dialog text by removing the object type attribute to make a proper translation more easy (frontend:1.0.0.10)
  - There are two text fields around the keyword that could be used or let empty for translation (dialogs.confirm.textOne / textTwo)
- Add job and overwrite creator: the value can be sAMAccountName that will be mapped to the mail address RevApp internally (backend:1.0.0.11)
- Add timestamp to every audit log entry (backend:1.0.0.12)
- Change the error message of a failed job request to "Sorry, the video is no longer available!" (backend:1.0.0.12)
- Add job name and namespace to share email template (backend:1.0.0.12)
  - If a user is part of several namespaces and wants review a job, he might need to login to authenticate agains RevApp. For this purpose he must 
    know to which namespace he should login to view his content
- Improved responsive behaviour of Approval Buttons in detail page and add status lock logic (backend:1.0.0.12, frontend:1.0.0.11)
  - A job cannot be approved by the creator anymore 
  - If multiple users have the right to approve, the first one who approves locks his desition (approved or not approved). He will be the only person that 
    can unlock the state to initiate a reapproval. 
  - Both infos are presented in the gui as a lock sign with tooltip<>
- Add more logging to the jobs/share endpoit to keep track of the input parameters (backend:1.0.0.14)
### Removed
