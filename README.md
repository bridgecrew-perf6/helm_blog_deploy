# 安装helm

[安装helm官方位置](https://helm.sh/docs/intro/install/)

```bash
curl https://baltocdn.com/helm/signing.asc | sudo apt-key add -
sudo apt-get install apt-transport-https --yes
echo "deb https://baltocdn.com/helm/stable/debian/ all main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list
sudo apt-get update
sudo apt-get install helm
```



# helm chart使用

## 添加git仓库

https://github.com/aslafy-z/helm-git

```bash
helm plugin install https://github.com/aslafy-z/helm-git --version 0.11.1
helm repo add slcnx-blog git+ssh://git@github.com/slcnx/helm_blog_deploy@install?ref=main
"slcnx-blog" has been added to your repositories
```

查看版本

```bash
root@mykernel:~# helm repo list
NAME            URL
slcnx-blog      git+ssh://git@github.com/slcnx/helm_blog_deploy@install?ref=main
root@mykernel:~# helm search repo slcnx-blog
NAME                            CHART VERSION   APP VERSION     DESCRIPTION
slcnx-blog/myblog_deploy        0.1.0           1.16.0          A Helm chart for Kubernetes
```

## 发布一个主版本v1

1. 查看版本的模板

   ```
    helm template v1 -n slcnx-prod --create-namespace slcnx-blog/myblog_deploy
   ```

2. 安装

    ```bash
    helm install v1 -n slcnx-prod --create-namespace https://github.com/slcnx/helm_blog_deploy
    ```

## 查看历史

```bash
helm ls -n slcnx-prod 
```

## 更新主版本的补丁

```bash
helm upgrade install  -n slcnx-prod --set image.tag="" https://github.com/slcnx/helm_blog_deploy
```

## 回滚上一个版本

```
helm rollback  -n slcnx-prod v1
```

## 删除主版本v1

```
helm uninstall  -n slcnx-prod v1
```

