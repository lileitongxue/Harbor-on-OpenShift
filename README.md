# Harbor-on-OpenShift

1.目前Harbor官网提供helm安装方式，但是要求k8s 1.8+以上版本，因为她们的k8s编排文件是以beta2来写的，其实k8s低版本的也可以安装，(需要自己手动改一下api版本)我是在k8s1.6上安装的。<br>
Harbor官网地址：https://github.com/vmware/harbor/tree/v1.5.0/contrib/helm/harbor <br>

2.安装在openshift上稍微有点不同的是，openshift是以route提供服务的，k8s是以ingress，route是不能配置多个svc的，但是可以配置成相同的hostname名字，不同的path路径<br>

3.安装过程

git clone https://github.com/lileitongxue/Harbor-on-OpenShift.git <br>

oc create -f ./deploy/deploy.yaml <br>

oc create -f ./statefulset/statefulset.yaml <br>

oc create -f ./configmap/cm.yaml <br>

oc create -f ./secret/adminserver.yaml <br>

oc create -f ./secret/jobservice.yaml <br>

oc create -f ./secret/mysql.yaml <br>

oc create -f ./secret/postgresql.yaml <br>

oc create -f ./secret/registry.yaml <br>

oc create -f ./secret/ui.yaml <br>

oc create -f ./svc/svc.yaml <br>

oc create -f ./route/route.yaml <br>

4.目前这几个pod 都没有做数据的持久化，需要自己挂卷，Harbor的版本是v1.5.0，但是镜像是1.4.0的，我是按照git上的来做的，也问过Harbor官网的人。就是这样的。。。。。
