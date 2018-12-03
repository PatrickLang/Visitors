


## Worklist

- [x] Get command line build working
- [x] Command line publish - hints at http://www.dotnetbull.com/2018/09/build-publish-web-app-msbuild-command-line.html
- [x] Dockerfile build
- [ ] ConfigurationBuilder for DB string
  - Switched to .net 4.7.2 and added environmentbuilder
  - Tested a hardcoded DB login, but there's also some identity provider problem:
```none
 Request Id: 83d398ea-301c-49fe-bf6f-c6833b7a1d00
Correlation Id: 9ba254b0-e31a-40f0-bb33-e5dd1b440116
Timestamp: 2018-12-03T00:19:03Z
Message: AADSTS700016: Application with identifier 'https://mycompanyvisitorsweb20170302015428.azurewebsites.net/' was not found in the directory 'mycompanydemo.onmicrosoft.com'. This can happen if the application has not been installed by the administrator of the tenant or consented to by any user in the tenant. You may have sent your authentication request to the wrong tenant
Advanced diagnostics: Enable
If you plan on getting support for an issue, turn this on and try to reproduce the error. This will collect additional information that will help troubleshoot the issue.
```
- [ ] Kubernetes yaml


## Steps

```powershell
Remove-Item -Recurse -Force MyCompany.Visitors.Web\bin\Release\Publish
msbuild MyCompany.Visitors.Server.sln /t:clean /p:Configuration=Release
#msbuild MyCompany.Visitors.Server.sln /t:build /p:Configuration=Release
msbuild MyCompany.Visitors.Server.sln /t:build /p:Configuration=Release /p:PublishProfile=FolderProfile /p:DeployOnBuild=true
cd MyCompany.Visitors.Web

docker build --no-cache -t visitors .
docker run --rm -p 8080:80 -d visitors
```