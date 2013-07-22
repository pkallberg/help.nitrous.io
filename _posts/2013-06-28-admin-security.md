---
layout: article
title: Security on Nitrous.IO
published: true
categories: [privacy and terms]
---

### Nitrous.IO The Platform & Web Service

Nitrous.IO is a cloud application platform used by software developers and software companies of all sizes to optimize development workflow. Our platform allows developers to focus on development while Nitrous.IO focuses on infrastructure management, development box setup and configuration and stack dissemination amongst teams.

We are dedicated to protecting the security of the development resources that we provide, and protecting the trust of our customers is paramount to our definition of success. We build Nitrous.IO on top of the Nitrous.IO platform, so we are fully aware.

### Reporting a Security Vulnerability

If you discovered a security vulnerability with the system, please [email us immediately](mailto:security@nitrous.io). We will diligently investigate the details of the issue and will work with you to understand the scope of the issue presented. Security is one of our highest priorities and we will always immediately address any security concerns [sent to us](mailto:security@nitrous.io).

Because the security vulernability may affect other users, we ask that you please do not share the issue publicly. We will avoid taking legal action against you or action against your account if you act in the benefit of the privacy of our community.  We appreciate your research for the improvement of the system.

### Security Assessments and Compliance

#### Data Centers / Infrastructure

Nitrous.IO’s physical infrastructure is hosted and managed within Amazon’s secure data centers and utilize the Amazon Web Service (AWS) technology. Amazon continually manages risk and undergoes recurring assessments to ensure compliance with industry standards. Amazon’s data center operations have been accredited under:

* ISO 27001
* SOC 1/SSAE 16/ISAE 3402 (Previously SAS 70 Type II)
* PCI Level 1
* FISMA Moderate
* Sarbanes-Oxley (SOX)
* PCI

We use PCI compliant payment processor Stripe for encrypting and processing credit card payments. Nitrous.IO’s infrastructure provider is PCI Level 1 compliant.

### Physical Security

Nitrous.IO utilizes ISO 27001 and FISMA certified data centers managed by Amazon. Amazon has many years of experience in designing, constructing, and operating large-scale data centers. This experience has been applied to the AWS platform and infrastructure. AWS data centers are housed in nondescript facilities, and critical facilities have extensive setback and military grade perimeter control berms as well as other natural boundary protection. Physical access is strictly controlled both at the perimeter and at building ingress points by professional security staff utilizing video surveillance, state of the art intrusion detection systems, and other electronic means. Authorized staff must pass two-factor authentication no fewer than three times to access data center floors. All visitors and contractors are required to present identification and are signed in and continually escorted by authorized staff.

Amazon only provides data center access and information to employees who have a legitimate business need for such privileges. When an employee no longer has a business need for these privileges, his or her access is immediately revoked, even if they continue to be an employee of Amazon or Amazon Web Services. All physical and electronic access to data centers by Amazon employees is logged and audited routinely.

For additional information see: https://aws.amazon.com/security

### Environmental Safeguards

#### Fire Detection and Suppression

Automatic fire detection and suppression equipment has been installed to reduce risk. The fire detection system utilizes smoke detection sensors in all data center environments, mechanical and electrical infrastructure spaces, chiller rooms and generator equipment rooms. These areas are protected by either wet-pipe, double-interlocked pre-action, or gaseous sprinkler systems.

#### Power

The data center electrical power systems are designed to be fully redundant and maintainable without impact to operations, 24 hours a day, and seven days a week. Uninterruptible Power Supply (UPS) units provide back-up power in the event of an electrical failure for critical and essential loads in the facility. Data centers use generators to provide backup power for the entire facility.

#### Climate and Temperature Control

Climate control is required to maintain a constant operating temperature for servers and other hardware, which prevents overheating and reduces the possibility of service outages. Data centers are conditioned to maintain atmospheric conditions at optimal levels. Monitoring systems and data center personnel ensure temperature and humidity are at the appropriate levels.

#### Management

Data center staff monitor electrical, mechanical and life support systems and equipment so issues are immediately identified. Preventative maintenance is performed to maintain the continued operability of equipment.

For additional information see: https://aws.amazon.com/security

