Out of the box IIS rewrite module is not present in Sitecore docker images (10.0-ltsc2019).

**To install it to specific Sitecore container, the following can be performed**:

1) Download https://download.microsoft.com/download/1/2/8/128E2E22-C1B9-44A4-BE2A-5859ED1D4592/rewrite_amd64_en-US.msi file (parent article: https://www.iis.net/downloads/microsoft/url-rewrite).
2) Copy the file inside the container as it is described here: https://kb.sitecore.net/articles/383441
3) Open Powershell inside the container as it is described here: https://kb.sitecore.net/articles/137733
4) Install the module using Powershell (you must be in the directory where rewrite_amd64_en-US.msi is located):

```powershell
Start-Process msiexec.exe -ArgumentList '/i', 'rewrite_amd64_en-US.msi', '/quiet', '/norestart' -NoNewWindow -Wait
```

**To create an image based on Sitecore CM, the following command can be used:**

```powershell
Get-Content Dockerfile | docker build --build-arg "BASE_IMAGE=scr.sitecore.com/sxp/sitecore-xp1-cm:10.0-ltsc2019" -t spl-cm-with-rewrite-module:10.0-ltsc2019 .
```

**Simple rewrite rule to ensure that the Rewrite module works**:

```xml
<system.webServer>
    <rewrite>
        <rules>
            <rule name="Rewrite from test.aspx to test2.aspx">
                <match url="test.aspx" />
                <action type="Rewrite" url="test2.aspx" />
            </rule>
        </rules>
    </rewrite>
    ...
</system.webServer>
```





