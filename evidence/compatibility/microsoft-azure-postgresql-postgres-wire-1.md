<!-- fetched 2026-10-13 from https://learn.microsoft.com/en-us/azure/postgresql/flexible-server/overview by sweep-shape-compat.py; text extracted from the provider's own page -->

What Is Azure Database for PostgreSQL flexible server? - Azure Database for PostgreSQL | Microsoft Learn 
 Skip to main content
 Skip to Ask Learn chat experience
 This browser is no longer supported.
 Upgrade to Microsoft Edge to take advantage of the latest features, security updates, and technical support.
 Download Microsoft Edge
 More info about Internet Explorer and Microsoft Edge
 Table of contents 
 Exit editor mode 
 Ask Learn 
 Ask Learn 
 Reading mode 
 Table of contents 
 Read in English 
 Add 
 Add to Plans 
 Edit 
 Copy Markdown 
 Print 
 Note 
 Access to this page requires authorization. You can try signing in or changing directories .
 Access to this page requires authorization. You can try changing directories .
 What is Azure Database for PostgreSQL flexible server?
 Feedback 
 Summarize this article for me
 In this article
 This article provides an overview of Azure Database for PostgreSQL, helping you get acquainted with its key features and core concepts.
 Azure Database for PostgreSQL is a fully managed database service that gives you granular control and flexibility over database management functions and configuration settings. The service provides flexibility and server configuration customizations based on your requirements. The architecture lets you collocate the database engine with the client tier for lower latency and choose high availability within a single availability zone and across multiple availability zones. Azure Database for PostgreSQL flexible server instance also provides cost optimization controls with the ability to stop and start your server and a burstable compute tier that's ideal for workloads that don't need full compute capacity continuously. The service supports various major community versions of PostgreSQL. For details on the specific versions supported, see Supported versions of PostgreSQL in Azure Database for PostgreSQL . The service is available in various Azure regions .
 Architecture and high availability
 The Azure Database for PostgreSQL deployment model supports high availability within a single availability zone and across multiple availability zones. The architecture separates compute and storage. The database engine runs on a container inside a Linux virtual machine, while data files reside on Azure storage. The storage maintains three locally redundant synchronous copies of the database files, ensuring data durability.
 If you configure zone redundant high availability, the service provisions and maintains a warm standby server across the availability zone within the same Azure region. The data changes on the source server are synchronously replicated to the standby server to ensure zero data loss. With zone redundant high availability, once the planned or unplanned failover event is triggered, the standby server comes online immediately and is available to process incoming transactions. This feature allows the service resiliency from availability zone failure within an Azure region that supports multiple availability zones, as shown in the following picture.
 For more information, visit High availability for more details.
 Automated patching with a managed maintenance window
 The service performs automated patching of the underlying hardware, OS, and database engine. The patching includes security and software updates. The planned maintenance release includes minor version upgrades for the PostgreSQL engine. You can configure the patching schedule to be system-managed or define your custom schedule. During the maintenance schedule, the patch is applied, and the server might need to restart as part of the patching process to complete the update. By using the custom schedule, you can make your patching cycle predictable and choose a maintenance window with minimum impact on your business. Generally, the service follows a monthly release schedule as part of the continuous integration and release.
 Automatic backups
 Azure Database for PostgreSQL automatically creates server backups and stores them on the region's zone redundant storage (ZRS). You can restore your server to any point within the backup retention period. The default backup retention period is seven days. You can optionally configure the retention for up to 35 days. The service encrypts all backups by using AES 256-bit encryption. For more information, see Backups .
 Adjust performance and scale within seconds
 Azure Database for PostgreSQL is available in three compute tiers: Burstable, General Purpose, and Memory Optimized. The Burstable tier is best for low-cost development and low concurrency workloads without continuous compute capacity. The General Purpose and Memory Optimized tiers are better for production workloads that require high concurrency, scale, and predictable performance. You can build your first application on a small database for a few dollars a month, then seamlessly adjust the scale to meet the needs of your solution.
 Stop and start server to lower TCO
 Azure Database for PostgreSQL allows you to stop and start the server on demand to lower your TCO. The compute tier billing stops immediately when you stop the server. This feature can provide significant cost savings during development, testing, and time-bound predictable production workloads. The server remains stopped for seven days unless you restart it sooner.
 Enterprise-grade security
 Azure Database for PostgreSQL uses the FIPS 140-2 validated cryptographic module for storage encryption of data at rest. The service encrypts data, including backups and temporary files created while running queries. It uses the AES 256-bit cipher included in Azure storage encryption, and the keys can be system-managed (default). Azure Database for PostgreSQL encrypts data in motion with default transport layer security (SSL/TLS) enforced by default. The service enforces and supports TLS version 1.2 and later.
 By using Azure virtual network, Azure Database for PostgreSQL flexible server instance allows full private access to the servers. Servers in the Azure virtual network can only be reached and connected through private IP addresses. With virtual network integration, public access is denied, and servers can't be reached by using public endpoints.
 Monitor and alerting
 Azure Database for PostgreSQL has built-in performance monitoring and alerting features. All Azure metrics have a one-minute frequency, each providing 30 days of history. You can configure alerts on the metrics. The service exposes host server metrics to monitor resource utilization and allows configuring slow query logs. By using these tools, you can quickly optimize your workloads and configure your server for the best performance.
 Built-in PgBouncer
 An Azure Database for PostgreSQL flexible server instance has a built-in PgBouncer and a connection pooler. You can enable it and connect your applications to your Azure Database for PostgreSQL flexible server instance through PgBouncer by using the same hostname and port 6432. When enabled, PgBouncer is also available for elastic clusters under port 8432.
 Azure regions
 One advantage of running your workload in Azure is global reach. Azure Database for PostgreSQL is currently available in the following Azure regions:
 Region
 Intel Compute
 AMD Compute
 Confidential Compute
 Zone-Redundant HA
 Same-Zone HA
 Geo-Redundant backup
 Australia Central
 ✅ (v3/v4/v5)
 ❌
 ❌
 ❌
 ✅
 ✅
 Australia Central 2 *
 ✅ (v3/v4/v5)
 ❌
 ❌
 ❌
 ✅
 ❌
 Australia East
 ✅ (v3/v4/v5/v6)
 ✅ (v5)
 ❌
 ✅
 ✅
 ✅
 Australia Southeast
 ✅ (v3/v4/v5)
 ❌
 ❌
 ❌
 ✅
 ✅
 Austria East
 ✅ (v3/v4/v5)
 ✅ (v5)
 ❌
 ✅
 ✅
 ❌
 Belgium Central
 ✅ (v3/v4/v5)
 ✅ (v5)
 ❌
 ✅
 ✅
 ❌
 Brazil South
 ✅ (v3/v4/v5)
 ❌
 ❌
 ✅ $
 ✅
 ❌
 Brazil Southeast *
 ✅ (v3/v4/v5)
 ❌
 ❌
 ❌
 ✅
 ❌
 Canada Central
 ✅ (v3/v4/v5)
 ✅ (v5)
 ❌
 ✅
 ✅
 ✅
 Canada East
 ✅ (v3/v4/v5)
 ✅ (v5)
 ❌
 ❌
 ✅
 ✅
 Central India
 ✅ (v3/v4/v5)
 ❌
 ❌
 ✅ $
 ✅
 ✅
 Central US
 ✅ (v3/v4/v5)
 ❌
 ❌
 ✅
 ✅
 ✅
 Chile Central
 ✅ (v3/v4/v5)
 ✅ (v5)
 ❌
 ✅
 ✅
 ❌
 China East 2
 ✅ (v3/v4)
 ❌
 ❌
 ❌
 ✅
 ❌
 China East 3
 ✅ (v3/v4)
 ❌
 ❌
 ❌
 ✅
 ✅
 China North 2
 ✅ (v3/v4)
 ❌
 ❌
 ❌
 ✅
 ❌
 China North 3
 ✅ (v3/v4/v5)
 ❌
 ❌
 ✅
 ✅
 ✅
 East Asia
 ✅ (v3/v4/v5)
 ✅ (v6)
 ❌
 ✅ $ **
 ✅
 ✅
 East US
 ✅ (v3/v4/v5)
 ✅ (v5)
 ❌
 ✅ $
 ✅
 ✅
 East US 2
 ✅ (v3/v4)
 ❌
 ❌
 ✅ $
 ✅
 ✅
 France Central
 ✅ (v3/v4/v5)
 ❌
 ❌
 ✅
 ✅
 ✅
 France South
 ✅ (v3/v4/v5)
 ❌
 ❌
 ❌
 ✅
 ✅
 Germany North *
 ✅ (v3/v4/v5)
 ❌
 ❌
 ❌
 ✅
 ✅
 Germany West Central
 ✅ (v3/v4/v5)
 ❌
 ❌
 ✅ $
 ✅
 ✅
 Indonesia Central
 ✅ (v3/v4/v5)
 ✅ (v5/v6)
 ❌
 ✅
 ✅
 ❌
 Israel Central
 ✅ (v3/v4)
 ❌
 ❌
 ✅
 ✅
 ❌
 Italy North
 ✅ (v3/v4/v5)
 ❌
 ❌
 ✅
 ✅
 ❌
 Japan East
 ✅ (v3/v4)
 ❌
 ❌
 ✅
 ✅
 ✅
 Japan West
 ✅ (v3/v4/v5)
 ✅ (v6)
 ❌
 ❌
 ✅
 ✅
 Jio India Central
 ✅ (v3)
 ❌
 ❌
 ❌
 ✅
 ✅
 Jio India West
 ✅ (v3)
 ❌
 ❌
 ❌
 ✅
 ✅
 Korea Central
 ✅ (v3/v4/v5)
 ❌
 ❌
 ✅ **
 ✅
 ✅
 Korea South
 ✅ (v3/v4/v5)
 ❌
 ❌
 ❌
 ✅
 ✅
 Malaysia West
 ✅ (v3/v4/v5)
 ✅ (v5/v6)
 ❌
 ✅
 ✅
 ❌
 Mexico Central
 ✅ (v3/v4)
 ❌
 ❌
 ✅ $
 ✅
 ❌
 New Zealand North
 ✅ (v3/v4/v5)
 ❌
 ❌
 ✅
 ✅
 ❌
 North Central US
 ✅ (v3/v4/v5)
 ✅ (v5)
 ❌
 ❌
 ✅
 ✅
 North Europe
 ✅ (v3/v4/v5)
 ❌
 ✅ (v5)
 ✅ $
 ✅
 ✅
 Norway East *
 ✅ (v3/v4/v5)
 ✅ (v5)
 ❌
 ✅
 ✅
 ✅
 Norway West
 ✅ (v3/v4/v5)
 ❌
 ❌
 ❌
 ✅
 ✅
 Poland Central
 ✅ (v3/v4)
 ❌
 ❌
 ✅
 ✅
 ❌
 Qatar Central
 ✅ (v3/v4)
 ❌
 ❌
 ✅ $
 ✅
 ❌
 South Africa North
 ✅ (v3/v4/v5)
 ❌
 ❌
 ✅
 ✅
 ✅
 South Africa West *
 ✅ (v3/v4/v5)
 ❌
 ❌
 ❌
 ✅
 ✅
 South Central US
 ✅ (v3/v4)
 ❌
 ❌
 ✅ $
 ✅
 ✅
 South India
 ✅ (v3/v4/v5)
 ✅ (v6)
 ❌
 ✅
 ✅
 ✅
 Southeast Asia
 ✅ (v3/v4)
 ❌
 ❌
 ✅ $
 ✅
 ✅
 Spain Central
 ✅ (v3/v4)
 ❌
 ❌
 ✅
 ✅
 ❌
 Sweden Central
 ✅ (v3/v4/v5)
 ❌
 ❌
 ✅
 ✅
 ✅
 Switzerland North
 ✅ (v3/v4/v5)
 ❌
 ❌
 ✅
 ✅
 ✅
 Switzerland West *
 ✅ (v3/v4/v5)
 ❌
 ❌
 ❌
 ✅
 ✅
 UAE Central *
 ✅ (v3/v4/v5)
 ❌
 ❌
 ❌
 ✅
 ✅
 UAE North
 ✅ (v3/v4/v5)
 ❌
 ✅ (v5)
 ✅
 ✅
 ✅
 UK South
 ✅ (v3/v4/v5)
 ✅ (v5)
 ❌
 ✅
 ✅
 ✅
 UK West
 ✅ (v3/v4/v5)
 ✅ (v5)
 ❌
 ❌
 ✅
 ✅
 US Gov Arizona
 ✅ (v3/v4)
 ❌
 ❌
 ❌
 ✅
 ❌
 US Gov Texas
 ✅ (v3/v4)
 ❌
 ❌
 ❌
 ✅
 ❌
 US Gov Virginia
 ✅ (v3/v4)
 ❌
 ❌
 ✅
 ✅
 ✅
 West Central US
 ✅ (v3/v4/v5)
 ❌
 ❌
 ❌
 ✅
 ✅
 West Europe
 ✅ (v3/v4/v5)
 ❌
 ✅ (v5)
 ✅ $
 ✅
 ✅
 West US
 ✅ (v3/v4/v5)
 ✅ (v5)
 ❌
 ❌
 ✅
 ✅
 West US 2
 ✅ (v3/v4)
 ❌
 ❌
 ✅ $
 ✅
 ✅
 West US 3
 ✅ (v3/v4/v5)
 ✅ (v5)
 ❌
 ✅ **
 ✅
 ❌
 Note
 Symbol legend: 
 * indicates access-restricted regions available only upon request
 $ indicates new zone-redundant HA deployments are temporarily blocked
 ** indicates zone-redundant HA deployment considerations for existing servers (see special considerations )
 $ New zone-redundant high availability deployments are temporarily blocked in these regions. The service fully supports already provisioned HA servers.
 $ New server deployments are temporarily blocked in these regions. The service fully supports already provisioned servers.
 ** You can now deploy zone-redundant high availability when you provision new servers in these regions. For existing servers deployed in AZ with no preference (check this on the Azure portal) before the region started to support AZ, even when you enable zone-redundant HA, the standby is provisioned in the same AZ (same-zone HA) as the primary server. To enable zone-redundant high availability in such cases, see these special considerations .
 (*) Certain regions are access-restricted to support specific customer scenarios, such as in-country/region disaster recovery. You can access these regions only upon request by creating a new support request.
 Note
 If your application requires zone-redundant high availability and it's unavailable in your preferred Azure region, consider using other regions within the same geography where zone-redundant HA is available, such as US East for US East 2, Central US for North Central US, and so on.
 V6 SKU family (Preview)
 Azure Database for PostgreSQL now supports General Purpose and Memory Optimized V6 SKU family in Public Preview. These versions deliver massive scale for high-performance OLTP, analytics, and complex queries, with improved price performance and higher memory ceilings.
 Limitations
 Scaling from V6 SKU family to Burstable tier isn't supported.
 Scaling from Burstable tier to V6 SKU family isn't supported.
 Virtual Network integration isn't supported.
 Migration
 Azure Database for PostgreSQL runs the community version of PostgreSQL. This version provides full application compatibility and requires minimal refactoring to migrate an existing application developed on the PostgreSQL engine to Azure Database for PostgreSQL.
 Azure Database Migration Service – For seamless and simplified migrations to Azure Database for PostgreSQL with minimal downtime, use Azure Database Migration Service. Visit What is the migration service in Azure Database for PostgreSQL? 
 Dump and Restore – For offline migrations where you can afford some downtime, dump, and restore by using community tools like pg_dump and pg_restore provides the fastest way to migrate. For more information, see Migrate using dump and restore .
 Feedback and support
 If you have questions or suggestions about Azure Database for PostgreSQL, you can get help and support through the following channels:
 To contact Azure Support, file a ticket from the Azure portal .
 To fix an issue with your account, file a support request in the Azure portal.
 To provide feedback or to request new features, create an entry via UserVoice .
 Related content
 Create an Azure Database for PostgreSQL 
 Feedback
 Was this page helpful?
 Yes 
 No 
 No 
 Need help with this topic?
 Want to try using Ask Learn to clarify or guide you through this topic?
 Ask Learn 
 Ask Learn 
 Suggest a fix? 
 Additional resources
 Last updated on 
 2026-01-09
 In this article
 Was this page helpful?
 Need help with this topic?
 Want to try using Ask Learn to clarify or guide you through this topic?
 Ask Learn 
 Ask Learn 
 Suggest a fix? 
 en-us 
 Your Privacy Choices 
 Theme 
 Light 
 Dark 
 High contrast 
 AI Disclaimer 
 Previous Versions 
 Blog 
 Contribute 
 Privacy 
 Consumer Health Privacy 
 Terms of Use 
 Trademarks 
 © Microsoft 2026
