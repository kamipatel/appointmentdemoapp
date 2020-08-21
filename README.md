sfdx force:config:set apiVersion=50.0

sfdx force:auth:web:login -d -a myhuborg
kamlesh.patel-qq1l@force.com

- Enable email perms
sfdx force:user:permset:assign -n AppointmentAppPerms -u appointmentapp

sfdx force:org:create -s -f config/project-scratch-def.json -a appointmentapp -d 30


sfdx force:source:deploy -u appointmentapp -m PermissionSet:AppointmentAppPerms

https://developer.salesforce.com/docs/component-library/documentation/en/lwc/lwc.use_barcodescanner_example

sfdx force:user:permset:assign -n Appointment_Manager_Permission -u appointmentapp

sfdx force:org:open -u appointmentapp

sfdx force:source:pull  -u appointmentapp

sfdx force:source:push  -u appointmentapp