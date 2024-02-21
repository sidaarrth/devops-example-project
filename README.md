# devops-example-project
#created script to reset bulk password using powershell script
# Load user list
**#store users login ID in this text file**
 $ListOfUsers = Get-Content D:\Userlist.txt 
 foreach ($user in $ListOfUsers) {
     #Convert the password to secure string
     #Set the default password which you want to assign to user
     $Pass = ConvertTo-SecureString -String "India@24" -AsPlainText –Force
     #Reset the account password
     Set-ADAccountPassword $user -NewPassword $Pass -Reset
     #Force user to change password at next logon
     Set-ADUser -Identity $user -ChangePasswordAtLogon $true
     #Display userid and password values 
     Write-Host $user, $Password
 }
