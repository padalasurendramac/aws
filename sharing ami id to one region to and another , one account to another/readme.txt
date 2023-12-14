## Sharing ami id to one region to another and one account to another account

first step:- take the ami backup ( note:- make sure while taking the backup no reboot option shoud select)

after completed the ami backup it should available then only we can share

second step:- select ami id then client actions> copy ami > select the region > then save

third step:- select ami id > then client edit permissn options> add account number > save 
note:- make sure below option must select
 Add 'Create volume' permission to associated snapshots when creating account permissions.
