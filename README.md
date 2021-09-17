# Covenant C2 Pivot
>> Performing a pivot using the Covenant C2 technology.

## Initial Setup
- Pinging all the hosts is very important to establish that they all have a connection to each other over the “host-only” network.
- This is the Kali Linux host pinging the tortuga_dc and tortuga_server hosts.

![img](https://github.com/elisims/c2pivot/raw/main/images/1.jpg)

- This is the tortuga_dc pinging the Kali Linux and tortuga_server hosts.

![img](https://github.com/elisims/c2pivot/raw/main/images/2.jpg)

- This is the tortuga_server pinging the Kali Linux and tortuga_dc hosts.

![img](https://github.com/elisims/c2pivot/raw/main/images/3.jpg)

- With all the connections checked and established we can now start the pivot preparation."

## Initiating the Pivot

- Starting Covenant using the command “sudo dotnet run” within the Covenant directory.

![img](https://github.com/elisims/c2pivot/raw/main/images/4.jpg)

- Covenant can be managed by navigating to https://127.0.0.1:7443 in a browser.

![img](https://github.com/elisims/c2pivot/raw/main/images/5.jpg)

- Now I needed to start a new listener on port 80 by clicking on “Listeners”>create.

![img](https://github.com/elisims/c2pivot/raw/main/images/6.jpg)

- The important edits to this form are giving the Listener a name, in this case “L2” and then providing the connectAddress. I am going to just leave the default Port at :80.

![img](https://github.com/elisims/c2pivot/raw/main/images/7.jpg)

- Once the Listener has been created, it is time to generate a PowerShell Launcher to pass to the target. The important fields to fill out on this form are the Listener name (which is the name we filled out earlier) and bringing the delay down to 1, Jitter down to 2, and
ensuring that the connect attempts is around 5000.

![img](https://github.com/elisims/c2pivot/raw/main/images/8.jpg)

- Once the payload has been generated (by clicking the “generate” button), the payload needs to be hosted. So, click the “host” tab and put in a path easy to remember- We used /567 here because we are doing this for our IT&C567 class.

![img](https://github.com/elisims/c2pivot/raw/main/images/9.jpg)

- Once  that  information  is  filled  out,  click  the  “host”  button  to  ensure  the  payload’s PowerShell command is updated.

![img](https://github.com/elisims/c2pivot/raw/main/images/10.jpg)

- Once this setup has been completed, simply navigate to the IP that you chose to host the payload  on-  In  our  case  192.168.214.130/567-  In  a  browser  to  check  if  the  payload’s PowerShell one liner is there.

![img](https://github.com/elisims/c2pivot/raw/main/images/11.jpg)

- The payload has indeed been successfully established; therefore, we need to copy this one liner and execute it in the PowerShell application so that the C2 will be downloaded to this host.

![img](https://github.com/elisims/c2pivot/raw/main/images/12.jpg)

- Finally, we need to need to create another launcher, but this time it needs to be an SMB grunt- Which requires a few different parameters for the Covenant form.

![img](https://github.com/elisims/c2pivot/raw/main/images/13.jpg)

- For this launcher, we need a Listener (we used the name L1) and an SMBPipeName (we used the pipeName “it567”). All the other parameters can remain the same as before. Then, once again we need to host the payload- So click the “host” tab and this time make the path “/it567/smb”.

![img](https://github.com/elisims/c2pivot/raw/main/images/14.jpg)

- Then click the “host” button to update the PowerShell one liner.

![img](https://github.com/elisims/c2pivot/raw/main/images/15.jpg)

- Finally,  once  this  setup  has  been  completed,  on  the  target  machine  navigate  to  the address we established in the above instructions “192.168.214.130/it567smb” and check if the payload has been successfully hosted there.

![img](https://github.com/elisims/c2pivot/raw/main/images/16.jpg)

- With the PowerShell one liner successfully established on the target machine, simply copy and paste the one liner into a   owerShell terminal and we have officially established a C2
through an  SMB connection."

![img](https://github.com/elisims/c2pivot/raw/main/images/17.jpg)
