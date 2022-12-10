#  Implementation of simple TO-DO Application on MERN (MongoDB-ExpressJS-ReactJS-NodeJS) webstack in AWS

## AWS account set up and provisioning Ubuntu Server

### Steps

1. Create a Security group for the EC2 instance defining desired inbound rules from target IPs
     ![Security group for EC2](./images/security-group.png)

2. Launched EC2 instance, selecting an Ubuntu free tier

3. Made necessary configurations (Enabling Public IP, Assigning security group created in 2, creating key)-value pair) needed to run the EC2 instance.
    ![EC2 instance](./images/EC2-instance.png)

4. SSH-ed into the EC2 instance using the windows terminal
    - Downloaded the Windows SSH from the windows store
    - Followed steps in [ARTICLE](https://learn.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse?source=recommendations&tabs=powershell) in installing and configuring OpenSSH in windows.
    - The openSSH allows remote access into our EC2 instance from the windows terminal.
    - Followed steps in [OpenSSH key management](https://learn.microsoft.com/en-us/windows-server/administration/openssh/openssh_keymanagement) to create key authentication management for OpenSSH in windows
    ![SSH-ing into server](./images/SSH-via-windows-terminal.png)

5. `sudo apt update` -- Updating packages in the package manager



## Installing Node and NPM on Ubuntu Server

### Steps

1. `curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -` -- Getting location of Node.js software from [Ubuntu repository](https://github.com/nodesource/distributions#deb)

2. `sudo apt-get install -y nodejs` -- Installing Node.js and [Node package manager (NPM)](https://www.npmjs.com/)

3. `node -v` -- Verifying node installation

4. `npm -v` -- Verifying npm installation

5. `mkdir` -- Creating project directory

6. `npm init` -- Initializing project directory to create *package.json*

    ![Initialing Node Packet Management](./images/initializing-npm.PNG)



## Installing ExpressJS on Ubuntu Server


### Steps

1. `npm install express` -- Installing express using npm

2. `touch index.js` -- Creating an *index.js* file

3. `npm install dotenv` -- Installing dotenv module

4. `vim index.js` -- Populating the *index.js* file, specifying port **5000** as shown below

    ![Populating the index.js file](./images/populating-index-file.PNG)

5. `node index.js` -- Starting server to see if it is running on port 5000

6. *http://3.86.238.24:5000/* -- Accessing the server's public IP address followed by port 5000 in the browser results in webpage displayed like so:

    ![Accessing server's public IP address in browser](./images/brower-content-displayed.PNG)

The Todo application will utilize the standard [HTTP requests methods](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods) to perform: 
    - Create a new task
    - Display list of all tasks
    - Delete a completred task

To perform each of these tasks, I created routes that will define the various endpoints that these To-do tasks will depend on

    `mkdir routes` -- Creating folder **routes** for to define endpoints for the application's tasks.

    `cd routes` -- Chnaging directory to the *routes* folder

    `touch api.js` -- Creating an **api.js** file

    `vim api.js` -- Opening the **api.js** file and populating using the **vi** editor like so:

        ![Populating the *api.js* file](./images/populating-api-file.PNG)

    

## Installing [MongoDB](https://www.mongodb.com/) on the Ubuntu Server and creating a NoSQL database

This procedure allows the creation of models to define the database schema -- database fields where data will be entered.

### Steps

1. `npm install mongoose` -- I installed [mongoose](https://mongoosejs.com/) using NPM for schema and model creation

2. `mkdir models && cd models && touch todo.js` -- Creating a models folder and creating a *todo.js* file inside the **models** folder

3.  `vim todo.js` -- Opening the **todo.js** file and populating using the **vi** editor like so:

        ![Creating schema for database](./images/creating-todo-schema.PNG)

4. `vim api.js` -- I updated the routes in the *api.js* file to make use of the new model like so

        ![Updating routes to make use of created models](./images/updating-routes-to-make-use-new-model.PNG)
