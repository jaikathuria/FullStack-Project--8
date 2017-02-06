# Linux Server Configuration

### Project Overview
 >A baseline installation of a Linux distribution on a virtual machine and prepare it to host web applications, to include installing updates, securing it from a number of attack vectors and installing/configuring web and database servers

### Why this Project?
>A deep understanding of exactly what web applications are doing, how they are hosted, and the interactions between multiple systems are. This project, turns a brand-new, bare bones, Linux server into the secure and efficient web application host that a Data Driven Web Applications Needs.

### Major Keypoints
> i. Deploying a web application to a publicly accessible server.

> ii. Properly securing application ensures, application remains stable and that user’s data is safe.

### Steps Followed to Configur Linux server
#### 1. Create Development Environment Instance.

  * [Create new development environment.](https://www.udacity.com/account#!/development_environmet)

  * Download private key and write down your public IP address.

#### 2. Launch Virtual Machine and SSH into the server.

  * Move private key file into the desired folder.

  * Change the file rights of the key (Only Owner Can Read and Write.):

 ```
     $ chmod 600 /(address_to_private_key)/udacity_key.rsa
 ```

  * SSH into the instance:

  ```
     $ ssh -i /(address_to_private_key)/udacity_key.rsa root@PUBLIC_IP_ADDRESS
  ```

#### 3. Create New User.

  * Add a new user called grader.

  ```
     $ sudo adduser grader
  ```

  * Give sudo access to grader.

  ```
     $ sudo nano /etc/sudoers.d/grader
  ```
    Add the following text to the the newly created file:

  ```
     grader ALL=(ALL:ALL) ALL
  ```
   i. Edit the hosts file :

   ```
      $ sudo nano /etc/hosts
   ```

   ii. Add the host to hosts file :

   ```
      127.0.1.1 ip-XX-XX-XX-XX
   ```

#### 4. Setup SSH keys for grader.

  * On the local system, Go to the directory where you want to save the Key, and run the following command.

    ```
      $ ssh-keygen -t rsa
    ```

    followed by the name of the key. Run the following command to install the generated public key on the server.

    ```
    $ ssh-copy-id grader@XX.XX.XX.XX -i (key_name.pub)
    ```

  * Log into the remote VM as *root* user through ssh and open the following file: `$ cat /.ssh/authorized_keys` , then copy the content of the file at  `$ nano /home/grader/.ssh/authorized_keys` 

  * Now you are able to log into the remote VM through ssh with the following command: `$ ssh -i udacity_key.rsa grader@XX.XX.XX.XX`

Source: [Digital Ocean](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2)
