# Provision the UAA resource using the XS command line

The code is incorrect because it doesnt take the right instance number into account, hence the port is wrong

1. Logon to the server: `ssh -i openSAPHXE.pem root@34.231.45.95`
2. Then switch user to the HXEADM super user: `su - hxeadm`
3. Then use the  right command line:

`
xs login -a https://ec2-34-231-45-95.compute-1.amazonaws.com:39030 -o HANAExpress -s development -u XSA_DEV -p Passw\!rd --skip-ssl-validation
`

Then create the service instance like this:

`xs create-service xsuaa space openSAPHANA6_00-uaa
`
