---
title: "Nextcloud: The Ultimate Solution to Replace Google Drive and Others"
date: 2023-09-30T20:00:00+01:00
description: Many of us have turned to giants like Google, however, have you ever wondered if there's a better way to manage your personal data without compromising your privacy ?
menu:
  sidebar:
    name: Private Cloud Drive
    identifier: nextcloud
    parent: raspberry
    weight: 10
---

In today's digital age, the need for secure storage solutions has never been greater.

Many of us have turned to giants like Google Drive or Microsoft OneDrive for their convenience and accessibility.
However, have you ever wondered if there's a better way to manage your personal data without compromising your privacy and flexibility?

In this article, we'll explore why Nextcloud stands as the ideal alternative to replace any drive provider.

## Why Using Drive Solutions Like Google Drive or Microsoft?

Services like Google Drive and Microsoft OneDrive offer unparalleled ease of use when it comes to synchronizing files across multiple devices. This feature ensures that your documents, photos, and other files are always up-to-date and accessible, which is especially valuable for users who need real-time access to their data.

But... Storing your data with big corporations means potentially compromising your privacy, as they may access and use your personal information. This issue has become increasingly significant, especially in the wake of privacy regulations like the General Data Protection Regulation (GDPR).

In recent years, Google has faced legal actions related to its data usage policies. For instance, France's data protection authority, CNIL, issued a significant fine against Google for breaching GDPR regulations, including inadequate information provided to users and lack of valid consent for personalized ads. This condemnation underscores the serious concerns about how Google handles user data.

Pros:
- **Convenience**: Services like Google Drive and Microsoft OneDrive offer seamless synchronization across devices, making it easy to access your files from anywhere.
- **Collaboration**: They provide collaboration features, such as real-time document editing and sharing, which are essential for teamwork.
- **Integration**: Integration with other software and services, such as Google Workspace and Microsoft Office, can enhance productivity.

Cons:
- **Privacy Concerns**: Storing your data with big corporations means potentially compromising your privacy, as they may access and use your personal information.
- **Limited Customization**: These services often lack advanced customization options for users who want more control over their data.
- **Dependency**: Relying on a single provider makes you vulnerable to service outages and changes in terms of service or pricing.

## Using Your Own Drive

Creating your own cloud storage solution may sound like a daunting task, but it's an incredibly exciting endeavor that offers a plethora of benefits. 

First and foremost, it puts you in the driver's seat, giving you full control over your data and privacy. The excitement lies in the freedom to customize your cloud to fit your exact needs, whether it's expanding storage capacity, implementing advanced security measures, or integrating unique features. What makes this journey even more thrilling is the vibrant open-source community that surrounds self-hosted solutions like Nextcloud.

With a global network of enthusiasts developers, these communities are constantly pushing the boundaries of what's possible. They enhance and refine features, improve security, and offer invaluable support. So, if you're a web tinkerer or someone who enjoys the thrill of building and contributing, I invite you to dive into the world of self-hosted solutions and join these open-source projects. **Regardless of your skill level, there's a place for everyone, and your participation can make a real difference in shaping the future of decentralized, secure, and customizable project.**

Advantages:
- **Privacy Control**: Hosting your data on your own infrastructure ensures you have complete control over your data and who can access it.
- **Cost Savings**: Over time, hosting your own cloud storage solution can be cost-effective compared to subscription-based services.
- **Customization**: You can tailor your storage solution to meet your specific needs, including security measures and storage capacity.

Drawbacks:
- **Technical Knowledge**: Setting up and maintaining your own cloud storage solution can be daunting for those without technical expertise.
- **Initial Investment**: There may be an upfront cost for hardware and software, such as a Network Attached Storage (NAS) device and server hosting.
- **Responsibility**: You're responsible for data backups, security, and system updates, which can be time-consuming.

## NextCloud 

{{<img src="/posts/raspberry/nextcloud/nextcloud.png" align="center" >}}

