# HTB Active Directory Lab

## Objective

Gain a comprehensive understanding of Active Directory(AD) functionality and schema. Go over essential concepts related to Active Directory. Engage in hands-on practice to execute common AD management tasks, reinforcing theoretical knowledge with practical skills.

### Skills Learned

- Define and clarify commonly used AD terminology
- Investigate AD objects and structures to learn about their roles
- Explore AD functionality through PowerShell command line and a GUI interface
- Perform tasks commonly done in a Cybersecurity and IAM workspace including adding users, removing users, creating Organizational Units (OUs), and managing groups

### Tools Used

- PowerShell Terminal
- Active Directory 

## Steps
This lab was set up through Hack the Box's own Pwnbox. The first half involves reading and answering questions. The second involves completing basic AD tasks for a company.

  1. Read about Active Directory fundamentals and answer questions based on the reading.
  ![Hackthebox_lab_q-examples](https://github.com/OGkevq/HTB-Active-Directory/assets/159976397/41096189-b707-4c19-bd8f-fc791d765058)
    Ref1: A couple of the questions asked and answered after finishing a particular portion of the reading. About 35 questions in total.
  2. Open terminal in Pwnbox and use command "xfreerdp /v:(insert borrowed IP address) /u:htb-student_adm /p:Academy_student_DA" to connect to Windows AD server.
  3. Add the new users "Andromeda Cepheus", "Orrion Starchser" and "Artemis Callisto into the IT folder
   
     i. Add users via PowerShell (Open a PowerShell terminal --> Type command _"PS C:\htb> New-ADUser -Name "Orion Starchaser" -Accountpassword (ConvertTo-SecureString -AsPlainText (Read-Host "Enter a secure password") -Force ) -Enabled $true -OtherAttributes@{'title'="Analyst";'mail'="o.starchaser@inlanefreight .local"}_")
    ![HTB_Lab1_AddUser](https://github.com/OGkevq/HTB-Active-Directory/assets/159976397/846df398-f963-40aa-bcb1-15aac126c916)
     Ref2: Adding users in Powershell
     
     ii. Add users via the AD GUI (From Server Manager window, select "Tools" --> Select "Active Directory Users and Computers" --> Click on and Expand the scope "inlanefreight.local" --> Find the route to the IT folder, in this case, "Corp > Employees > HQ-NYC > IT" --> Right-click on IT, then click New > User --> Fill in the information in the pop-up window --> Click finish )
     ![HTB_Lab1_AddUsers](https://github.com/OGkevq/HTB-Active-Directory/assets/159976397/f9bc3a23-8707-4258-9f64-636b7f8fc451)
     Ref3: Adding users via GUI 

  5. Delete users that have left the company
      i. Delete users via Powershell (Open Powershell terminal --> Type command _"PS C:\htb> Remove-ADUser -Identity (insert name of user)"_)
      ![HTB_Lab1_DeleteUser2](https://github.com/OGkevq/HTB-Active-Directory/assets/159976397/ced112fe-21a9-4ff2-b69c-a53cd1f45fb1)
    Ref 4: Deleting users via Powershell

      ii. Delete users via GUI (From Server Manager window, select "Tools" --> select "Active Directory Users and Computers" --> Right click on "Employees" and select Find --> Type in the name of the user --> Right click and select delete, Hit yes to confirm)  
      ![HTB_Lab1_DeleteUser](https://github.com/OGkevq/HTB-Active-Directory/assets/159976397/ff9bf2f9-a0cd-4424-add1-073117a68bc3)
      Ref5: Deleting users via GUI
  6. Unlock the Account for user "Adam Masters" who locked themselves out (Open Powershell terminal --> Type command _"PS C:\htb> Unlock-ADAccount -Identity amasters"_)
  ![HTB_Lab1_UNlockUser](https://github.com/OGkevq/HTB-Active-Directory/assets/159976397/34b7e80c-f531-4e8e-8239-291c53c9ceaa)
  Ref6: Unlocking a user via Powershell
  7. Create a new OU called Security Analyst and add the new users to the OU
     i. Under HQ-NYC, select IT, right-click and select "new"--> "Organizational Unit". Input the name "Security Analysts", select domain local, and click ok. Drang new users into OU. 
     ![HTB_Lab1_NewOU](https://github.com/OGkevq/HTB-Active-Directory/assets/159976397/733f78d4-c4cd-4665-9492-35b85ea5de0d)
     Ref6: Image of new Users in the newly created Security Analysts OU
  
  8. Right-click on new OU and select "new"--> "Group"
  9. Right-click on new users and select "Add to group"
  
