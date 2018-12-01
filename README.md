


## Worklist

- [x] Get command line build working
- [x] Command line publish - hints at http://www.dotnetbull.com/2018/09/build-publish-web-app-msbuild-command-line.html
- [x] Dockerfile build
- [ ] ConfigurationBuilder for DB string
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