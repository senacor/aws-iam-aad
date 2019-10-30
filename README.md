This code provides automated integration between AWS and Azure for SAML federation between Azure AD and multiple AWS accounts. You can read a detailed explanation about what it does and how it works in following  AWS blog post:

https://aws.amazon.com/blogs/security/how-to-automate-saml-federation-to-multiple-aws-accounts-from-microsoft-azure-active-directory/

The solution is designed to make it easy to manage any number of AWS accounts in a way that integration efforts are not increased with number of accounts.

This solution includes an PowerShell script to automate ongoing changes in AWS that need to be updated in Azure AD, as well as a solution to easily deploy changes in AWS accounts without having to manually login to each account. You can read about details in the blog post.

# Changes in this Fork

## Add support for AWS Landing Zone Solution

It seems that this solution is not build to run as part of the AWS
Landing Zone Solution. What we tried is to integrate it into the inital
Landing Zone script as an Add On. 

Therefore several role settings has to be changes or become redundant to
the AWS Landing Zone original Setup. As well as some of the formatings
in the cloud formation script does not work when running it via the
console. 

## AD login changed

In the original version, the get_aad_access_tokel.ps1 script based on
the authentication with an Azure user. We failed to get this user login
up and running with the right permissions. 

Therefore wh change to the script to a clientID and ClientSecret based
login. To stay compatible with the other scripts just changed the
internal logic to use the azureUser as ClientID and the azurePassword as
ClientSecret. 
