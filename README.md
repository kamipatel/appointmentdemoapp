sfdx force:config:set apiVersion=50.0

sfdx force:auth:web:login -d -a myhuborg
test-zovmkezpwaiv@example.com

sfdx force:org:create -s -f config/project-scratch-def.json -a appointapp -d 30

### Push Perms for content builder and email template
sfdx force:source:deploy -u appointapp -m PermissionSet:AppointmentAppPerms

### Assign content builder and email template perms
sfdx force:user:permset:assign -n AppointmentAppPerms -u appointapp

sfdx force:source:push  -u appointapp -f

sfdx force:user:permset:assign -n Appointment_Manager_Permission -u appointapp

sfdx force:org:open -u appointapp

### Create an appointment and email the patient

### Change the password
sfdx force:user:password:generate -u appointapp

### On Phone, go to salesforce mobile app and enter