### Network Security

#### Firewalls

Firewalls are utilized to restrict access to systems from external networks and between systems internally. By default all access is denied and only explicitly allowed ports and protocols are allowed based on business need.  Each system is assigned to a firewall security group based on the system’s function. Security groups restrict access to only the ports and protocols required for a system’s specific function to mitigate risk.

Host-based firewalls restrict customer applications from establishing localhost connections over the loopback network interface to further isolate customer applications. Host-based firewalls also provide the ability to further limit inbound and outbound connections as needed.

#### DDoS Mitigation

Our infrastructure provides DDoS mitigation techniques including TCP Syn cookies and connection rate limiting in addition to maintaining multiple backbone connections and internal bandwidth capacity that exceeds the Internet carrier supplied bandwidth.  We work closely with our providers to quickly respond to events and enable advanced DDoS mitigation controls when needed.

#### Spoofing and Sniffing Protections

Managed firewalls prevent IP, MAC, and ARP spoofing on the network and between virtual hosts to ensure spoofing is not possible. Packet sniffing is prevented by infrastructure including the hypervisor which will not deliver traffic to an interface which it is not addressed to.  Nitrous.IO utilizes box isolation, operating system restrictions, and encrypted connections to further ensure risk is mitigated at all levels.

#### Port Scanning

Port scanning is prohibited and every reported instance is investigated by our infrastructure provider.  When port scans are detected, they are stopped and access is blocked.

### Data Security

#### Customer Applications

Each development box on Nitrous.IO runs within its own isolated environment and cannot interact with other applications or areas of the system. This restrictive operating environment is designed to prevent security and stability issues.  These self-contained environments isolate processes, memory, and the file system using LXC while host-based firewalls restrict applications from establishing local network connections.

### Add-ons

Customers can extend the functionality of applications by using Nitrous.IO add-ons. Add-ons are offered and managed by 3rd party companies and implement their own security controls and processes.

For additional information see: https://addons.nitrous.io

### System Security

#### System Configuration

System configuration and consistency is maintained through standard, up-to-date images, configuration management software, and by replacing systems with updated deployments. Systems are deployed using up-to-date images that are updated with configuration changes and security updates before deployment. Once deployed, existing systems are decommissioned and replaced with up-to-date systems.

#### Customer Application Isolation

Applications on the Nitrous.IO platform run within their own isolated environment and cannot interact with other applications or areas of the system to prevent security and stability issues.  These self-contained environments isolate processes, memory, and the file system while host-based firewalls restrict applications from establishing local network connections.

#### System Authentication

Operating system access is limited to Nitrous.IO staff and requires username and key authentication. Operating systems do not allow password authentication to prevent password brute force attacks, theft, and sharing.

#### Vulnerability Management

Our vulnerability management process is designed to remediate risks without customer interaction or impact.  Nitrous.IO is notified of vulnerabilities through internal and external assessments, system patch monitoring, and third party mailing lists and services.  Each vulnerability is reviewed to determine if it is applicable to Nitrous.IO’s environment, ranked based on risk, and assigned to the appropriate team for resolution.

New systems are deployed with the latest updates, security fixes, and Nitrous.IO configurations and existing systems are decommissioned as customers are migrated to the new instances. This process allows Nitrous.IO to keep the environment up-to-date. Since customer applications run in isolated environments, they are unaffected by these core system updates.

To further mitigate risk, each component type is assigned to a unique network security group. These security groups are designed to only allow access to the ports and protocols required for the specific component type. For example, user applications running within an isolated box are denied access to the Nitrous.IO management infrastructure as each is within its own network security group and access is not allowed between the two.

#### Nitrous.IO Application Security

We undergo penetration tests, vulnerability assessments, and source code reviews to assess the security of our application, architecture, and implementation. Our third party security assessments cover all areas of our platform including testing for OWASP Top 10 web application vulnerabilities and customer application isolation.  Nitrous.IO works closely with external security assessors to review the security of the Nitrous.IO platform and applications and apply best practices.

Issues found in Nitrous.IO applications are risk ranked, prioritized, assigned to the responsible team for remediation, and Nitrous.IO’s security team reviews each remediation plan to ensure proper resolution.

