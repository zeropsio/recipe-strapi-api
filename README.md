# Zerops.io x Strapi.io integration

Import script

```yaml
project:
  name: foobar-prod
  tags:
    - prod
    - foobar
services:
  - hostname: storage
    type: object-storage
    objectStorageSize: 10
    priority: 100

  - hostname: db
    type: postgresql@12
    mode: HA
    priority: 100

  - hostname: api
    type: nodejs@16
    buildFromGit: https://github.com/zeropsio/recipe-strapi-api
    enableSubdomainAccess: true
    envVariables:
      ADMIN_JWT_SECRET: 1tUoMgit3aFh41KfDXUmnw==
      JWT_SECRET: pL3JDJtTg/7qsQ9BiuJzJQ==
      API_TOKEN_SALT: NSrsf0VO1mZzh21JWEB4fg==
      APP_KEYS: G7lIC0XJ5gQvuF5Rx3jULg==,RmKy61asV1fS/m8t8RX37Q==,525oWc3F7n6KuvCX3NhOvg==,i3GE/1RDvNaR+IpXHwoeeg==
      NODE_ENV: production
      HOME: "/"
      DATABASE_PASSWORD: ${db_password}
      S3_ACCESS_KEY_ID: ${storage_accessKeyId}
      S3_ACCESS_SECRET: ${storage_secretAccessKey}
      S3_ENDPOINT_URL: ${storage_apiUrl}
      S3_BUCKET_NAME: ${storage_serviceId|lower}.storage
    ports:
      - port: 1337
        httpSupport: true
    verticalAutoscaling:
      minCpu: 1
      maxCpu: 10
      minRam: 0.5
      maxRam: 0.5
    minContainers: 2
    priority: 50

  # - hostname: app
  #   type: nginx@1.20
  #   envVariables:
  #     API_ENDPOINT: ${api_zeropsSubdomain}
  #   nginxConfig: |
  #     server {
  #         listen 80 default_server;
  #         listen [::]:80 default_server;

  #         server_name _;
  #         root /var/www;

  #         location / {
  #           gzip_static on;
  #           add_header Cache-Control no-cache;
  #           expires 0;
  #             try_files $uri $uri/ /index.html;
  #         }

  #         access_log syslog:server=unix:/dev/log,facility=kern;
  #         error_log syslog:server=unix:/dev/log,facility=kern;
  #     }
  #   minContainers: 2

```

---

# 🚀 Getting started with Strapi

Strapi comes with a full featured [Command Line Interface](https://docs.strapi.io/developer-docs/latest/developer-resources/cli/CLI.html) (CLI) which lets you scaffold and manage your project in seconds.

### `develop`

Start your Strapi application with autoReload enabled. [Learn more](https://docs.strapi.io/developer-docs/latest/developer-resources/cli/CLI.html#strapi-develop)

```
npm run develop
# or
yarn develop
```

### `start`

Start your Strapi application with autoReload disabled. [Learn more](https://docs.strapi.io/developer-docs/latest/developer-resources/cli/CLI.html#strapi-start)

```
npm run start
# or
yarn start
```

### `build`

Build your admin panel. [Learn more](https://docs.strapi.io/developer-docs/latest/developer-resources/cli/CLI.html#strapi-build)

```
npm run build
# or
yarn build
```

## ⚙️ Deployment

Strapi gives you many possible deployment options for your project. Find the one that suits you on the [deployment section of the documentation](https://docs.strapi.io/developer-docs/latest/setup-deployment-guides/deployment.html).

## 📚 Learn more

- [Resource center](https://strapi.io/resource-center) - Strapi resource center.
- [Strapi documentation](https://docs.strapi.io) - Official Strapi documentation.
- [Strapi tutorials](https://strapi.io/tutorials) - List of tutorials made by the core team and the community.
- [Strapi blog](https://docs.strapi.io) - Official Strapi blog containing articles made by the Strapi team and the community.
- [Changelog](https://strapi.io/changelog) - Find out about the Strapi product updates, new features and general improvements.

Feel free to check out the [Strapi GitHub repository](https://github.com/strapi/strapi). Your feedback and contributions are welcome!

## ✨ Community

- [Discord](https://discord.strapi.io) - Come chat with the Strapi community including the core team.
- [Forum](https://forum.strapi.io/) - Place to discuss, ask questions and find answers, show your Strapi project and get feedback or just talk with other Community members.
- [Awesome Strapi](https://github.com/strapi/awesome-strapi) - A curated list of awesome things related to Strapi.

---

<sub>🤫 Psst! [Strapi is hiring](https://strapi.io/careers).</sub>
