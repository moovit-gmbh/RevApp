# RevApp Changelog

All notable changes for the private product RevApp will be documented in this file.

## [05.06.2024]
### Fixed
- Improve video download behaviour (frontend:1.0.0.24)

## [initial release]
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
- Add searchbar to admin pages (namespaces, users and groups) (frontend:1.0.0.19, backend:1.0.0.19)
- Add filter checkbox to filter out selected users/ groups in the corresponding edit dialogs and to the share dialog and sort by items that are selected or that have rights set (frontend:1.0.0.19, backend:1.0.0.19)
- Add pagination options 15 - 101 to all table views (frontend:1.0.0.19, backend:1.0.0.19)
- Add email light mode (frontend:1.0.0.19, backend:1.0.0.19) - deletion of existing preference entry EMAIL and restart of backend container required
- Add a "copy to clipboard" action for the public link into the context menu of the share dialog for public links (frontend:1.0.0.22)
- Add a new quick view and approve dialog that can be accessed via tile view by selecting one tile and hit the space bar (frontend:1.0.0.22)
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
- Send email to internal users or public link users when triggering it via API or Helmut RevApp nodes should now work properly (backend:1.0.0.17)
- Make timecode in/outpoint badges of comments section more readable and fix issue where all timecode have been overwritten by edition one timecode of one comment (frontend:1.0.0.17, backend:1.0.0.18)
- Avoid sending multiple mails when using api and assigning job to internal users (backend:1.0.0.18)
- Redirect to login page when user gets unauthorized during application browse (frontend:1.0.0.17)
- It's not possible anymore to set an outpoint before an inpoint (frontend:1.0.0.21, backend:1.0.0.21)
- Refactored all password change pages and removed the requirement to apply old password on change whenever an admin user is logged in (frontend:1.0.0.21, backend:1.0.0.21)
- Fixed skip upload feature for the Revapp Upload Asset Action node (worker:1.0.0.8)
- Fixed multiple email sending whenever the rights of an job gets changed (backend:1.0.0.23)
- Overwriting creator in email now also possible for public link sharing (backend:1.0.0.23)
- Search fields now not case sensitive with upper cases (frontend:1.0.0.22)
- Users with SHARE rights are now actually able to share an asset (backend:1.0.0.23)
- Changed timestamp field of audit logging database entry to be a date and added database index for that (backend:1.0.0.23)
- Fixed namespace filter for message bus update of add job (frontend:1.0.0.22)
- When changing the language back to master language English the rights where not translated correctly and therefore the switches did not display any rights -> fixed with(frontend:1.0.0.22)
- Several multiselect refactorings (frontend:1.0.0.22)
  - Fix multiselect checkbox behaviour of list view
  - Add multiselect for tile view
    - Add selection indicator border
    - With shift + click multiple tiles can be selected
  - Fix multiselect top bar menu that does not disappear on scroll and fix it's selected jobs counter
- Fix pagination (frontend:1.0.0.22, backend:1.0.0.23)
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
- When using the Helmut upload to RevApp node the worker will fist check if the file is accessable and tries to skip the upload (worker:1.0.0.7)
- When sharing via Helmut RevApp Share by Email node the email requestor will be overwritten with the creator of the job instead of using the API user (backend:1.0.0.17)
- Security: 
  - Removed external dependency requests (frontend:1.0.0.16)
  - Not exposing account information on failed login attempts (frontend:1.0.0.16)
  - Hide nginx server version (frontend:1.0.0.16)
  - Add all security headers except Content-Security-Policy (frontend:1.0.0.16)
- Change filename of downloaded video to be the job name (frontend:1.0.0.17)
- Block right click context menu on video in detail page to avoid direct download (frontend:1.0.0.22)
- Change basket icon to cancel icon for cancelation of edit / reply process in comments section to avoid misleading expectation that comments can be deleted (frontend:1.0.0.22)
- Added hover effect to table rows (frontend:1.0.0.22)
- Enlarged title in player (frontend:1.0.0.22)
### Removed
