# Push Notifications

We use Azure Push Notifications service to send notifications to users apple devices (NotificationsId stored at ClientAccountService.Db.ClientPersonalInfoConnString table, Pk=Trader, Rk=ClientId)

To test from Azure Portal go to Test Send tab at Notification Hub used to send notifications, choose Apple at Platforms, type your NotificationsId from Azure Table above and click Send, you should receive message in mobile application.

As far as each certificate has expiration date we need to update it periodicaly.

Steps to update (there are original source to [Create Certificate signing request](https://help.apple.com/developer-account/#/devbfa00fef7) and [Sign](https://customersupport.doubledutch.me/hc/en-us/articles/229495568-iOS-How-to-Create-a-Push-Notification-Certificate)):

* Create Certificate signing request
  * Launch Keychain Access (for MacOS)
  * Choose Keychain Access > Certificate Assistant > Request a Certificate from a Certificate Authority.
  * In the Certificate Assistant dialog, enter an email address and Common Name fields (email address should be valid email of Apple Developer Portal user)
  * Choose “Saved to disk”, and click Continue.

* Sign Certificate
  * Go to https://developer.apple.com/programs/
  * Click on 'Certificates, Identifiers & Profiles'.
  * Select 'Identifiers' and click on our application name (Lykke Wallet)
  * Scroll down the page to "Push Notifications" and click 'Configure'.
  * A pop-up window will appear. Click on 'Create Certificate' under Production SSL Certificate.
  * Click 'Choose File' and select the CSR file we are created in Keychain programm and click on 'Continue'.
  * Your certificate is ready for download. Click on 'Download'.

* Export Certificate
  * Click on certificate file we are downloaded at developer.apple.com (.cer file), it will trigger Keychain Access to open.
  * To find the certificate in Keychain Access, you can use the Search field in the top-right of the dialog window. Type in the Bundle ID of the App ID. You can now confirm that the Push Certificate was correctly created, is valid, and has an associated private key.
  * Right-click on the certificate to show the contextual menu. In the menu that appears, select Export: "Apple Push Services...” (to unselect it in the list click somewhere below the certificate)

* Upload Certificate
  * To upload the certificate at Azure Portal go to Apple (APNS) tab at Notification Hub used to send notifications, click on Upload Certificate select file (.p12), type password and click Save
