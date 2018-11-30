


## Worklist

- [x] Get command line build working
- [ ] Command line publish - hints at http://www.dotnetbull.com/2018/09/build-publish-web-app-msbuild-command-line.html
- [ ] Dockerfile build
- [ ] ConfigurationBuilder for DB string
- [ ] Kubernetes yaml


## Steps

```powershell
msbuild MyCompany.Visitors.Server.sln /t:clean /p:Configuration=Release
msbuild MyCompany.Visitors.Server.sln /t:rebuild /p:Configuration=Release


docker build . -t ff


```