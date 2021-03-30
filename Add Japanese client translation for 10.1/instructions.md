**To install the client translation in 10.1+ to specific Sitecore container, the following can be performed**:

1. Download the archive from dev.sitecore.net to the c:\tools folder of the container. 
2. Extract the archive using Powershell to the App_Data folder of the site.

After creating the container, Japanese language needs to be added using control panel.

**To create an image based on Sitecore XP0, the following command can be used:**

```powershell
Get-Content Dockerfile | docker build --build-arg "BASE_IMAGE=scr.sitecore.com/sxp/sitecore-xp0-cm:10.1-ltsc2019" -t spl-xp0-with-jp-lang:10.1-ltsc2019 .
```



