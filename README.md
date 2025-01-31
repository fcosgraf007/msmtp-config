For those of us having a server at home with a basic home internet connection, the issue is how to easily bypass the problem of having port 25 blocked by our ISP.
To quickly go around it you can setup an msmtp client to login to your personal email to send useful information from your running server.

Requisites:
sudo apt-get install msmtp-mta
Open necessary ports in your firewall for outgoing emails.

Create or edit the config file for msmtp. msmtp will look for a file named .msmtprc in your home folder by default (.file means it is an occult file and wont be displayed with ls unless specified). This file must contain the instructions and your personal credentials so that msmtp can use them to send your ip address to your own email securely with tls. This file creates an "account" readable by msmtp to be used to send email. In this example the password is stored in plain text inside the configuration file so it must be in a secure account only accessible to the owner of the external email service used to send emails. TLS will be enabled.

Be aware that if the information is not correctly typed, msmtp might give you misleading error codes which will make troubleshooting very hard. Check the correct details of our email provider before. An example of this is the real root server of your email provider might not be the .net or .com domain extension but rather a .us or pl or any other extemsion if they have the root email services in a foreign country. Next, create and configure a script to be used by msmtp in your home folder. Install curl if is not installed already.

If problems arise with permissions, make sure to set permissions 600 for your user to the .msmtp file.
