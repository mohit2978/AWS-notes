## Notes lecture 30

today we see volume and lifecycle manager!!first launch ec2 instance!!

to get more instance like running instance click on actions after selecting running instance then images an templates>launch more like this.

for 2 ec2 instance there will be 2 volumes!! 

to get which volume attached to which ec2 instance just go to volumes and select that volume and go to column attached resources!! and then change name of volume and put any name!!

/dev/sda1 is root volume .if you see in attached resources then you will be able to see it!!

![alt text](image.png)

to get password for windows server using pem file select windows server

got to actions > security > get windows password >upload key> decrypt password and then you get password

## volumes > actions

![alt text](image-1.png)

1. Modify volume (see later)
2. create snapshot backup of volume is snapshot just simply create it. to take snapshot 
automatically we use lifecycle manager by creating policies!!
3. Create lifecycle snapshot policy related to lifecycle policy
4. delete volume (greyed out) as attached to ec2
5. attach volume ( greyed out) as already attached
6. detach volume ( to detach volume )( to detach root volume stop ec2 and then detach)
  in volumes you see detached volumes in available state and attached volume in in-use state

    ![alt text](image-2.png)
    now as root volume is detach you can't start ec2 instance!!

    you need to attach to ec2 to make sure ec2 runs!! go to volumes 
    actions>attach volume

    1-b AZ can be attached to 1-b ec2 instance so limited AZ!! so will not able to see
    ec2 of other AZ!!
    ![alt text](image-3.png)

    can see device name recommendation!!
    we can attach 1 volume to 1 ec2 but io1 ,io2 can be attached to max 16 ec2 instance

    these (io1,io2 ) only can be attached to multiple ec2 instance!!

    for additional volume you can detach while ec2 is running

7. force detach volume (only works for additional volume) as sometimes when ec2 is running and 
and someone working on it after you click on detach volume it will still be in use and
the detach volume button will be greyed out so now you need to click on force detach!!
we try to detach volume it will say you can not detach so in that case you need to forcefully detach!!

 > It is not recommended to use force detach make sure everyone logs out before you detach

8. Mange auto-enabled I/O ( I/O enabled don't disable it!!)

9. Manage tags

10. fault injection (not required as new)

## Modify volumes

lets say we have volume of 30GB windows now customer says 30 Gb full!! now we want to
increase to 50 GB!!

![alt text](image-4.png)

we can change volume type and even increase size!!  
also the volume size can only be increase not decreased!!

root volume only supports SDD not HDD!!

now on windows server go to disk management!! we increase from 30 GB to 50 GB !!
so on disk management 20 GB is unallocated! AWS have no access to disk management

![alt text](image-5.png)

on 30 Gb click on extend volume and click on next next till finish!! so we increased volume 
size on fly!!

now we want to create volume additional
## create additional volume

very common real time application!! 

on volume > create volume 

![alt text](image-6.png)

for magnetic its max 1024 GB and rest its 16 TB!!

put in same AZ in which ec2 is present!!

 ![alt text](image-7.png)

give names to volume like this only!! after creating volume attach to ec2 instance!

after attaching volume to ec2 windows server just left click on 
the windows bar and go to disk management!!

![alt text](image-8.png)

your added volume will be offline just right click on offline and make it online!!
then not initialized status just right click and initialize it!!

now it shows online!!

then right click click on new additional volume !! then next next and finish!!

## create snapshot lifecycle policy or Lifecycle manager

used to automatically create snapshot and AMI's! it uses tags in policies!!

suppose for 10 volumes you want to take backup at end of day so for all that 10 volume put same tag!!

 for policy go to lifecycle manager or create snapshot lifecycle policy!!

![alt text](image-9.png)

click on custom policy ,select snapshot policy and then on next step!!

select target as volume as we need volume backup!! select tag! then description!
select default role!! policy status is enabled!!

select time when you want to take backup!! all these backup things occur at out of office hours!!

retention type means you need how many number of previous snapshot you need!! as 
if you keep extra it will be billed!!

![alt text](image-10.png)

All advanced setting are optional!!

tagging to tag snapshot

snapshot archiving  snapshot will not be deleted directly

Fast snapshot restore (FSR) restore immediately!!

cross region copy copy to another region used when entire regions goes down !!then we 
need the snapshot !! this is disaster recovery!!

if something goes wrong we have volume in another region!!

cross account sharing sharing across various accounts!!

we can also take backup of ec2 too here in lifecycle manger called as AMIs!!























































































