### Backups

#### Development Boxes

Development boxes on the Nitrous.IO platform are automatically backed up as part of the deployment process on secure, access controlled, and redundant storage.  We use these backups to activate your box on our platform and to automatically bring your development box back online in the event of an outage.

#### Customer Configuration and Meta-information

Your configuration and meta-information is backed up every minute to the same high-durability, redundant infrastructure used to store your database information.  These frequent backups allow capturing changes made to the running application configuration added after the initial deployment.

#### Nitrous.IO Platform

From our instance images to our databases, each component is backed up to secure, access-controlled, and redundant storage.  Our platform allows for recovering databases to within seconds of the last known state, restoring system instances from standard templates, and deploying customer applications and data.  In addition to standard backup practices, Nitrous.IO’s infrastructure is designed to scale and be fault tolerant by automatically replacing failed instances and reducing the likelihood of needing to restore from backup.

### Disaster Recovery

#### Customer Applications and Databases

Our platform automatically restores customer applications and Nitrous.IO Postgres databases in the case of an outage. The Nitrous.IO platform is designed to dynamically instantiate development boxes within the Nitrous.IO cloud, monitor for failures, and recover failed components including development boxes.

#### Nitrous.IO Platform

The Nitrous.IO platform is designed for stability, performance and inherently mitigates common issues that lead to outages while maintaining recovery capabilities.  Our platform maintains redundancy to prevent single points of failure, is able to replace failed components, and utilizes multiple data centers designed for resiliency. In the case of an outage, the platform is deployed across multiple data centers using current system images and data is restored from backups. Nitrous.IO reviews platform issues to understand the root cause, impact to customers, and improve the platform and processes.

#### Customer Data Retention and Destruction

You have the freedom to define what data your applications store and the ability to purge data from your databases to comply with your data retention requirements. If you deprovision a development box and associated services, we maintain snapshots of the development box and manifests of 3rd party services for one week after which time its automatically destroyed rendering the data unrecoverable.

Decommissioning hardware is managed by our infrastructure provider using a process designed to prevent customer data exposure. AWS uses techniques outlined in DoD 5220.22-M (“National Industrial Security Program Operating Manual “) or NIST 800-88 (“Guidelines for Media Sanitization”) to destroy data.

For additional information see: https://aws.amazon.com/security

### Privacy

Nitrous.IO has a published privacy policy that clearly defines what data is collected and how it is used.  Nitrous.IO is committed to customer privacy and transparency.

We takes steps to protect the privacy of our customers and protect data stored within the platform. Some of the protections inherent to Nitrous.IO’s products include authentication, access controls, data transport encryption, HTTPS support for customer applications, and the ability for customers to encrypt stored data.

### Access to Customer Data

The Nitrous.IO staff does not access or interact with customer data or applications as part of normal operations. There may be cases where Nitrous.IO is requested to interact with customer data or applications at the request of the customer for support purposes or where required by law. Customer data is access controlled and all access by Nitrous.IO staff is accompanied by customer approval or government mandate, reason for access, actions taken by staff, and support start and end time.

### Customer Security Best Practices

#### Encrypt Data in Transit

Enable HTTPS for applications and SSL database connections to protect sensitive data transmitted to and from applications.

#### Encrypt Sensitive Data at Rest

Customers with sensitive data can encrypt stored files and data within databases to meet their data security requirements.  Data encryption can be deployed using industry standard encryption and the best practices for your language or framework.

#### Secure Development Practices

Apply development best practices for your chosen development language and framework to mitigate known vulnerability types such as those on the OWASP Top 10 Web Application Security Risks.

#### Authentication

To prevent unauthorized account access use a strong passphrase for both your Nitrous.IO user account and SSH keys, store SSH keys securely to prevent disclosure, replace keys if lost or disclosed, and use Nitrous.IO’s RBAC model to invite contributors rather than sharing user accounts.

#### Use of Third-Party Solutions

In developing your application on Nitrous.IO you may choose to use third party services for added functionality such as Amazon S3, an email service provider, or one of our add-on partners. Be mindful of the data shared with these providers and their security practices just as you would be with Nitrous.IO.
