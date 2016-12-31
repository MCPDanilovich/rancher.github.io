---
title: Windows in Rancher
layout: rancher-default-v1.3
version: v1.3
lang: en
---

## Windows (Experimental)
---

To deploy Windows in Rancher, you'll first need to create a new [environment]({{site.baseurl}}/rancher/{{page.version}}/{{page.lang}}/environments/) that has an [environment template]({{site.baseurl}}/rancher/{{page.version}}/{{page.lang}}/environments/#what-is-an-environment-template) with the container orchestration set as **Windows**.

Currently, Rancher only supports creating containers on specific hosts. Most of the other features in Cattle that may appear are currently not supported (e.g. service discovery, healthcheck, meta data, DNS, load balancer).

> **Note:** There is a default Windows template available. If you try to create your own Windows template, you will need to disable all other infrastructure services as they are currently not compatible with Windows.

### Creating a Windows Environment

In the dropdown of environments, click on the **Manage Environments**. To create a new environment, click on **Add Environment**, provide a **Name**, **Description** (Optional), and select an environment template that has Windows as the orchestration. If [access control]({{site.baseurl}}/rancher/{{page.version}}/{{page.lang}}/configuration/access-control/) is turned on, you can [add members]({{site.baseurl}}/rancher/{{page.version}}/{{page.lang}}/environments/#editing-members) and select their [membership role]({{site.baseurl}}/rancher/{{page.version}}/{{page.lang}}/environments/#membership-roles). Anyone added to the membership list would have access to your environment.

After a Windows environment has been created, you can navigate to the environment by either selecting the name of the environment in the environment's dropdown in the upper left hand corner or by selecting **Switch to this Environment** in the specific environment's drop down.

> **Note:** As Rancher adds support for multiple container orchestration frameworks, Rancher currently does not support the ability to switch between environments that already have services running in it.

### Windows hosts

In order to add a host into Windows, you'll need to prepare a host running [Windows Server 2016 with Docker](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/index) installed.

In the **Infrastructure** tab, you will get a custom command to launch the Rancher agent container. Launch this `rancher/agent` container by following the directions to start containers in Windows.

On the hosts, the agent binary will be download to a folder called `C:/Program Files/rancher` and agent logs will be found at `C:/ProgramData/rancher/agent.log`.

### Networking in Windows

By default, we support NAT and transparent [networking](https://docs.microsoft.com/en-us/virtualization/windowscontainers/manage-containers/container-networking).

Currently, the default _Windows_ environment template supports a transparent network named `transparent`. If you create a network with a different name, you will need to create a new environment template with _Windows_ as the container orchestration. After selecting _Windows_, you can click on **Edit Config** to change the name of the transparent network. After creating the updated environment template, you can create a new environment that will support the newly named transparent network.
 