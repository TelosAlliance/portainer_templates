# Portainer Templates

## Scope

Telos Alliance's portainer templates are used to deploy Telos Alliance container products. These templates **SHOULD** only be used as part of the Telos Alliance Container Setup Tool (TACST) or Infinity VIP System.

These templates will not work on other systems. If a container product is being deployed without TACST or VIP please reference the [Docker Compose files](https://github.com/TelosAlliance/portainer_templates) and product specific information.

## What are Portainer templates?

Portainer has an option where you can create predetermined templates to easily deploy containers inside Portainer. The way Telos Alliance has implemented templates is based on docker compose files to bring the containers on line. What determines the containers shown in Portainer and the options for the container are json files.

## How do Portainer templates work

Portainer pulls the templates in over the internet from the Telos Alliance GitHub server for production and the GitLab server for development. Each template file in this project has a unique purpose. The templates a system use can be changed by adjusting the URL in the Portianer UI. The next sections explain the purpose of each template, and the how to change between templates.

Production templates and Compose files are delivered from this public GitHub repository. Changes published to `main` become available to customer systems immediately.

```mermaid
flowchart TD

    subgraph Portainer Templates via UI
    PortUi[Portainer UI]
    PortSet[Settings]
    AppSet[Application settings]
    AppTemp[App Templates]
    SetUrl[Set URL]
    end
    PortUi --> PortSet
    PortSet --> AppSet
    AppSet --> AppTemp
    AppTemp --> SetUrl
    SetUrl --> HUrl

    subgraph Portainer Templates on Portainer start
    StPort[Start Portainer]
    PortAPI[Call Portainer API endpoint]
    PortApiSet[Set TEMPLATES value to URL]
    end
    StPort --> PortAPI
    PortAPI --> PortApiSet
    PortApiSet --> HUrl

    subgraph Git Server
    TempRepo[Templates repository]
    Json1[templates-v3.json]
    Json2[vip-templates-v3.json] 
    HUrl[Hosting URL]
    end
    HUrl --> Json1 & Json2
    Json1 & Json2 --> |templates pull from| TempRepo

    subgraph Portainer&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp
    TempUi[Template UI]
    CompFile[Docker-compose file]
    TempRepo --> TempUi
    TempUi--> |environment variables| CompFile
    end

    RC[Running container]
    CompFile --> |starts| RC
```

### templates-v3.json

templates-v3.json is the standard production template for Telos Alliance Container Setup Tool. Products listed in templates-v3.json are fully released by Telos Alliance. All customers with TACST will get this update as soon as it is on main.

### beta-templates-v3.json (ex internal-templates)

beta-templates-v3.json includes pre-release products, feature updates, and legacy products. It **MUST** only be used under Telos Alliance or authorized partner supervision, not as the default production catalog.

### vip-templates-v3.json

vip-templates-v3.json is the standard production template for VIP Systems. Products listed in vip-templates-v3.json are fully released by Telos Alliance. All customers with VIP systems will get this update as soon as it is on main.

VIP has special templates to support additional VIP Products (Panels, VIP Server, and Dashboard) only available to VIP customers. There are also some special considerations for general products, like VXS, that must be accounted for in VIP system.

## Deployment requirements

Release 1.3.14 targets Docker Engine 28 or later. Updated macvlan Compose files use `interface_name` to assign `eth0` to `telosmacvlan` and `eth1` to `ext1macvlan` where declared, rather than relying on network attachment order. Docker Compose CLI deployments require version 2.36.0 or later; Portainer deployments must also support this Compose attribute. Confirm deployment-tool compatibility before updating a customer system. These assignments remove the need for the previous Docker 27 downgrade workaround.

Legacy v2/internal catalogs are retained but are not part of this v3 promotion. They contain historical Compose references that require separate path validation before use.

## How to change templates in a product

By default products that can use templates have the appropriate template in place when Portainer starts. If the template needs to be changed the steps below can be used on a running system.

1. Log into portainer
1. Select the local instance of portainer
1. Navigate to settings for Portainer
1. Find the app template setting
1. Delete the URL in the app template
1. Copy paste the the the url for app template you want to use into the app template line. The list of app template URLS is below.

    | Template Name | URL |
    |---------------|-----|
    |templates-v3|<https://github.com/TelosAlliance/portainer_templates/raw/main/templates-v3.json>|
    |vip-templates-v3|<https://github.com/TelosAlliance/portainer_templates/raw/main/vip-templates-v3.json> |

1. Press save
1. Navigate to the App Template menu
1. The product list you switched to is now present.

> **WARNING:** Portainer versions 2.18 and earlier require version 2 portainer templates.

>| Template Name | URL |
>|---------------|-----|
>|templates-v2|<https://github.com/TelosAlliance/portainer_templates/raw/main/templates-v2.json>|
>|vip-templates-v2|<https://github.com/TelosAlliance/portainer_templates/raw/main/vip-templates-v2.json> |

## More information

For more information about Telos Alliance Portainer templates please [contact customer support](https://www.telosalliance.com/support-request).