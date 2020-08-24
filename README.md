# Note: You need Winter'21 org with DevHub enabled

sfdx force:config:set apiVersion=50.0

sfdx force:auth:web:login -d -a myhuborg  "Replace with Your debhub org"  

sfdx force:org:create -s -f config/project-scratch-def.json -a appointapp -d 30

**Push Perms for content builder and email template**  
sfdx force:source:deploy -u appointapp -m PermissionSet:AppointmentAppPerms

**Assign content builder and email template perms**  
sfdx force:user:permset:assign -n AppointmentAppPerms -u appointapp

**Push the source code**  
sfdx force:source:push  -u appointapp -f

**Assign app perms**  
sfdx force:user:permset:assign -n Appointment_Manager_Permission -u appointapp

**Open the app**  
sfdx force:org:open -u appointapp

**Got to Appointment app, create an appointment and email the patient**  

**Change the password**  
sfdx force:user:password:generate -u appointapp

**On Phone, go to salesforce mobile app and scan the QR code from the email**  

