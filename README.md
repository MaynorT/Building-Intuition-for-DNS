<p align="center">
<img src="https://i.imgur.com/CtGfsq8.png" alt="osTicket logo"/>
</p>

<h1>Building Intuition for DNS</h1>
In this lab we will be experimenting with DNS. This lab will help us have a better understanding of DNS.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- DNS

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Active Directory Virtual Machine
- Client Machine joined to your domain

<h2>Lab Steps</h2>
<p>
</p>
<p>
First we will be inspecting DNS A-Records on the server A records are hostname to IP address mappings. We are going to create an A record on DC-1 for "mainframe" and have it point to DC-1's private IP address. If we try to ping mainframe without setting the DNS record it will not work. When we ping "mainframe" Client-1 is checking the DNS cache, checking its local host file and checking the DNS server. To create an A-record go to the AD->Tools->DNS->DC-1->Forward lookup zones->TristanDomain.com-> right click and create a new A record, title it mainframe. An A record is hostname to ip address mapping. If we go back to the client machine and ping mainframe we will get a reply. 
</p>
<br />

<p>
<img src="https://user-images.githubusercontent.com/121250918/210034339-ae9400fd-083a-4ca4-855b-1316b9938c76.png" height="80%" width="80%"/>
</p>
<img src="https://user-images.githubusercontent.com/121250918/210034345-c945a461-85da-4e3a-bb66-808dc2561d9d.png" height="80%" width="80%"/>
<p>
Now we will change the record address of "mainframe" to 8.8.8.8 if we go back to the client machine it will still ping the former address even though we have changed it. That is because we have to flush the DNS with the command ipconfig /flushdns. That will clear the DNS cache, when we attempt to ping mainframe again the address of the new record will show. 
</p>
<br />
<img src="![image](https://user-images.githubusercontent.com/121250918/210034519-62420bdf-30ac-4ed6-98ec-04246c48483a.png" height="80%" width="80%"/>
</p>
<img src="https://user-images.githubusercontent.com/121250918/210034355-4688870b-44ea-43a9-9703-1aba4a039fd1.png" height="80%" width="80%"/>
</p>
<p>
Finally to complete this we will configure a CNAME record that points the host "search" to "www.google.com" If we ping "search" ping will not be able to find the host. we have to go back into the DNS tool on DC-1 and create the CNAME record "search". Once we create the CNAME record is created and we ping "search" it will resolve to www.google.com.
</p>
<br />
<p>
<img src="https://user-images.githubusercontent.com/121250918/210034358-26dc6bf2-aa91-4a89-a566-a9380dc7394c.png" height="80%" width="80%"/>
</p>
<img src="https://user-images.githubusercontent.com/121250918/210034364-c9c92fef-402a-403e-bcd5-56b560630cf0.png" height="80%" width="80%"/>
<p>
