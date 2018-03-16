# Installation command line options

Table below contains all the possible charts configurations that can be supplied to `helm install` command using the `--set` flags

| Parameter                                    | Description                                                                  | Default                                                           |
| ---                                          | ---                                                                          | ---                                                               |
| global.hosts.domain                          | Domain name that will be used for all publicly exposed services              | Required                                                          |
| global.hosts.https                           | Serve over https                                                             | true                                                              |
| global.psql.host                             | Global hostname of an external psql, overrides subcharts' psql configuration | Optional                                                          |
| global.psql.password.secret                  | Global name of the secret containing the psql password                       | Optional                                                          |
| global.psql.password.key                     | Key pointing to the psql password in the psql secret                         | Optional                                                          |
| nginx.replicaCount                           | Number of replicas                                                           | 1                                                                 |
| nginx.LoadBalancerIp                         | IP of the external load balancer                                             | Required                                                          |
| nginx.images.defaultbackend.repository       | Default backend that nginx routes to eg: 404                                 | gcr.io/google_containers/defaultbackend                           |
| nginx.images.defaultbackend.tag              | dafault backend image tag                                                    | 1.4                                                               |
| nginx.images.defaultbackend.pullPolicy       | default backend pull policy                                                  | IfNotPresent                                                      |
| nginx.images.nginxIngress.repository         | nginx repository                                                             | quay.io/kubernetes-ingress-controller/nginx-ingress-controller    |
| nginx.images.nginxIngress.tag                | nginx image tag                                                              | 0.9.0                                                             |
| nginx.images.nginxIngress.pullPolicy         | nginx image pull policy                                                      | IfNotPresent                                                      |
| nginx.service.name                           | nginx service name                                                           | nginx                                                             |
| nginx.service.type                           | nginx service type                                                           | LoadBalancer                                                      |
| nginx.service.ports                          | nginx service ports                                                          | [{"http": 80}, {"https": 443}, {"ssh": 22}]                       |
| nginx.serviceAccount.autoGenerate            | Whether chart should generate service account for RBAC                       | true                                                              |
| nginx.serviceAccount.name                    | Service account name                                                         | default                                                           |
| nginx.proxyConnectTimeout                    | Defines a timeout for establishing a connection                              | 15                                                                |
| nginx.proxyReadTimeout                       | Defines a timeout for reading a response                                     | 600                                                               |
| nginx.proxySendTimeout                       | Sets a timeout for transmitting a request                                    | 600                                                               |
| nginx.proxyBodySize                          | body size                                                                    | 512m                                                              |
| nginx.hstsIncludeSubdomains                  | set HSTS for all subdomains                                                  | false                                                             |
| nginx.serverNameHashBucketSize               | Sets the bucket size for the server names hash tables                        | 256                                                               |
| nginx.global.hosts.domain                    | Domain name                                                                  | example.local                                                     |
| nginx.global.hosts.hostSuffix                |                                                                              | Undefined by default                                              |
| nginx.global.hosts.https                     | True if nginx will serve over https                                          | false                                                             |
| nginx.global.hosts.gitlab.serviceName        | Gitlab service name                                                          | unicorn                                                           |
| nginx.global.hosts.gitlab.servicePort        | Gitlab service port name                                                     | workhorse                                                         |
| nginx.global.hosts.registry.serviceName      | Registry service name                                                        | registry                                                          |
| nginx.global.hosts.registry.servicePort      | Registry port name                                                           | registry                                                          |
| nginx.global.hosts.minio.serviceName         | Minio service name                                                           | minio-svc                                                         |
| nginx.global.hosts.minio.servicePort         | Minio port name                                                              | service                                                           |
| nginx.shell.name                             | Shell service name                                                           | gitlab-shell                                                      |
| nginx.shell.port                             | Shell port name                                                              | ssh                                                               |
| nginx.ingress.enabled                        | Enable ingress                                                               | true                                                              |
| nginx.ingress.acme                           | Enable lets encrypt via kube-lego                                            | true                                                              |
| nginx.ingress.hosts                          | Hosts ingress listens to                                                     | Empty array                                                       |
| nginx.ingress.annotations                    | Annotations                                                                  | Undefined by default                                              |
| nginx.ingress.tls                            | Tls certificates (custom)                                                    | Undefined by default                                              |
| redis.image.repository                       | Redis image repository                                                       | redis                                                             |
| redis.image.tag                              | Redis image tag                                                              | 3.2.5                                                             |
| redis.image.pullPolicy                       | Redis image pull policy                                                      | IfNotPresent                                                      |
| redis.service.name                           | Redis service name                                                           | redis                                                             |
| redis.service.type                           | Redis service type                                                           | ClusterIP                                                         |
| redis.service.externalPort                   | Redis internal port                                                          | 6379                                                              |
| redis.service.internalPort                   | Redis exposed port                                                           | 6379                                                              |
| redis.service.clusterIP                      | Cluster IP                                                                   | 0.0.0.0                                                           |
| redis.replicas                               | Number of replicas                                                           | 1                                                                 |
| redis.enabled                                | Enable flag for the chart                                                    | true                                                              |
| redis.timeout                                | Timeout in seconds                                                           | 60                                                                |
| redis.tcpKeepalive                           | Keep alive in seconds                                                        | 300                                                               |
| redis.loglevel                               | Log verbosity                                                                | notice                                                            |
| redis.password.secret                        | Secret name                                                                  | gitlab-redis                                                      |
| redis.password.key                           | Key to password in the secret                                                | redis-password                                                    |
| redis.persistence.enabled                    | Enable persistence flag                                                      | true                                                              |
| redis.persistence.accessMode                 | Redis access mode                                                            | ReadWriteOnce                                                     |
| redis.persistence.size                       | Size of volume needed for redis persistence                                  | 5Gi                                                               |
| redis.persistence.subPath                    | Subpath to mount persistence volume at                                       |                                                                   |
| registry.enabled                             | Enable registry flag                                                         | true                                                              |
| registry.httpSecret                          | Https secret                                                                 |                                                                   |
| registry.authEndpoint                        | Auth endpoint                                                                | Undefined by default                                              |
| registry.tokenService                        | JWT token service                                                            | container_registry                                                |
| registry.tokenIssuer                         | JWT token issuer                                                             | gitlab-issuer                                                     |
| registry.certificate.secret                  | JWT certificate                                                              | gitlab-registry                                                   |
| registry.certificate.key                     | JWT certificate private key                                                  | registry-auth.crt                                                 |
| registry.replicas                            | Number of replicas                                                           | 1                                                                 |
| registry.minio.enabled                       | Enable minio flag                                                            | true                                                              |
| registry.minio.bucket                        | Minio registry bucket name                                                   | registry                                                          |
| registry.minio.credentials.secret            | Secret containing minio credentials                                          | gitlab-minio                                                      |
| minio.image                                  | Minio image                                                                  | minio/minio                                                       |
| minio.imageTag                               | Minio image tag                                                              | RELEASE.2017-12-28T01-21-00Z                                      |
| minio.imagePullPolicy                        | Minio image pull policy                                                      | Always                                                            |
| minio.enabled                                | Minio enable flag                                                            | true                                                              |
| minio.credentials.secret                     | Minio credentials secret                                                     | gitlab-minio                                                      |
| minio.mountPath                              | Minio config file mount path                                                 | /export                                                           |
| minio.replicas                               | Minio number of replicas                                                     | 4                                                                 |
| minio.persistence.enabled                    | Minio enable persistence flag                                                | true                                                              |
| minio.persistence.accessMode                 | Minio persistence access mode                                                | ReadWriteOnce                                                     |
| minio.persistence.size                       | Minio persistence volume size                                                | 10Gi                                                              |
| minio.persistence.subPath                    | Minio persistence volume mount path                                          |                                                                   |
| minio.serviceType                            | Minio service type                                                           | ClusterIP                                                         |
| minio.servicePort                            | Minio service port                                                           | 9000                                                              |
| minio.resources.requests.memory              | Minio minimum memory requested                                               | 256Mi                                                             |
| minio.resources.requests.cpu                 | Minio minimum cpu requested                                                  | 250m                                                              |
| minio.defaultBuckets                         | Minio default buckets                                                        | [{"name": "registry"}]                                            |
| minio.minioConfig.region                     | Minio region                                                                 | us-east-1                                                         |
| minio.minioConfig.browser                    | Minio browser flag                                                           | on                                                                |
| minio.minioConfig.domain                     | Minio domain                                                                 |                                                                   |
| gitlab.gitaly.replicaCount                   | Gitaly replicas                                                              | 1                                                                 |
| gitlab.gitaly.image.repository               | Gitaly image repository                                                      | registry.gitlab.com/gitlab-org/build/cng/gitaly                   |
| gitlab.gitaly.image.tag                      | Gitaly image tag                                                             | latest                                                            |
| gitlab.gitaly.image.pullPolicy               | Gitaly image pull policy                                                     | Always                                                            |
| gitlab.gitaly.service.name                   | Gitaly service name                                                          | gitaly                                                            |
| gitlab.gitaly.service.type                   | Gitaly service type                                                          | ClusterIP                                                         |
| gitlab.gitaly.service.externalPort           | Gitaly service exposed port                                                  | 8075                                                              |
| gitlab.gitaly.service.internalPort           | Gitaly internal port                                                         | 8075                                                              |
| gitlab.gitaly.enabled                        | Gitaly enable flag                                                           | true                                                              |
| gitlab.gitaly.serviceName                    | Gitaly service name                                                          | gitaly                                                            |
| gitlab.gitaly.authToken.secret               | Gitaly secret name                                                           | gitaly-secret                                                     |
| gitlab.gitaly.authToken.key                  | Key to gitaly token in the secret                                            | token                                                             |
| gitlab.gitaly.redis.password.secret          | Redis secret containing redis password                                       | gitlab-redis                                                      |
| gitlab.gitaly.redis.password.key             | Key to redis password in redis secret                                        | redis-password                                                    |
| gitlab.gitaly.shell.authToken.secret         | Shell secret                                                                 | gitlab-shell-secret                                               |
| gitlab.gitaly.shell.authToken.key            | Shell key                                                                    | secret                                                            |
| gitlab.gitaly.persistence.enabled            | Gitaly enable persistence flag                                               | true                                                              |
| gitlab.gitaly.persistence.accessMode         | Gitaly persistence access mode                                               | ReadWriteOnce                                                     |
| gitlab.gitaly.persistence.size               | Gitaly persistence volume size                                               | 50Gi                                                              |
| gitlab.gitaly.persistence.subPath            | Gitaly persistence volume mount path                                         |                                                                   |
| gitlab.gitlab-shell.replicaCount             | Shell replicas                                                               | 1                                                                 |
| gitlab.gitlab-shell.image.repository         | Shell image repository                                                       | registry.gitlab.com/gitlab-org/build/cng/gitlab-shell             |
| gitlab.gitlab-shell.image.tag                | Shell image tag                                                              | latest                                                            |
| gitlab.gitlab-shell.image.pullPolicy         | Shell image pull policy                                                      | Always                                                            |
| gitlab.gitlab-shell.service.name             | Shell service name                                                           | gitlab-shell                                                      |
| gitlab.gitlab-shell.service.type             | Shell service type                                                           | ClusterIP                                                         |
| gitlab.gitlab-shell.service.externalPort     | Shell exposed port                                                           | 22                                                                |
| gitlab.gitlab-shell.service.internalPort     | Shell internal port                                                          | 22                                                                |
| gitlab.gitlab-shell.enabled                  | Shell enable flag                                                            | true                                                              |
| gitlab.gitlab-shell.authToken.secret         | Shell auth secret                                                            | gitlab-shell-secret                                               |
| gitlab.gitlab-shell.authToken.key            | Shell auth secret key                                                        | secret                                                            |
| gitlab.gitlab-shell.unicorn.serviceName      | Unicorn service name                                                         | unicorn                                                           |
| gitlab.gitlab-shell.redis.serviceName        | Redis service name                                                           | redis                                                             |
| gitlab.gitlab-shell.redis.password.secret    | Redis secret                                                                 | gitlab-redis                                                      |
| gitlab.gitlab-shell.redis.password.key       | Key to redis password in redis secret                                        | redis-password                                                    |
| gitlab.omnibus.replicaCount                  | Omnibus replicas                                                             | 1                                                                 |
| gitlab.omnibus.image.repository              | Omnibus image repository                                                     | gitlab/gitlab-ee                                                  |
| gitlab.omnibus.image.tag                     | Omnibus image tag                                                            | nightly                                                           |
| gitlab.omnibus.image.pullPolicy              | Omnibus image pull policy                                                    | Always                                                            |
| gitlab.omnibus.service.name                  | Omnibus service name                                                         | omnibus                                                           |
| gitlab.omnibus.service.type                  | Omnibus service type                                                         | ClusterIP                                                         |
| gitlab.omnibus.service.clusterIP             | Omnibus cluster IP                                                           | 0.0.0.0                                                           |
| gitlab.omnibus.service.ports.psql            | Omnibus psql port                                                            | 5432                                                              |
| gitlab.omnibus.enabled                       | Omnibus enable flag                                                          | true                                                              |
| gitlab.omnibus.external_url                  | Omnibus external url                                                         | http://gitlab.example.local                                       |
| gitlab.omnibus.trusted_proxies               |                                                                              | ["127.0.0.1/24", "10.0.0.0/8", "172.16.0.0/12", "192.168.0.0/16"] |
| gitlab.omnibus.redis.serviceName             | Redis service name                                                           | redis                                                             |
| gitlab.omnibus.redis.password.secret         | Redis secret                                                                 | gitlab-redis                                                      |
| gitlab.omnibus.redis.password.key            | Key to redis password in redis secret                                        | redis-password                                                    |
| gitlab.omnibus.psql.shared_buffers           | Size of psql shared buffers                                                  | 1MB                                                               |
| gitlab.omnibus.psql.password.secret          | Secret containing psql password                                              | gitlab-postgres                                                   |
| gitlab.omnibus.psql.password.key             | Key to psql password in psql secret                                          | psql-password                                                     |
| gitlab.omnibus.psql.persistence.enabled      | psql persistence enabled flag                                                | true                                                              |
| gitlab.omnibus.psql.persistence.accessMode   | psql persistence access mode                                                 | ReadWriteOnce                                                     |
| gitlab.omnibus.psql.persistence.size         | psql persistence volume size                                                 | 10Gi                                                              |
| gitlab.omnibus.psql.persistence.subPath      | psql persistence volume mountpath                                            |                                                                   |
| gitlab.sidekiq.image.repository              | Sidekiq image repository                                                     | registry.gitlab.com/gitlab-org/build/cng/gitlab-sidekiq           |
| gitlab.sidekiq.image.tag                     | Sidekiq image tag                                                            | latest                                                            |
| gitlab.sidekiq.image.pullPolicy              | Sidekiq image pull policy                                                    | Always                                                            |
| gitlab.sidekiq.enabled                       | Sidekiq enabled flag                                                         | true                                                              |
| gitlab.sidekiq.redis.serviceName             | Redis service name                                                           | redis                                                             |
| gitlab.sidekiq.redis.password.secret         | Redis secret                                                                 | gitlab-redis                                                      |
| gitlab.sidekiq.redis.password.key            | Key to redis password in redis secret                                        | redis-password                                                    |
| gitlab.sidekiq.psql.serviceName              | psql service name                                                            | omnibus                                                           |
| gitlab.sidekiq.psql.password.secret          | psql password secret                                                         | gitlab-postgres                                                   |
| gitlab.sidekiq.psql.password.key             | key to psql password in psql secret                                          | psql-password                                                     |
| gitlab.sidekiq.gitaly.serviceName            | gitaly service name                                                          | gitaly                                                            |
| gitlab.sidekiq.gitaly.authToken.secret       | gitaly secret                                                                | gitaly-secret                                                     |
| gitlab.sidekiq.gitaly.authToken.key          | key to gitaly token in gitaly secret                                         | token                                                             |
| gitlab.sidekiq.replicas                      | Sidekiq replicas                                                             | 1                                                                 |
| gitlab.sidekiq.railsSecrets.secret           | Secret containing rails secrets.yml                                          | rails-secrets                                                     |
| gitlab.sidekiq.railsSecrets.key              | Key to contents of secrets.yml in rails secret                               | secrets.yml                                                       |
| gitlab.sidekiq.concurrency                   | Sidekiq default concurrency                                                  | 10                                                                |
| gitlab.sidekiq.timeout                       | Sidekiq job timeout                                                          | 5                                                                 |
| gitlab.sidekiq.resources.requests.cpu        | Sidekiq minimum needed cpu                                                   | 100m                                                              |
| gitlab.sidekiq.resources.requests.memory     | Sidekiq minimum needed memory                                                | 600M                                                              |
| gitlab.unicorn.replicaCount                  | Unicorn number of replicas                                                   | 1                                                                 |
| gitlab.unicorn.image.repository              | Unicorn image repository                                                     | registry.gitlab.com/gitlab-org/build/cng/gitlab-unicorn           |
| gitlab.unicorn.image.tag                     | Unicorn image tag                                                            | latest                                                            |
| gitlab.unicorn.image.pullPolicy              | Unicorn image pull policy                                                    | Always                                                            |
| gitlab.unicorn.service.name                  | Unicorn service name                                                         | unicorn                                                           |
| gitlab.unicorn.service.type                  | Unicorn service type                                                         | ClusterIP                                                         |
| gitlab.unicorn.service.externalPort          | Unicorn exposed port                                                         | 8080                                                              |
| gitlab.unicorn.service.internalPort          | Unicorn internal port                                                        | 8080                                                              |
| gitlab.unicorn.service.workhorseExternalPort | Workhorse exposed port                                                       | 8181                                                              |
| gitlab.unicorn.service.workhorseInternalPort | Workhorse internal port                                                      | 8181                                                              |
| gitlab.unicorn.enabled                       | Unicorn enabled flag                                                         | true                                                              |
| gitlab.unicorn.workerProcesses               | Unicorn number of workers                                                    | 2                                                                 |
| gitlab.unicorn.workerTimeout                 | Unicorn worker timeout                                                       | 60                                                                |
| gitlab.unicorn.railsSecrets.secret           | Secret containing rails secrets.yml                                          | rails-secrets                                                     |
| gitlab.unicorn.railsSecrets.key              | Key to contents of secrets.yml in rails secret                               | secrets.yml                                                       |
| gitlab.unicorn.redis.serviceName             | Redis service name                                                           | redis                                                             |
| gitlab.unicorn.redis.password.secret         | Redis secret                                                                 | gitlab-redis                                                      |
| gitlab.unicorn.redis.password.key            | Key to redis password in redis secret                                        | redis-password                                                    |
| gitlab.unicorn.psql.serviceName              | psql service name                                                            | omnibus                                                           |
| gitlab.unicorn.psql.password.secret          | psql secret name                                                             | gitlab-postgres                                                   |
| gitlab.unicorn.psql.password.key             | Key to psql password in psql secret                                          | psql-password                                                     |
| gitlab.unicorn.shell.authToken.secret        | Shell token secret                                                           | gitlab-shell-secret                                               |
| gitlab.unicorn.shell.authToken.key           | Key to shell token in shell secret                                           | secret                                                            |
| gitlab.unicorn.gitaly.serviceName            | Gitaly service name                                                          | gitaly                                                            |
| gitlab.unicorn.gitaly.authToken.secret       | Gitaly secret name                                                           | gitaly-secret                                                     |
| gitlab.unicorn.gitaly.authToken.key          | Key to gitaly token in gitaly secret                                         | token                                                             |
| gitlab.unicorn.registry.api.protocol         | Registry protocol                                                            | http                                                              |
| gitlab.unicorn.registry.api.serviceName      | Registry service name                                                        | registry                                                          |
| gitlab.unicorn.registry.api.port             | Registry port                                                                | 5000                                                              |
| gitlab.unicorn.registry.tokenIssuer          | Registry token issuer                                                        | gitlab-issuer                                                     |
| gitlab.unicorn.registry.certificate.secret   | Registry certificate                                                         | gitlab-registry                                                   |
| gitlab.unicorn.registry.certificate.key      | Registry certificate key                                                     | registry-auth.key                                                 |
| gitlab.unicorn.resources.requests.cpu        | Unicorn minimum cpu                                                          | 200m                                                              |
| gitlab.unicorn.resources.requests.memory     | Unicorn minimum memory                                                       | 1.4G                                                              |
| gitlab.migrations.image.repository           | Migrations image repository                                                  | registry.gitlab.com/gitlab-org/build/cng/gitlab-rails             |
| gitlab.migrations.image.tag                  | Migrations image tag                                                         | latest                                                            |
| gitlab.migrations.image.pullPolicy           | Migrations pull policy                                                       | Always                                                            |
| gitlab.migrations.enabled                    | Migrations enable flag                                                       | true                                                              |
| gitlab.migrations.redis.serviceName          | Redis service name                                                           | redis                                                             |
| gitlab.migrations.redis.password.secret      | Redis secret                                                                 | gitlab-redis                                                      |
| gitlab.migrations.redis.password.key         | Key to redis password in redis secret                                        | redis-password                                                    |
| gitlab.migrations.psql.serviceName           | psql service name                                                            | omnibus                                                           |
| gitlab.migrations.psql.password.secret       | psql secret                                                                  | gitlab-postgres                                                   |
| gitlab.migrations.psql.password.key          | key to psql password in psql secret                                          | psql-password                                                     |
| gitlab.migrations.railsSecrets.secret        | Secret containing rails secrets.yml                                          | rails-secrets                                                     |
| gitlab.migrations.railsSecrets.key           | Key to contents of secrets.yml in rails secret                               | secrets.yml                                                       |
| gitlab.migrations.initialRootPassword        | Password to the gitlab root account                                          | Required                                                          |