[NextCloud](https://nextcloud.com/) is a self-hosted, open-source cloud storage and collaboration platform that combines the best of both worlds.
It offers the convenience of cloud-based file synchronization and collaboration tools while allowing you to maintain control over your data.

Key Features of Nextcloud:

- **File Storage**: Store, organize, and access your files from any device with ease.
- **Collaboration**: Share files, calendars, contacts, and even host video calls within your Nextcloud instance.
- **Security**: Nextcloud puts a strong emphasis on security, offering features like end-to-end encryption.
- **Customization**: You can extend Nextcloud's functionality through a vast selection of apps and plugins.
- **Self-Hosted**: You have complete ownership and control over your data, ensuring your privacy.

## How to Install Nextcloud with Docker

Setting up Nextcloud with Docker offers a flexible and customizable solution.
Docker allows you to encapsulate Nextcloud and its dependencies into containers, making installation and management straightforward.

### Prerequisites
Ensure you have a server or NAS device capable of running Docker.
Install Docker on your server or NAS. Follow the official Docker documentation for your platform.

### Docker

Utilizing [LinuxServer's](https://www.linuxserver.io/) Docker image is a prudent choice when considering self-hosting solutions like Nextcloud, as it introduces crucial security features that bolster your data protection efforts. One such feature is the implementation of PUID (Process User ID) and PGID (Process Group ID), which allow you to precisely control who has read and write permissions on your system. This fine-grained control ensures that only authorized users or processes can access and modify specific files or directories, reducing the risk of unauthorized access or data breaches. Furthermore, creating a dedicated Linux group with minimal permissions further fortifies your system's security posture, limiting potential vulnerabilities.

Moreover, LinuxServer's Docker image goes the extra mile by providing MODS (Modular Object Detection System), an additional layer that equips your self-hosted environment with an array of tools and expanded capabilities. These tools can enhance your cloud storage solution's functionality, security, and monitoring capabilities.

The folder structure you've outlined provides a clear and organized setup. 

Inside the "nextcloud" directory, you've segmented your components into distinct subdirectories, enhancing manageability.
- The "maria_db" directory likely houses the MariaDB database that Nextcloud relies on to store user data and configurations securely. Separating this component ensures data isolation and efficient database management.
- The "nextcloud_config" directory is likely where you store your Nextcloud configuration files, making it easy to access and modify Nextcloud settings as needed.
- The "docker-compose.yml" file is a pivotal piece of the puzzle, as it orchestrates the entire Nextcloud environment using Docker containers. This file defines how your Nextcloud, MariaDB, and any other required services interact, simplifying deployment and maintenance.
- The ".env" file likely contains environment variables necessary for configuring your Nextcloud and MariaDB containers, streamlining the setup process. 

Altogether, this organized folder structure and setup demonstrate a thoughtful approach to creating and maintaining a robust and secure self-hosted Nextcloud instance on your NAS.

```
nas/
├─ nextcloud/
│  ├─ maria_db/
│  ├─ nextcloud_config/
│  ├─ docker-compose.yml
│  ├─ .env
```

```yml
version: '3.8'

services:
  nextcloud_db:
    image: lscr.io/linuxserver/mariadb:latest
    container_name: nextcloud_db
    restart: unless-stopped
    volumes:
      - ./maria_db:/config
    environment:
      - PUID=1000
      - PGID=100
      - TZ=Etc/UTC
      - MYSQL_ROOT_PASSWORD=$NEXTCLOUD_MYSQL_ROOT_PASSWORD
      - MYSQL_DATABASE=$NEXTCLOUD_MYSQL_DATABASE
      - MYSQL_USER=$NEXTCLOUD_MYSQL_USER
      - MYSQL_PASSWORD=$NEXTCLOUD_MYSQL_PASSWORD

  nextcloud_app:
    image: lscr.io/linuxserver/nextcloud:latest
    restart: unless-stopped
    ports:
      - 8443:443 # Replace 8443 by your custom exposed port
    depends_on:
      nextcloud_db:
        condition: service_started
    volumes:
      - ./nextcloud_config:/config
      - /volume1/cloud:/data # Replace /volume1/cloud to your local cloud path
    environment:
      - PUID=1000
      - PGID=100
      - TZ=Etc/UTC
      - DOCKER_MODS=linuxserver/mods:nextcloud-memories|linuxserver/mods:nextcloud-mediadc
      - MYSQL_HOST=nextcloud_db
      - MYSQL_DATABASE=$NEXTCLOUD_MYSQL_DATABASE
      - MYSQL_USER=$NEXTCLOUD_MYSQL_USER
      - MYSQL_PASSWORD=$NEXTCLOUD_MYSQL_PASSWORD
```

```ini
NEXTCLOUD_MYSQL_DATABASE=nextcloud
NEXTCLOUD_MYSQL_USER=nextcloud
NEXTCLOUD_MYSQL_ROOT_PASSWORD=****************************
NEXTCLOUD_MYSQL_PASSWORD=****************************
```

By effectively using `chmod`, `chown`, and configuring `PUID` and `PGID` in your Docker Compose file, you can maintain a secure and customized environment for your self-hosted services while ensuring that permissions align with your system's requirements.

I recommend establishing a `docker` group on your server and assigning a unique user for each hosted application within this `docker` group. Employ the `chown` command recursively to grant permissions exclusively to each respective user. In the event of a security breach, this approach confines each application within its designated space, mitigating potential issues.

Additionally, you have the option to configure permissions in a more granular manner, such as providing full permissions to the user, read-only access to the group, and no access to others, thereby enhancing security measures.

### Secure Your Instance

Implement security best practices, such as enabling HTTPS with [Let's Encrypt](https://letsencrypt.org/fr/) and configuring user permissions.

Most NAS solutions offer a valuable feature known as a reverse proxy with [Let's Encrypt](https://letsencrypt.org/fr/) SSL/TLS certificates. This functionality is typically included within the NAS configuration portal, simplifying the process of securing web applications and services hosted on the NAS.

In case you haven't set up a reverse proxy on your server, another excellent option is to consider using [Nginx Proxy Manager](https://github.com/NginxProxyManager/nginx-proxy-manager), a notable open-source solution that offers an appealing alternative. This project is well-regarded for its user-friendly approach, providing straightforward and comprehensible documentation. Furthermore, Nginx Proxy Manager can be effortlessly installed using Docker, making it a convenient choice for those seeking a hassle-free way to implement a reverse proxy for their services.

## Conclusion

Nextcloud offers an excellent alternative to commercial cloud storage providers like Google Drive or Microsoft OneDrive.
By self-hosting NextCloud with Docker, you gain full control over your data's privacy and flexibility while enjoying the benefits of a modern cloud collaboration platform.
Take the leap into the world of Nextcloud, and you'll never look back at traditional cloud providers the same way again.
