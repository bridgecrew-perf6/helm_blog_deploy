# helm chart使用

## 发布一个主版本v1

1. 查看版本的模板

   ```
   helm template v1 -n slcnx-prod --create-namespace https://github.com/slcnx/helm_blog_deploy
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

