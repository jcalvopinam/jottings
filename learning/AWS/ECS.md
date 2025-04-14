---
title: ECS
date: 2023-05-31
status: wip
tags: cluster, task_definition
---

## Cluster
Es como una red general en la que se encuentran todos nuestros servicios, que a su vez cada servicio ejecutan las tareas que contiene contenedores manejando el tráfico de entrada asignado, un puerto específico y una IP pública que se le asigne de forma automática.

- Create cluster
- Choose `Networking only`
- Cluster name: `aws course`
- Create VPC
- Click on `Create` button

### Create task definition
- Click on `Create new Task Definition`
- Choose `Fargate`
- Task Definition Name: `msvc-user`
- Task Role > IAM Console > filter ECS > AWSServiceRoleForECS > AWS Service 
	- Use Case > Elastic Container Service > Elastic Container Task
- Click on `Next`
- Filter `ECS` > choose AmazonECSTaskExecutionRolePolicy
- Click on `Next`
- Set Role Name: `ECSTaskExecutionRolePolicy`
- Create Role
- Go back to Task Role and choose the role created: `ECSTaskExecutionRolePolicy`
- Operative System Family: `Linux`
- Task size
	- Task memory: `1GB`
	- Task CPU: `0.5 vCPU`
- Add Container
	- Container Name: `msvc-user`
	- Image: `jcalvopinam/user:;1.0.0` // Dockerhub repository
	- Memory Limits (MiB) Soft Limit: `256`
	- Port Mapping: `8001`
	- Environment variables

| key     | Value          |     |
| ------- | -------------- | --- |
| PORT    | 8001           |     |
| DB_HOST | localhost:3306 |     |
| ...     |                |     |
