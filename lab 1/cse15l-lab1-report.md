**CSE 15L lab 1 report**

Alex Zhang

For this lab, we are supposed to learn about how to log into a server and run some commands using ssh.

Going into part 2 of the lab we may run into some troubles. You have to follow the instructions on how to reset your password. The first time I reset my password to the same password, and it didn’t work for the whole lab period. Later in the day I tried it again and resetted all my passwords to a different password which finally worked, at the cost of changing my ucsd password as well.

Picture below is what you should see when you finish part 3, which is simply installing VS code. I have VS code already installed, but if not, just follow the instructions and download from the link provided. 
![Image](CSE%2015L%20lab%201%20vscode.png)

![Image](CSE%2015l%20lab%201%20pic%201.png)

Picture above is part 4. This is where most people run into problems with the passwords during log in. I didn’t get it to work during lab hours, but it eventually worked by the end of the day. Some people got it working in 5 minutes, don’t know why.
In this part, you basically use the ssh command to connect to a server. If you have the right password and username, you should be able to log in. (Don’t copy exactly from lab instructions because that is not your username).

![Image](cse%2015l%20lab%201%20pic%202.png)
This picture shows part 5, which is trying some commands while you are on the server. You should try out some of the suggested commands like ls that list all the files in your current directory. I also used pwd to print my current working directory. At the bottom you see cp to copy hello.txt to my directory using “~” and I am able to print hello.txt with the cat command.

![Image](cse%2015l%20lab%201%20pic%203.png)
Step 6 is where it gets a little more complicated. First you need to make sure you are logged out using the “exit” command. When you are logged out, you are asked to create a java file called WhereAmI.java with the code provided in the instructions. I created a new folder for cse15l and created the file there. Then you are supposed to test the code locally, which I had an error. Now you will use the “scp'' command to copy this file onto your directory on the server. Provide the file name and where you want to put it then enter your password. Then you have to log in once again to run the code on the server which will show where you are on the server.
![Image](cse%2015l%20lab%201%20pic%204.png)
Step 7 you are supposed to set up a ssh key to log in quickly without having to type your password every time you use ssh or scp. You use the command ssh-keygen(no space) to get a key. Then you log in to the server and type mkdir .ssh and log out. Locally you use scp to copy the public key up to the server in your account. Enter password again and it should work now.
![Image](cse%2015l%20lab%201%20pic%205.png)
Part 8 I accidentally used scp while on the server, it gave me some errors and scared me, so be sure to use scp while on the client. I made a local edit in the WhereAmI file and used scp to upload it again without having to enter a password. Then I use ssh but with “ls” following to see the files without having to actually log in. Then I logged in and did the javac and java commands on WhereAmI using a “;” without having to write two lines. At the bottom, you can see the local edit.
