---
title: "Keycloak"
date: 2023-03-15T10:00:00+10:00
image: "images/products/keycloak.png"
layout: product
description: AMI to build pentesting Debian Linux based enviornment.
permalink: "/aws-machine-images/keycloak/"
bodyClass: page-product
weight: 110
---

# Introduction

Keycloak is an open-source identity and access management (IAM) solution that offers centralized authentication, authorization, and user management for applications. It simplifies authentication, access control, and user administration, providing enhanced security and user management features. Keycloak supports Single Sign-On (SSO), identity federation, user registration, role-based access control (RBAC), multi-factor authentication (MFA), and authorization services. It integrates with existing systems, provides an admin console and management APIs, and supports high availability and scalability for large-scale applications. With Keycloak, developers can implement secure and seamless user authentication and access management in their applications.

# Usage Instructions

* SSH into the new instance as the default OS user to perform additional configurations. Check the default user for the Linux distribution here https://github.com/kurianinc/ami-pub/wiki#default-os-users.
  
* To access the Keycloak application from a browser the service must be configured to access via HTTPS using an NGINX reverse-proxy. For this purpose  the NGINX config file is available at the following location that needs to be updated for the subdomain used for accessing Keycloak service:
  * Ubuntu: /etc/nginx/sites-enabled/default
  * Debian: /etc/nginx/sites-enabled/default
  * Red Hat Linux: /etc/nginx/nginx.conf
  * CentOS: /etc/nginx/nginx.conf
  * openSUSE Linux: /etc/nginx/nginx.conf
  * SUSE Linux: /etc/nginx/nginx.conf
  * AlmaLinux: /etc/nginx/nginx.conf
  * Rocky Linux: /etc/nginx/nginx.conf
  * Oracle Linux: /etc/nginx/nginx.conf
  * Amazon Linux: /etc/nginx/nginx.conf
  * Fedora: /etc/nginx/nginx.conf
 
* If you are accessing the Keycloak service using a load balancer and plan to terminate SSL at the LB level, this configuration is not needed. You just need to point the load balancer to the port 8080 on the EC2 node for the subdomain traffic.

* To enable HTTPS you need a subdmain to access the Keycloak service, such as keycloak.yourcompany.com, and an SSL certificate for that. The certificate can be obtained from the free service LetsEncrypt (https://letsencrypt.org/) or be bought from a reputed Certificate Authority (CA) or a self-signed certificate can be generated also.
* Point the subdomain to the EC2 node where the Keycloak service is running by making appropriate changes in the DNS service used. 
* Edit the NGINX config file in the following places:
  * For server configuration for port 80 change server_name to the subdomain.
  * For server configuration for port 443 update certificate information, ssl_certificate and ssl_certificate_key. If you use LetsEncrypt tools this would be updated automatically.
 
* If needed start NGINX service and access Keycloak service using HTTPS, such as https://keycloak.yourcompany.com 
  
# AWS Marketplace Listing

Multiple versions of this AMI are listed in the AWS Marketplace:

*   TBD

