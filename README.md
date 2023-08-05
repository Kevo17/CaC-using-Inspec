<h1>CaC using Inspec </h1>


<h2>Description</h2>
This lab focuses on leveraging InSpec, a powerful open-source framework, to implement Compliance as Code practices. Compliance as Code allows organizations to define, test, and enforce regulatory and security compliance requirements through automated and auditable code-based policies.
<br />


<h2>Languages and Utilities Used</h2>

- <b>Inspec</b>
- <b>JSON</b>
- <b>GitLab</b>

<h2>Environments Used </h2>

- <b>Windows 11</b>
- <b>Linux</b> 

<h2>Program walk-through:</h2>

Download the Inspec debian package from the InSpec website: <br/>
```
wget https://packages.chef.io/files/stable/inspec/4.37.8/ubuntu/18.04/inspec_4.37.8-1_amd64.deb
```
<br/>
 
<p align="center">
<img src="https://i.imgur.com/XOM7Ast.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

Install the downloaded package: <br/>
```
dpkg -i inspec_4.37.8-1_amd64.deb
``` 
<p align="center">
<img src="https://i.imgur.com/w2W22hz.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

We have successfully installed the Inspec tool, let’s explore the functionality it provides us: <br/>
```
inspec --help
``` 
<p align="center">
<img src="https://i.imgur.com/I1eiE5R.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

Let’s try to check whether our servers follow the linux-baseline best practices. We will be using the Dev-Sec’s linux-baseline Inspec profile. Before executing the profile, we need to run the below command: <br/>
```
echo "StrictHostKeyChecking accept-new" >> ~/.ssh/config
``` 
<p align="center">
<img src="https://i.imgur.com/Ya09I4Q.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

Let’s run the Inspec against the production server: <br/>
```
inspec exec https://github.com/dev-sec/linux-baseline -t ssh://root@prod-rcgsg0ei -i ~/.ssh/id_rsa --chef-license accept<br/>
``` 
<p align="center">
<img src="https://i.imgur.com/xnId0VP.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

Get priv key: <br/>
- cat /root/.ssh/id_rsa<br />
 
<p align="center">
<img src="https://i.imgur.com/JOSFBPX.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />


Add the following key/value pair in the Varible section of the GitLab environment: <br/>
 
<p align="center">
<img src="https://i.imgur.com/FnSbOnk.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
<img src="https://i.imgur.com/BNzp7BJ.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

Use hysnsec/inspec docker image to perform continuous compliance scanning with our production server and embed it as part of the prod stage with job name as inspec: <br/>
 
<p align="center">
<img src="https://i.imgur.com/0URcS3L.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>
<br /> 
Results: <br />
<p align="center">
<img src="https://i.imgur.com/R4lg95k.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
