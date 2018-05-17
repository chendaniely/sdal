Setup instructions for the mac

1.  Plug in the CAC Card Reader
2.  Go to: https://www.centrify.com/express/identity-service/smart-card-download-files/
    - If that link does not work go to: http://www.centrify.com/express/smart-card-form/
    - Fill out form and click Download Now. Don't forget to click the EULA button. 
    - On the  next page download appropriate version for your version of Mac OS (You can check this by selecting About This Mac from the Apple menu). Download for Mac OS 10.12  As of Feb. 14, 2017 it is Centrify 5.3.3.
3.  Open the downloaded file and run the .dmg installation package.
    When installation finishes, you will see the Centrify Express for Smart Card control panel.
4.  Install certificates
    1.  Download the following file: http://iasecontent.disa.mil/pki-pke/Certificates_PKCS7_v5.0u1_DoD.zip
    2.  Unzip the contents of the zip file into a folder
    3.  Double-click each p7b file, launching the KeyChain Access utility and add it to your "login" keychain
5.  Check certificate permissions
    - Check that DOD ROOT CA 2, 3, and 4 are set to TRUST (if there is a small red X logo, it is not trusted) The blue + logo will mean it is set to trusted.
    - Double Click on DoD Root CA 3 (do CA 2 and 4 as well)
    - Click on Trust chervion on left hand side.
    - Use pulldown to set "when to use certificate" to Always Trust
6. Plugging your CAC in for the frist time
    - will ask you for your password and pin a few times, pay attention to the prompt for your PIN, and the prompt to unlock your keychain.
7.  You can test to see if everything is working by going to `pde.army.mil` and seeing if the page loads with your CAC plugged in.

