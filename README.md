
## (1). Git Version Control Setup
- ### 1.1 Git repository initialization
I started out by creating a new folder on my windows machine named 'MarketPeak_Ecommerce' after which i initialized it to be a local git repo.

- ### 1.2 Local Website Development
I downloaded the zipped MarketPeak_E-commerce website file from tooplate.com, unzipped it and then moved the files and folders into my local repository.

- ### 1.3 Git commit
I added and committed these changes to git

- ### 1.4 Push to Github
I created a remote repo on Github with exactly the same name and then push the changes in my local repo to the github repo.


## (2). AWS Deployment
- ### 2.1 Setup AWS Instance
I logged into the AWS Management Console and created/launched an instance which i named 'Market-place'
I created and download a key pair in 'pem' format for which i'll use to login(ssh) into my VM from my local machine.
I then connected to the instance using ssh.

- ### 2.2 Clone the repository
I clonned the remote repository from github into my AWS Ubuntu machine using the 'https' method using:

git clone repo-url

- ### 2.3 Install Web Server on The Instance
I installed a web server(apache2) on my instance.

I then checked the service to see if the service was running but it wasn't so i started it using the command:
sudo systemctl start apache2

I also enabled the service so that when the instance is turned off and re-started, it comes up automatically:
sudo systemctl start enable

- ### 2.4 Configure Apache2 For Website
Becuase i understood that in order for me to serve the MarketPeak Ecommerce website from the EC2 Instance, i'll have to 
configure the apache2 to point to the directory on the linux server where the website codes are stored, usually in:
/var/www/html

I had to remove previously existing files and folders in that directorty:
sudo rm -rf /var/www/html/*

Then i had to copy all the file from the MarketPeak_Ecommerce directory into it:
sudo cp -r ~/MarketPeak_Ecommerce/* /var/www/html

I had to reload the apache2 service:
sudo systemctl reload apache2