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
- Placeholder appears after upload asset for users of type USER (frontend:1.0.0.8, backend::1.0.0.9)
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
### Removed
