<style>#_html{zoom:0.9}#_toc{width:600px;zoom:0.7;}#_toc{line-height:1!important}</style>



# Polarion System Configuration Properties Reference

Polarion 2304  
POL008 - 2304


Unpublished work. © 2023 Siemens

This Documentation contains trade secrets or otherwise confidential information owned by Siemens Industry Software Inc. or
its affiliates (collectively, "Siemens"), or its licensors. Access to and use of this Documentation is strictly limited as set forth in
Customer’s applicable agreement(s) with Siemens. This Documentation may not be copied, distributed, or otherwise disclosed
by Customer without the express written permission of Siemens, and may not be used in any way not expressly authorized by
Siemens.


This Documentation is for information and instruction purposes. Siemens reserves the right to make changes in specifications
and other information contained in this Documentation without prior notice, and the reader should, in all cases, consult
Siemens to determine whether any changes have been made.

No representation or other affirmation of fact contained in this Documentation shall be deemed to be a warranty or give rise to
any liability of Siemens whatsoever.

If you have a signed license agreement with Siemens for the product with which this Documentation will be used, your use of
this Documentation is subject to the scope of license and the software protection and security provisions of that agreement.

If you do not have such a signed license agreement, your use is subject to the Siemens Universal Customer Agreement, which
may be viewed at https://www.sw.siemens.com/en-US/sw-terms/base/uca/, as supplemented by the product specific terms
which may be viewed at https://www.sw.siemens.com/en-US/sw-terms/supplements/.

SIEMENS MAKES NO WARRANTY OF ANY KIND WITH REGARD TO THIS DOCUMENTATION INCLUDING, BUT NOT LIMITED
TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE, AND NON-INFRINGEMENT OF
INTELLECTUAL PROPERTY. SIEMENS SHALL NOT BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, CONSEQUENTIAL OR
PUNITIVE DAMAGES, LOST DATA OR PROFITS, EVEN IF SUCH DAMAGES WERE FORESEEABLE, ARISING OUT OF OR RELATED
TO THIS DOCUMENTATION OR THE INFORMATION CONTAINED IN IT, EVEN IF SIEMENS HAS BEEN ADVISED OF THE POSSIBILITY
OF SUCH DAMAGES.

TRADEMARKS: The trademarks, logos, and service marks (collectively, "Marks") used herein are the property of Siemens or other
parties. No one is permitted to use these Marks without the prior written consent of Siemens or the owner of the Marks,
as applicable. The use herein of third party Marks is not an attempt to indicate Siemens as a source of a product, but is
intended to indicate a product from, or associated with, a particular third party. A list of Siemens’ Marks may be viewed at:
www.plm.automation.siemens.com/global/en/legal/trademarks.html. The registered trademark Linux® is used pursuant to a
sublicense from LMI, the exclusive licensee of Linus Torvalds, owner of the mark on a world-wide basis.


About Siemens Digital Industries Software
Siemens Digital Industries Software is a global leader in the growing field of product lifecycle management (PLM),
manufacturing operations management (MOM), and electronic design automation (EDA) software, hardware, and services.

Siemens works with more than 100,000 customers, leading the digitalization of their planning and manufacturing processes. At
Siemens Digital Industries Software, we blur the boundaries between industry domains by integrating the virtual and physical,
hardware and software, design and manufacturing worlds. With the rapid pace of innovation, digitalization is no longer
tomorrow’s idea. We take what the future promises tomorrow and make it real for our customers today. Where today meets
tomorrow. Our culture encourages creativity, welcomes fresh thinking and focuses on growth, so our people, our business, and
our customers can achieve their full potential.

Support Center: support.sw.siemens.com  
Send Feedback on Documentation: support.sw.siemens.com/doc_feedback_form


## 1. Introduction

In addition to the extensive configuration and customization options available in the Polarion's
Administration, there is a set of system level configuration properties available to administrators and
developers that affect how various Polarion system processes and functions work or behave.


The properties file
All the configuration properties are embedded in the system. A default subset is exposed in the
polarion.properties file. This file resides on the server's file system.

Default location polarion.properties file:

- Windows: %POLARION_HOME%\polarion\configuration\polarion.properties
- Linux: %POLARION_HOME%/etc/polarion.properties

The file is a Java properties file with each property specified as a `key=value` pair. If a property
documented in this reference is not present in the properties file by default, its default value is still in
effect. If you want to modify the value, you can add the property on a new line using any text editor
application.

```
com.property.added.to.file=myvalue
```

> Tip:
> You must restart the Polarion server in order for changes in the polarion.properties file take effect.


Runtime properties
A subset of the configuration properties are classified as "runtime". You should edit Runtime properties
in the Configuration Properties page of Polarion Administration. Changes do not require restarting the
server. See the Runtime properties section of this document for a listing.


Usage
Caution:
Configuration at the system level is an advanced topic for experienced administrators, integrators,
and developers. Improper usage of system configuration properties can potentially result in
performance degradation, index corruption, Out of Memory and other errors. If you are unsure
about the impact of a setting on your system, it is recommended that you test in a non-production
environment, or seek support or services.



## 2. System properties

### `announcer.smtp.host`

Default value: none

To enable email notifications and the sending of bug reports:
1. Set 1com.polarion.platform.persistence.notifications.disabled` to false
2. Add or uncomment and configure the following properties in the polarion.properties file:
```
announcer.smtp.host=<name or IP of an accessible SMTP host>
announcer.smtp.port=<port number of the SMTP host> (25 is the default)
(Optional) announcer.smtp.auth=<false|true> (Set it to true if your SMTP host requires authentication.)
announcer.smtp.user= SMTP host username (Required if announcer.smtp.auth=true.)
announcer.smtp.password=SMTP host username's password (Required if announcer.smtp.auth=true.)
```

Scope: System

Added in version: 3.0.0


### `announcer.smtp.password`

Default value: none
The password for the user set in `announcer.smtp.user` property.

(Required when announcer.smtp.auth is true because authentication is required to access the SMTP host.)
To enable email notifications and the sending of bug reports:
1. Set `com.polarion.platform.persistence.notifications.disabled` to false
2. Add or uncomment and configure the following properties in the polarion.properties file:
```
announcer.smtp.host=<name or IP of an accessible SMTP host>
announcer.smtp.port=<port number of the SMTP host> (25 is the default)
(Optional) announcer.smtp.auth=<false|true> (Set it to true if your SMTP host requires authentication.)
announcer.smtp.user= SMTP host username (Required if announcer.smtp.auth=true.)
announcer.smtp.password=SMTP host username's password (Required if announcer.smtp.auth=true.)
```

Scope: System

Added in version: 3.0.0


### `announcer.smtp.user`

Default value: none
The user you use to access those SMTP hosts that require authentication.

(Required when `announcer.smtp.auth` is true.)
To enable email notifications and the sending of bug reports:
1. Set `com.polarion.platform.persistence.notifications.disabled` to false
2. Add or uncomment and configure the following properties in the polarion.properties file:
```
announcer.smtp.host=<name or IP of an accessible SMTP host>
announcer.smtp.port=<port number of the SMTP host> (25 is the default)
(Optional) announcer.smtp.auth=<false|true> (Set it to true if your SMTP host requires authentication.)
announcer.smtp.user= SMTP host username (Required if announcer.smtp.auth=true.)
announcer.smtp.password=SMTP host username's password (Required if announcer.smtp.auth=true.)
```

Scope: System

Added in version: 3.0.0

### `attachments.indexingOfAttachmentContent.additionalFileTypes`

Default value: ""

When indexing is enabled in the system configuration, then by default, Polarion indexes the content of some types of attachments,
determined by their file extensions.

This property enables you to specify additional file types to be indexed. The value type is string. If not empty, value should be a commaseparated list of file extensions, without the period character.

Do not use wildcards.

Example: `attachments.indexingOfAttachmentContent.additionalFileTypes=csv,xls,xlm`

Indexing more attachment types can significantly increase the time needed to index/reindex Polarion. Consider whether additional
types are really needed and used for searching
You can use the property `attachments.indexingOfAttachmentContent.fileTypesToIgnore` to explicitly exclude
attachment file types from indexing
The property `attachments.indexingOfAttachmentContent.enabled` controls whether or not indexing of attachment
content is enabled.

See the Help topic Attachment file types for indexing for a list of the file types indexed by default, and information about all file formats
supported for indexing.

Scope: System

Added in version: 3.20.1 (20 R1)


### `attachments.indexingOfAttachmentContent.enabled`

Default value: head

Setting this property to "false" disables the indexing of attachment content. (Can improve indexing time.)
NOTE: By setting this value to false, the content of attachments can no longer be searched. (Other attachment fields like fileName or
length are not affected by this property.)
Setting this property to "true" enables the indexing of attachment content in both the head and history indexes.

Setting this property to "head" (the default) only enables the indexing of attachment content in the head index.

Scope: System

Added in version: 3.7.0 (2013)


### `attachments.indexingOfAttachmentContent.fileTypesToIgnore`

Default value: ""

By default, Polarion indexes the content of some types of attachments, determined by their file extensions. This property enables you to
explicitly specify file types that should not be indexed.

The value type is string. If not empty, value should be a comma-separated list of file extensions, without the period character. Do not use
wildcards.

Example: `attachments.indexingOfAttachmentContent.fileTypesToIgnore=doc,java,pages,pdf`

Indexing fewer attachment types can decrease the time needed to index/reindex Polarion. If you want to exclude any types in the default
list from being indexed because you don't really need to have them indexed, or because you find they cause issues with indexing,
specify them in this property.

You can use the property `attachments.indexingOfAttachmentContent.additionalFileTypes` to explicitly include
attachment file types for indexing
The property `attachments.indexingOfAttachmentContent.enabled` controls whether or not indexing of attachment
content is enabled.

See the Help topic Attachment file types for indexing for a list of the file types indexed by default, and information about all file formats
supported for indexing.

Scope: System

Added in version: 3.20.1 (20 R1)


### `attachments.maxSizeOfIndexedAttachmentInMB`

Default value: 10

Limits the maximum size of attachments (in megabytes) that get indexed based on their content.

If an attachment’s size is lower or equal to this limit, then its content will get parsed and therefore be searchable.

If an attachment's size is larger than this limit, then its contents will not get parsed.

Other attachment attributes such as filename, author, or created date are not affected by this property.

See the Attachment file types for indexing topic in Support Center for a list of the file types indexed by default, and for further information
about all file formats supported for indexing.

Scope: System

Added in version: 3.7.1 (2013 SR1)


### `base.url`

Default value: none

The URL of your Polarion instance.

(What users will type in the browser to access Polarion.)
It must be a fully qualified domain name (FQDN) or an IP address.

Scope: System

Added in version: 3.0.0


### `bulkEditLimit`

Default value: 20

Lets you configure a limit, that when reached, Polarion displays the Action options instead of immediately displaying the Bulk Edit form.

Value represents number of items selected for bulk editing.

Scope: System

Added in version: 3.4.2


### `calc.base.url`

Default value: none

The Node-specific URL of a node.

It is used in calculations to access Polarion via web services.

Example: `calc.base.url=http://example-node`

Scope: System

Added in version: 3.0.0


### `calculated.fields.mode`

Default value: async

Controls what mode is used for the calculation of fields. (Since Polarion 3.3.0.) Possible Values:

- async – Calculated fields values are calculated asynchronously after a commit.
- off – Disables calculated fields.

Scope: System

Added in version: 3.3.0


### `com.polarion.activity.(sourceID).(type).maxActivitiesAge`

Default value: 90

Configures how long activities are kept by the activity cleaner job. Limits can be set individually for a particular source, source and type,
or globally for all sources. If the property is not specified, the limit is controlled by the per source default defined by the
IActivitySource implementation.

`maxActivitiesAge` properties define the limit in days.

A search for the value is done in the following order:
1. System property for source.type: `com.polarion.activity.(sourceID).(type).maxActivitiesAge`
2. System property for source: `com.polarion.activity.(sourceID).maxActivitiesAge`
3. System property for all sources, types: `com.polarion.activity.maxActivitiesAge`
4. The default limit for source/type: as returned by IActivitySource.getHistoryLimitDays(type)

Scope: System

Added in version: 3.10.2 (2016 SR2)


### `com.polarion.activity.(sourceID).(type).maxActivitiesLimit`

Default value: 5000

Configures how many activities are kept by the activity cleaner job. A limit can be set individually for a particular source, a source and
type and globally for all sources.

If no property is specified, the limit is controlled by the per source default defined by the IActivitySource implementation.

maxActivitiesLimit properties define the limit by the number of items.

A search for the value is done in the following order:
1. System property for source.type: `com.polarion.activity.(sourceID).(type).maxActivitiesLimit`
2. System property for source: `com.polarion.activity.(sourceID).maxActivitiesLimit`
3. System property for all sources, types: `com.polarion.activity.maxActivitiesLimit`
4. Default limit for source/type: as returned by IActivitySource.getHistoryLimitCount(type);

Scope: System

Added in version: 3.10.2 (2016 SR2)


### `com.polarion.alm.activities.bulkPublishInterval`

Default value: 1000

Optimizes the writing of Activities to the shared Lucene index by writing them only once per given interval. Value is an integer
representing milliseconds. Setting it to zero (0) or a negative value disables bulk publishing.

Scope: System

Added in version: 3.17.1 (17.1)


### `com.polarion.alm.activities.disabled`

Default value: false

Enables or disables the creation of Activities in the Activity Stream. Value is Boolean (true or false).

Scope: System

Added in version: 3.5.2 (2011 SR2)


### `com.polarion.alm.ui.enableGravatar`

Default value: false

Enables or disables the Gravatar (https://en.gravatar.com/) service so that it can be used with user avatar images. Value is
Boolean (true or false).

Scope: System

Added in version: 3.5.2 (2011 SR2)


### `com.polarion.alm.ui.forms.extensions.disableTimeSpentRecording`

Default value: false

Defines whether the time spent on manual test execution should be stored within the Test Record. If set to true, then time is NOT
stored.

Even if time recording is disabled and the time is not recorded, users will still see the clock running while executing a test for a Test
Record.

Scope: System

Added in version: 3.8.2 (2014 SR2)


### `com.polarion.alm.ui.forms.extensions.testExtensionRecordsLimit`

Default value: 20

Defines the default value for how many test records will be loaded to build the test steps recent results and test case recent results
values in the Test Extension.

It can be overridden by the maxRecentItems configuration of the execute-test form extension. Value is a positive integer.

​

Scope: System

Added in version: 3.8.1 (2014 SR1)


### `com.polarion.alm.ui.forms.extensions.velocity.enabled`

Default value: true

Allows you to disable the out-of-the-box Velocity Form Extension if it conflicts with the Velocity Work Item Form Extension from the Extensions Porta
or with the Velocity Form Extension contributed by the PSO Scripting Engine.

To disable the out-of-the-box implementation, set the property to "false".

Scope: System

Added in version: 3.22.2 (22 R2)


### `com.polarion.cluster.#ClusterId#.loadBalancer.password`

Default value: None

The password of the credentials used to connect to the load balancer if authentication is enabled.

If your load balancer's Apache configuration requires a username and password, you must set these properties in the
polarion.properties file.

(Replace #ClusterId# with the Cluster machine's ID.)
The default setup uses the same credentials as the SVN repository. The username must be added in the following additional property.


### `com.polarion.cluster.#ClusterId#.loadBalancer.user`

Note: See the Configure the Coordinator section in the Deployment and Maintenance Guide on Support Center.

Scope: System

Added in version: 3.8.0 (2014)


### `com.polarion.cluster.#ClusterId#.loadBalancer.user`

Default value: none

The username of the credentials used to connect to the load balancer if authentication is enabled.

If your load balancer's Apache configuration requires a username and password, you must set these properties in the polarion.properties file.

(Replace #ClusterId# with the Cluster machine's ID.)

The default setup uses the same credentials as the SVN repository.

The username's password must be added in the following additional property.


### `com.polarion.cluster.#ClusterId#.loadBalancer.password`

Note: See the Configure the coordinator section in the Deployment and Maintenance Guide on Support Center.

Scope: System

Added in version: 3.8.0 (2014)


### `com.polarion.cluster.client.connectionTimeout`

Default value: 120000

If a Polarion node does not contact the ZooKeeper server for longer than the specified time, then the old connection is discarded, and a
new one established. Value is an integer representing milliseconds.

NOTE: No events are fired. It is an internal function that ensures that the connection to the ZooKeeper server is still alive.

See also: `com.polarion.cluster.client.sessionTimeout`.

This property pertains to the configuration of Polarion to run in a clustered server environment. For information, see the Deployment
and Maintenance Guide on Support Center.

Scope: System

Added in version: 3.8.0 (2014)


### `com.polarion.cluster.client.lostReconnectTimeout`

Default value: 5000

Defines how long the Polarion node in a cluster waits if it loses its connection to the Coordinator before a shutdown is triggered. Value is
an integer representing milliseconds.

This property pertains to the configuration of Polarion to run in a clustered server environment.

For information, see the Deployment and Maintenance Guide on Support Center.

Scope: System

Added in version: 3.8.0 (2014)


### `com.polarion.cluster.client.retryPolicy.ExponentialBackoffRetry.baseSleepTime`

Default value: 10000

Defines how much the Polarion node should increase the delay time between reconnect attempts to the Coordinator. (If a previous
attempt was unsuccessful.)
By default it is: 0 seconds, 10 seconds, 20 seconds, 30 seconds. Value is an integer representing milliseconds.

This property pertains to the configuration of Polarion to run in a clustered server environment.

For information, see the Deployment and Maintenance Guide, available as a PDF download in the Polarion product center on Support
Center.

Scope: System

Added in version: 3.8.0 (2014)


### `com.polarion.cluster.client.retryPolicy.ExponentialBackoffRetry.maxRetries`

Default value: 6

Define the number of times that the Polarion node tries to reconnect to the Coordinator if it loses its connection to it. Value is a positive
integer.

This property pertains to the configuration of Polarion to run in a clustered server environment.


For information, see the Deployment and Maintenance Guide, available as a PDF download in the Polarion product center on Support
Center.

Scope: System

Added in version: 3.8.0 (2014)


### `com.polarion.cluster.client.sessionTimeout`

Default value: 120000

If a Polarion node does not contact the ZooKeeper server for longer than the specified time then its session expires. Value is an integer
representing milliseconds.

This property pertains to the configuration of Polarion to run in a clustered server environment.

For information, see the Deployment and Maintenance Guide, available as a PDF download in the Polarion product center on Support
Center.

​

Scope: System

Added in version: 3.8.0 (2014)


### `com.polarion.cluster.shutDownWhenConnectionToCoordinatorIsLost`

Default value: true

Controls whether nodes should shut themselves down when a connection to the Coordinator cannot be re-established. Value is Boolean
(true or false).

Scope: System

Added in version: 3.8.0 (2014)


### `com.polarion.clusterDescription`

Default value: none

A textual description of the Cluster Server.

Example:
com.polarion.clusterDescription=Stand-alone Selenium Tests Instance in GitLab
Add an ID for the Cluster machine with: `com.polarion.clusterId`
Example: com.polarion.clusterId=cluster1
Add a label for the Cluster machine with: `com.polarion.clusterLabel`
Example: com.polarion.clusterLabel=Selenium Tests Instance
Note: See the Configure shared services topic in the Deployment and Maintenance Guide on Support Center.

Also used when migrating a remote instance to a non-clustered stand-alone instance.

(See the Migrating a remote instance to a non-clustered stand-alone instance section in the Deployment and Maintenance Guide
on Support Center for details.)
Scope: System

Added in version: 3.10.0 (2016)


### `com.polarion.clusterId`

Default value: none

A Cluster's ID in a Polarion Clustered setup.

Example: `com.polarion.clusterId=cluster1`

Add a label for the Cluster machine with: `com.polarion.clusterLabel`

Example: `com.polarion.clusterLabel=Selenium Tests Instance`

Add a textual description of the Cluster machine with: `com.polarion.clusterDescription`

Example: `com.polarion.clusterDescription=Stand-alone Selenium Tests Instance in GitLab`

Note: See the Configure shared services topic in the Deployment and Maintenance Guide on Support Center.


Scope: System

Added in version: 3.10.0 (2016)


### `com.polarion.clusterLabel`

Default value: none

A Cluster's label in a Polarion Clustered setup.

Example:`com.polarion.clusterLabel=Selenium Tests Instance`

Add an ID for the Cluster machine with: `com.polarion.clusterId`

Example: `com.polarion.clusterId=cluster1`

Add a textual description of the Cluster machine with: `com.polarion.clusterDescription`

Example: `com.polarion.clusterDescription=Stand-alone Selenium Tests Instance in GitLab`

Note: See the Configure shared services topic in the Deployment and Maintenance Guide on Support Center.

​
Scope: System

Added in version: 3.10.0 (2016)


### `com.polarion.connectors.autoconfigurationDefaultLinkRole`

Default value: relates to

The ID of an existing link role that will be used by default in the Doors/ReqIF auto-mapping-configuration. Value is a string.

Scope: System

Added in version: 3.10.1 (2016 SR1)


### `com.polarion.customWordSpacingCharacters`

Default value: null

Allows for the use of custom characters (in Unicode) that will be used as word spacing during the HTML compare process. Enables
Document comparison with languages such as Japanese that do not separate words with spaces.

Specify a "break" character to be used when users compare Document versions in the Document history. Multiple characters can be
specified and breaks occur on every one of them.

Examples:
```
com.polarion.customWordSpacingCharacters=uff0e
com.polarion.customWordSpacingCharacters=\u3000\u3001\u3002\uff08\uff09\uff0c\uff0e\uff61\uff64
```

Scope: System

Added in version: 3.6.2 (2012 SR2)


### `com.polarion.disableInsecureEnumerations`

Default value: false

If enabled, then Project, Project Group and User enumerations return no available values. Value is Boolean (true or false).

Scope: System

Added in version: 3.6.3 (2012 SR3)


### `com.polarion.enableWiki`

Default value: true

Enables or disables the ability to create new wiki pages (i.e. Classic Wiki). Value is Boolean (true or false).

NOTE: The xWiki technology originally implemented in Polarion, and now referred to as "Classic Wiki", is considered deprecated. The
newer visual widget-based Pages technology is recommended for new pages, as is migration of existing Classic Wiki pages.

Scope: System

Added in version: 3.7.2 (2013 SR2)


### `com.polarion.enumerations.objectEnumerationsLimit`

Default value: 10000

Defines the maximum number of objects loaded in object enumerations like Documents, Pages, Test Runs, etc. Setting a lower limit can
improve performance, especially when there are hundreds of Documents, Pages etc. Value is an integer.

NOTE: If value is set to -1, then there is no limit.

Scope: System

Added in version: 3.9.1 (2015 SR1)


### `com.polarion.excelImport.maxValuesCount`

Default value: 20

Controls the number of distinct values in a column that a user will be able to map to enumeration values in the Excel import wizard. If
the number of values found in a column is greater than this limit, custom mapping will not be available for the column. Value is a positive
integer.

Scope: System

Added in version: 3.5.2 (2011 SR2)


### `com.polarion.excelImport.previewMaxCount`

Default value: 100

Sets the maximum number of Work Items displayed in the Excel import preview. Value is a positive integer.

Scope: System

Added in version: 3.5.2 (2011 SR2)


### `com.polarion.excelImportValueDelimiters`

Default value: ,;

Overwrites delimiters used for splitting multi-values fields during import from Microsoft Excel with the value set in this property.

Scope: System

Added in version: 3.6.3 (2012 SR3)


### `com.polarion.excelRoundTrip.sheetPassword`

Default value: polarion

Stores the password that Polarion applies to protected sheets of the Excel workbook exported for Excel round-trip. Value is a string.

Scope: System

Added in version: 3.5.2 (2011 SR2)


### `com.polarion.highchartExportServer.autoStart`

Default value: true

Enables or disables automatic startup of the HighCharts chart rendering server. Value is Boolean (true or false).

Scope: System

Added in version: 3.7.3 (2013 SR3)


### `com.polarion.highchartExportServer.home`

Default value: null

Defines a custom path to the folder with the HighCharts export server's files. If not defined, the default folder from the
`com.polarion.alm.ui` plugin is used. Value is a string.

Scope: System

Added in version: 3.7.3 (2013 SR3)


### `com.polarion.highchartExportServer.host`

Default value: 127.0.0.1

Defines the host name that will be used by the HighCharts chart rendering server. Value is a string.

Scope: System

Added in version: 3.7.3 (2013 SR3)


### `com.polarion.highchartExportServer.port`

Default value: 34567

Defines the port number that will be used by HighCharts chart rendering server. Value is a positive integer.

Scope: System

Added in version: 3.7.3 (2013 SR3)


### `com.polarion.httpsTrustAll`

Default value: false

Defines whether Polarion should trust all certificates, regardless of the host name and authority, when accessing resources via https
protocol. This property opens a security hole of a sort, and is provided only for backwards compatibility (older versions always trusted
all). Value is Boolean (true or false).

NOTE: Not all https connections are affected by this property. It applies only to some exports and communication between coordinator
and load balancer in a clustered server setup.

Scope: System

Added in version: 3.8.3 (2014 SR3)


### `com.polarion.javasvndriver.commitRestartDelay`

Default value: 500

Specifies the average delay time before a commit can be restarted because of a resource conflict. Zero (0) or a negative number means
no delay. Value is an integer representing milliseconds. The actual delay is chosen randomly in an interval of 50 to 150% of the time
value specified in this property.

See also: `com.polarion.javasvndriver.commitRestartLimit`

Scope: System

Added in version: 3.17.1 (17.1)


### `com.polarion.javasvndriver.commitRestartLimit`

Default value: 100

Defines the number of times a commit can be restarted if there is a resource conflict. Value is a positive integer.

Scope: System

Added in version: 3.9.3 (2015 SR3)


### `com.polarion.javasvndriver.getchanges.optimizeforspeed`

Default value: true

This is a performance optimization property.

The default value (true) is convenient if you have many projects in Polarion, AND frequent direct commits to SVN outside of Polarion, as
can be the case with a server cluster setup.

This setting will improve the speed of processing these changes in Polarion. Value is Boolean (true or false).

Scope: System

Added in version: 3.4.2


### `com.polarion.javasvndriver.iterateChangesChunkSize`

Default value: undefined

Defines the maximum number of revisions processed all at once during the context initialization phase of reindex operations. If a value
is not set (i.e. is null), then all revisions relevant for a given context are processed at once. Value is a positive integer.

Set this property to some reasonable value (e. g. 100) if you are experiencing Out of Memory (OOM) errors during the context
initialization phase of reindex.

NOTE: Setting this property to low values (e. g. 10) can significantly slow down the context initialization phase.

Scope: System

Added in version: 3.9.1 (2015 SR1)


### `com.polarion.javasvndriver.svnPoolStatsLoggingInterval`

Default value: 100000

Defines how often SVN connection statistics are printed to the main log file. The default value means that statistics print every 100000th
request to acquire a SVN connection.

TIP: The value should not be too low, as it can increase log file size.

Scope: System

Added in version: 3.20.2 (20 R2)


### `com.polarion.jobs.scheduler.dontStartScheduler`

Default value: false

Enables or disables automatic running of the Scheduler during and after Polarion start-up. Enable it if you want to prevent the Scheduler
from running automatically during and after start-up. Value is Boolean (true or false).

Warning: This property has no effect in a cluster setup. For information, see the Deployment and Maintenance Guide, available as a
PDF download in the Polarion product center on Support Center.

Scope: System

Added in version: 3.7.2 (2013 SR2)


### `com.polarion.loadBalancer`

Default value: null

This property contains the URL to the Apache Load Balancer in a clustered server setup. Value is a string. The property is case
insensitive.

NOTE: Due to a typographical error in one release of the setup documentation, both `com.polarion.loadBalancer` and
`com.polarion.loadbalancer` are accepted. If the latter is used, it prints a deprecation warning.

For information on clustered server setup, see the Deployment and Maintenance Guide, available as a PDF download in the Polarion
product center on Support Center.

​

Scope: System

Added in version: 3.9.1 (2015 SR1)


### `com.polarion.loadBalancer.workerUrl`

Default value: None

For Cluster installations:
The URL of an application node. (So that the load balancer knows where to find it.)
Note: Add this property for each node in a cluster.

Examples:

`com.polarion.loadBalancer.workerUrl=http/https://node1.yourdomain.com`

If using AJP:
`com.polarion.loadBalancer.workerUrl=AJP://host`
(Host is the host of the application node.)

Scope: System

Added in version: 3.8.0 (2014)


### `com.polarion.logoURL`

Default value: null

Optional. Defines a custom URL for an image which displays in the Navigation header as the application logo. Value is a
string. Recommended size: 64 x 64 pixels. Types: PNG, JPG.

Scope: System

Added in version: 3.6.3 (2012 SR3)


### `com.polarion.maxNotificationsAboutCreatedTestCases`

Default value: 50

This property causes Polarion to throw away notifications and Activity Stream activities for automated test cases, if the number created
in a single transaction exceeds the configured limit. Value is a positive or negative integer or zero (0).

Negative value means no limit is applied, and all notifications/activities are sent.

Zero value (0) means that no notifications/activities are sent.

Scope: System

Added in version: 3.6.0 (2012)


### `com.polarion.maxNotificationsAboutWorkItemsInCreatedDocument`

Default value: 50

This property causes Polarion to throw away notifications and Activity Stream activities about Work Items created together with a
containing LiveDoc (most likely as part of an import operation),
if the number exceeds the limit specified. Value is a positive or negative integer or zero (0).

A negative value means no limit is applied, and all notifications/activities are sent.

Zero (0) value means that no notification/activities are sent.

Scope: System

Added in version: 3.6.0 (2012)


### `com.polarion.modules.path`

Default value: modules

Defines the root path of Polarion modules (that is, of LiveDoc documents) relative to project root. Value is a string.

Scope: System

Added in version: 3.8.1 (2014 SR1)


### `com.polarion.modules.path.new`

Default value: modules

Defines the new root path of modules (LiveDocs root folder) relative to project root. Default value is the same as the value of
`com.polarion.modules.path`.

If you change this value to something else, all newly created modules will be placed under the new root but backward compatibility is
maintained so that you do not lose documents on legacy locations.

Value is a string.

Scope: System

Added in version: 3.8.1 (2014 SR1)


### `com.polarion.moreTemplatesLink`

Default value: ""

Specify the hyperlink for the Get more templates button in the Create New dialog on the index page of spaces. If the property is not set,
or its value contains an empty string, the button is hidden. Value type is string.

Scope: System

Added in version: 3.7.2 (2013 SR2)


### `com.polarion.notifications.documents.update.maxparagraphs`

Default value: 20

Defines the maximum number of changed paragraphs rendered in a Document updated notification. Prevents notification being overly
long in case of many changes in large Documents. Value is a positive integer.

Scope: System

Added in version: 3.5.0 (2011)


### `com.polarion.placeCommentsDirectly`

Default value: false

Controls the placement of document comments in the Document Editor. Value is Boolean (true or false). If true, then comments are
placed directly under the cursor. If false, comments are placed after current word.

The setting also applies to new comments added in round-trip documents when they are imported to Polarion.

Scope: System

Added in version: 3.6.2 (2012 SR2)


### `com.polarion.plans.calculateResolvedRemainingEstimate`

Default value: true

Used in time-based Plan calculations. Value is Boolean (true or false). If true, then remaining (time) estimate of resolved Work Items is
calculated.

Scope: System

Added in version: 3.10.0 (2016)


### `com.polarion.platform.cpuStatistics`

Default value: true

Enables or disables logging of details of CPU time spent to the TX log. Value is Boolean (true or false).

Example log entry (when property is enabled):
Summary for 'PreloadDataService': Total: 2.42 s, CPU [user: 1.17 s, system: 0.922 s], ...

Scope: System

Added in version: 3.17.1 (17.1)


### `com.polarion.platform.ehcachexml`

Default value: <polarion>/polarion/configuration/ehcache.xml

Defines a custom location for the ehcache.xml file, which is used for configuring EHCache. Useful in multi-instance scenarios when
each instance should have its own configuration. Value is a string.

NOTE: For information on multi-instance setup and configuration, see the Deployment and Maintenance Guide, available as a PDF
download in the Polarion product center on Support Center.

Scope: System

Added in version: 3.7.0 (2013)


### `com.polarion.platform.i18n.forceWrapable`

Default value: false

Governs the placement of words in a line when text is translated from one human language to another. Value is Boolean (true or false).

For example, suppose the German translation of English text results in more words, but it is desired to have the words in the same line,
not multiple lines.

When this property is true, then "zero width space" characters are added to the localization messages which do not contain any space,
after each character.

This is not noticeable to the end user, but it is helpful in testing whether the text is kept in one line.

​

Scope: System

Added in version: 3.8.3 (2014 SR3)


### `com.polarion.platform.internalPG`

Default value: null

Stores the connection string to the integrated PostgreSQL database.

Format: USER:PASSWORD@HOST:PORT
Example: polarion:polarion@localhost:5433
NOTES:
In the past, this property was optional. If not set, the legacy H2 database was used. Starting with version 20 R1 it is required, except in
the unusual case when the following properties are both set:


### `com.polarion.platform.sql.internalDB.head.url`

`com.polarion.platform.sql.internalDB.historical.url`
The value should be set automatically during installation.

Scope: System

Added in version: 3.10.0 (2016)


### `com.polarion.platform.internalPG.maxMultiRowInsertSize`

Default value: 100

Pertains to PostgreSQL operations. Specifies the maximum number of rows inserted by one multi-row insert statement. Value is a
positive integer.

INSERT INTO Struct_TestRun_records VALUES ((?, ?, ?, ?), (?, ?, ?, ?), (?, ?, ?, ?), (?, ?, ?,
?), (?, ?, ?, ?))
Specifying a value that is too big can cause exceptions resulting from a statement that is too big to handle. PostgreSQL requires that
one statement must be fully transferable using one "network chunk" with a limited size (several kilobytes).

Scope: System

Added in version: 3.9.1 (2015 SR1)


### `com.polarion.platform.internalPG.maxTextIndexSize`

Default value: 2048

Sets the maximum size of a String that can be put into a text-like column (in PostgreSQL: text) when such type of column is indexed.

If the String is bigger than the value of this property, the tail is cut off ( substring(0, value) ).

Value is a positive integer or zero (0). If set to 0, then there is no cutoff.

This does not affect the rich text fields (Work Item description, Document home page etc.) as these fields are not indexed in the
database.

NOTES:
PostgreSQL has a type 'text' which allows storing a String of unlimited size, but the index imposes an upper boundary on the size
of a String to be indexed (2048 in PostgreSQL 8.4).

Thus, if you have an indexed column of type 'text', you will not be able to put there a String bigger than 2048 bytes.

Default value is the PostgreSQL maximum as of version 8.4.


Scope: System

Added in version: 3.9.2 (2015 SR2)


### `com.polarion.platform.loggingServiceInterceptor.enabled`

Default value: true

Enable or disable the logging of time spent in Hivemind service interceptors in cases when it would cause problems. Value is Boolean
(true or false). The property has no effect when there are no interceptors configured. Interceptors are configured like this:
```
<service-point id="DSInterceptorFactory" interface="org.apache.hivemind.ServiceInterceptorFactory"
visibility="private">
<invoke-factory>
<construct class="com.polarion.fme.workitemsave.actions.DSInterceptorFactory">
</construct>
</invoke-factory>
</service-point>
<implementation service-id="com.polarion.platform.persistence.dataservice.dataService">
<interceptor service-id="DSInterceptorFactory" />
</implementation>
```

Scope: System

Added in version: 3.10.1 (2016 SR1)


### `com.polarion.platform.memoryStatistics`

Default value: true

Enables or disables logging of allocated memory to the TX log. It is an amount of the memory allocated by the execution of a given
operation.

Therefore, it is not an amount which stays allocated after the operation is executed.

Actually, none or very small fraction of that might stay in the memory after the operation is executed. Value is Boolean (true or false).

Example log entry (item resulting from true value in this property shown as bold):
Summary for 'PreloadDataService': Total: 1.55 s, CPU [user: 0.734 s, system: 0.75 s], Allocated
memory: 622.8 MB,
transactions: 8, svn: 1.21 s [57% getFile content (158x), 40% getDir2 content (89x)] (265x),
RepositoryConfigService: 0.615 s [97% getReadConfiguration (576x)] (668x), resolve: 0.345 s [67% Category (30x), 19% User
(8x)] (47x),
ObjectMaps: 0.0884 s [46% getPrimaryObjectLocation (43x), 28% getLastPromoted (43x), 27%
getPrimaryObjectProperty (43x)] (175x)

Scope: System

Added in version: 3.17.3 (17.3)


### `com.polarion.platform.monitoring.notifications.disabled`

Default value: false

Disables Polarion monitoring email notifications regarding available disk space:
Note: Setting this parameter to true will stop monitoring emails, even if they are configured in the following property.

(Set this property to false to enable monitoring notifications to be sent to emails configured in the following property.)

`com.polarion.platform.monitoring.notifications.receivers`

Scope: System

Added in version: 3.1.0


### `com.polarion.platform.monitoring.notifications.freeSpacePercent`

Default value: 5

Controls when notifications about low disk space are triggered. Value is an integer representing a percentage zero to 100 (0 -100).

When free disk space is less than the specified value, notifications are sent to the email addresses of all users assigned the global

administrator role.

NOTE: It is important that all global administrators have a valid email address in their user profile.

Scope: System

Added in version: 3.9.0 (2015)


### `com.polarion.platform.monitoring.notifications.receivers`

Default value: none

Configure email addresses (separated by commas) that should receive notifications regarding available disk space:
A warning message is sent if the available free disk space is running low.

By default, notifications are sent when free disk space:
is less than 5%
is less than 1 GB
less than 100 MB
(You can set the free disk space limit in the `com.polarion.platform.monitoring.notifications.freeSpacePercent`
property.)

Notes:
- `com.polarion.platform.monitoring.notifications.receivers` must be configured with at least one email address.
- `com.polarion.platform.monitoring.notifications.disabled` must be set to false
- (Optional) Add a sender to the notifications with: `com.polarion.platform.monitoring.notifications.sender`
- (Optional) Add a prefix to the subject line of notification emails with: `com.polarion.platform.monitoring.notifications.subject.prefix`

Scope: System

Added in version: 3.1.0


### `com.polarion.platform.monitoring.notifications.sender`

Default value: none

Set sender information (for example, polarion_monitoring@your_company.com) for monitoring notification emails.

(See `com.polarion.platform.monitoring.notifications.receivers` for information on the kind of monitoring notification
emails that get sent.)

Notes:
- `com.polarion.platform.monitoring.notifications.receivers` must be configured with at least one email address.
- `com.polarion.platform.monitoring.notifications.disabled` must be set to false
- (Optional) Add a prefix to the subject line of notification emails with: `com.polarion.platform.monitoring.notifications.subject.prefix`

Scope: System

Added in version: 3.1.0


### `com.polarion.platform.monitoring.notifications.subject.prefix`

Default value: none

Set a prefix that's automatically added to the beginning of the Subject line for monitoring notification emails.

(See `com.polarion.platform.monitoring.notifications.receivers` for information on the kind of monitoring notification
emails that get sent.)
Notes:
- `com.polarion.platform.monitoring.notifications.receivers` must be configured with at least one email address.
- `com.polarion.platform.monitoring.notifications.disabled` must be set to false
- (Optional) Add a sender to the notifications with: `com.polarion.platform.monitoring.notifications.sender`


Scope: System

Added in version: 3.1.0


### `com.polarion.platform.notificationsSynchronizationCleanupInterval`

Default value: 60

The time interval for cleaning out old revisions from a cluster-wide cached list of unprocessed events. Value is a positive integer
and used only in a clustered server setup.

NOTE: For information, see the Deployment and Maintenance Guide, available as a PDF download in the Polarion product center
on Support Center.

Scope: System

Added in version: 3.17.1 (17.1)


### `com.polarion.platform.notificationsSynchronizationCleanupThreshold`

Default value: 100

Specifies the number of revisions that are left in the cluster-wide cached list of unprocessed events. Value is a positive integer and only
used in a clustered server setup.

NOTE: For information, see the Deployment and Maintenance Guide, available as a PDF download in the Polarion product center
on Support Center.

Scope: System

Added in version: 3.17.1 (17.1)


### `com.polarion.platform.numOfPullingJobWorkers`

Default value: (see Description)

Configures how many worker threads can be used by the PullingJob when it indexes revisions done outside of Polarion. (Done by
some other node in a cluster, for example.)
The default value is taken from the `com.siemens.polarion.objectindexing.runtimeWorkers` property and is the same
number of threads used during Data Object Indexing.

If the value is set to 1, then revisions are processed on the PullingJob thread with no async behavior.

NOTE: For information, see the Deployment and Maintenance document, available as a PDF download in the Polarion product center
on Support Center.

Scope: System

Added in version: 3.9.3 (2015 SR3)


### `com.polarion.platform.numOfWorkersNotifications`

Default value: 1 + availableProcessors / 2

Number of worker threads for creating notifications and Activity Stream activities.

Value is a positive integer or zero (0). The maximum number of automatically selected workers based on the number of processors is 8.

Setting to zero (0) returns it to the original state where the activities and notifications are created by the "Persistence Events Processing
Thread".

Scope: System

Added in version: 3.17.1 (17.1)


### `com.polarion.platform.persistence.IAuthSrcPermissionService.allowed`

Default value: true

Controls whether AuthSrcPermissionService is used or not. Value is Boolean (true or false). If true, then instances of some prototypes
(Module, Work Item, for example) are checked to determine whether the current user has access rights to the proper SVN location,
according to the access file.

Set this property to false if you want to turn this feature off - when the access file is not available, for example.


Scope: System

Added in version: 3.5.0 (2011)


### `com.polarion.platform.persistence.notifications.disabled`

Default value: true

Set this property to false to enable email notifications and the sending of bug reports.

Configure bug report notifications:
1. Set `com.polarion.platform.persistence.notifications.disabled` to false
2. Add or uncomment and configure the following properties in the polarion.properties file:
```
announcer.smtp.host=<name or IP of an accessible SMTP host>
announcer.smtp.port=<port number of the SMTP host> (25 is the default)
(Optional) announcer.smtp.auth=<false|true> (Set it to true if your SMTP host requires authentication.)
announcer.smtp.user= SMTP host username (Required if announcer.smtp.auth=true.)
announcer.smtp.password=SMTP host username's password. (Required if announcer.smtp.auth=true.)
```

Scope: System

Added in version: 3.0.0


### `com.polarion.platform.repository.accessFileEncoding`

Default value: System dependent (see Description)

Optionally specify a non-default encoding of the Subversion access file. You may need to do this if there are paths or group names
containing national language characters in the access file, AND the default system file encoding cannot handle them.

NOTE: The default value is the value of the Java system variable file.encoding on the host system.

Scope: System

Added in version: 3.4.3


### `com.polarion.platform.repository.canHaveEmptyRolesInSvnAccessFile`

Default value: true

Set this property to address a Subversion 1.10 bug that does not allow for empty roles in the SVN access file prior to SVN's July 24th,
2019 update.

When set to false, creating and editing user roles in Administration will enforce having at least one user in each role, adding the current
user by default.

Creating a new project will also include the current user in each initial role if none is predefined in the project template by default.

Note: The issue was already fixed in SVN version 1.10.6 (July 24th, 2019 update) but you can set this property to false if you still
experience an issue.

When false, a dummy user is automatically assigned to every Group. (It's only visible in the SVN access file.)
IMPORTANT!
Do not delete this dummy user (ID=KF9Nrsnp9Ad) from the SVN access file, or create a user with the same name.

​

Scope: System

Added in version: 3.19.2 (19.2)


### `com.polarion.platform.repository.passwdFileEncoding`

Default value: (see Description)

Enables you to specify the encoding of the passwd and passwd_credentials files.

Useful when those files contain usernames and passwords with national characters, AND the default system file encoding cannot
handle them.

The default value is system dependent. The value of the Java system variable file.encoding is used. Value is a string.


Scope: System

Added in version: 3.17.0 (17)


### `com.polarion.platform.security.cacheSize`

Default value: 20000

Defines the size of the cache for security objects. Recommended value is the total number of all users. Value is a positive integer.

Scope: System

Added in version: 3.6.1 (2012 SR1)


### `com.polarion.platform.sql.doNotIndexWIsCommentsInHistory`

Default value: false

Controls whether or not Work Item comments are indexed in History. Value is Boolean (true or false). If true, then the comments are
not indexed.

Scope: System

Added in version: 3.6.3 (2012 SR3)


### `com.polarion.platform.sql.internalDB.head.url`

Default value: null

Stores the JDBC URL to the internal HEAD database. Only PostgreSQL is now supported, so the value must begin with:
jdbc:postgresql:
Setting this property provides the possibility to have HEAD and historical databases on different computers. It is used only when
property `com.polarion.platform.internalPG` is not set.

Note: While having PostgreSQL on a different machine than the Polarion server is possible, it is not officially supported.

Scope: System

Added in version: 3.10.0 (2016)


### `com.polarion.platform.sql.internalDB.historical.url`

Default value: null

Stores the JDBC URL to the internal historical database. Only PostgreSQL is now supported, so the value must begin
with: jdbc:postgresql:
Setting this property provides the possibility to have historical and HEAD databases on different computers. It is used only
when property `com.polarion.platform.internalPG` is not set.

Note: While having PostgreSQL on a different machine than the Polarion server is possible, it is not officially supported.

Scope: System

Added in version: 3.10.0 (2016)


### `com.polarion.platform.sql.invalidCommands`

Default value: "CHR", "CHAR", "PG_SLEEP", "ABORT_SESSION", "ARRAY_GET", "CARDINALITY", "ARRAY_CONTAINS",
"ARRAY_CAT", "ARRAY_APPEND", "ARRAY_MAX_CARDINALITY", "TRIM_ARRAY", "ARRAY_SLICE", "AUTOCOMMIT",
"CANCEL_SESSION", "CASEWHEN", "COALESCE", "CONVERT", "CURRVAL", "CSVWRITE", "CURRENT_SCHEMA",
"CURRENT_CATALOG", "DATABASE_PATH", "DATA_TYPE_SQL", "DB_OBJECT_ID", "DB_OBJECT_SQL", "DECODE",
"DISK_SPACE_USED", "SIGNAL", "ESTIMATED_ENVELOPE", "FILE_READ", "FILE_WRITE", "GREATEST", "LEAST",
"LOCK_MODE", "LOCK_TIMEOUT", "MEMORY_FREE", "MEMORY_USED", "NEXTVAL", "NULLIF", "NVL2", "READONLY",
"ROWNUM", "SESSION_ID", "SET", "TRANSACTION_ID", "TRUNCATE_VALUE", "CURRENT_PATH", "CURRENT_ROLE",
"CURRENT_USER", "H2VERSION"

For security reasons, the following list of SQL commands is prevented in SQL queries in Polarion. If attempted, they throw an exception
and are not executed.

If not configured, the following default list is used:

"CHR", "CHAR", "PG_SLEEP",
"ABORT_SESSION", "ARRAY_GET", "CARDINALITY", "ARRAY_CONTAINS", "ARRAY_CAT",
"ARRAY_APPEND", "ARRAY_MAX_CARDINALITY", "TRIM_ARRAY", "ARRAY_SLICE", "AUTOCOMMIT",
"CANCEL_SESSION", "CASEWHEN", "COALESCE", "CONVERT", "CURRVAL", "CSVWRITE",
"CURRENT_SCHEMA", "CURRENT_CATALOG", "DATABASE_PATH", "DATA_TYPE_SQL", "DB_OBJECT_ID",
"DB_OBJECT_SQL", "DECODE", "DISK_SPACE_USED", "SIGNAL", "ESTIMATED_ENVELOPE", "FILE_READ",
"FILE_WRITE", "GREATEST", "LEAST", "LOCK_MODE", "LOCK_TIMEOUT", "MEMORY_FREE", "MEMORY_USED",
"NEXTVAL", "NULLIF", "NVL2", "READONLY", "ROWNUM", "SESSION_ID", "SET", "TRANSACTION_ID",
"TRUNCATE_VALUE", "CURRENT_PATH", "CURRENT_ROLE", "CURRENT_USER", "H2VERSION"
Mind the possible security impact when allowing any additional SQL commands.

​

Scope: System

Added in version: 3.22.2 (22 R2)


### `com.polarion.platform.sql.maxBaselineSchemasKept`

Default value: 50

Defines the maximum number of baseline schemata that are kept simultaneously in the database. Value is a positive integer. If
exceeded, then the LRU algorithm is used to determine which schema is to be deleted.

Scope: System

Added in version: 3.8.2 (2014 SR2)


### `com.polarion.platform.sql.pgPort`

Default value: 5435

Defines the TCP port on which the built-in PostgreSQL-like server is listening. Value is a positive integer. This internal H2's PG server is
used since version 3.10.0 for the DBlink connection to Polarion's Lucene from the external PostgreSQL database. Scripts that configure
the PostgreSQL connection to Polarion do not take this configuration into account and always presume that it is running on default port
5435.

Scope: System

Added in version: 3.6.2 (2012 SR2)


### `com.polarion.platform.sql.populateEnumOptionsTable`

Default value: false

Controls whether refreshing of enumerations in a database job will be started as part of the data pre-loading phase. Value is Boolean
(true or false). Value false means to skip it.

Scope: System

Added in version: 3.17.3 (17.3)


### `com.polarion.platform.sql.searchSizeLimit`

Default value: 1000000

Defines the maximum SQL result size to prevent Out of Memory (OOM) errors. Value is bytes.

Scope: System

Added in version: 3.6.0 (2012)


### `com.polarion.platform.sql.synchronousAttachmentIndexingAlways`

Default value: false

Controls whether or not attachments are indexed asynchronously. Value is Boolean (true or false). If set to true, the attachments are
indexed synchronously.

Scope: System

Added in version: 3.7.0 (2013)


### `com.polarion.platform.sql.synchronousHistoryCreation`

Default value: false

Controls whether or not the History in the internal database is indexed synchronously during re-indexing. Value is Boolean (true or
false). If set to true, the history is indexed synchronously.

Scope: System

Added in version: 3.5.3 (2011 SR3)


### `com.polarion.platform.sql.useNewStructTables`

Default value: false

Value is Boolean (true or false). If you have very large manual Test Runs, the default system configuration can result in excessive
numbers of Test Run records in the historical database because it uses the default referencing of structures via a foreign key. You can
remedy this situation by setting this property to true, which ensures that artificial primary keys (PK) are generated for Test Run records,
resulting in far fewer records in the historical database.

NOTE: After changing the setting of this property it is necessary to reindex the system to rebuild the database. For more information,
see the online Help topic Index and Reindex.

Scope: System

Added in version: 3.8.3 (2014 SR3)


### `com.polarion.platform.sql.useStringPKs`

Default value: false

Defines type of C_PK, C_URI and FK_* columns in PostgreSQL database. Value is Boolean (true or false). Value set to false means
the columns are of type BIGINT, otherwise they are of type VARCHAR. Does not affect the legacy H2 database, as these columns are
always strings (VARCHAR).

Scope: System

Added in version: 3.10.1 (2016 SR1)


### `com.polarion.platform.subterraURITableCacheSize`

Default value: 250000

Defines the size of the cache used for translating numeric PKs to URIs. Value is a positive integer representing bytes. It should be
increased if the TX log shows high time spent in SubterraURITable. Each entry can take up to 1KB of memory so it should not be
increased too much.

Scope: System

Added in version: 3.10.1 (2016 SR1)


### `com.polarion.platform.threadStatistics`

Default value: false

Enables or disables logging of details of thread contention statistics to the TX log.

Example log entry:
... Thread: 0.00000136 s [100% waited (5x)] (5x), ...

WARNING: Enabling this property has caused significant system performance degradation in some performance tests. It is
recommended to disable it after getting the log data you need for analysis.

Scope: System

Added in version: 3.17.1 (17.1)


### `com.polarion.platform.tomcatSessionTimeout`

Default value: 30

Specifies the time (in minutes) after which session timeout occurs in the Tomcat web server.

Scope: System

Added in version: 3.10.0 (2016)


### `com.polarion.platform.transaction.timeout`

Default value: 3600

Specifies the period of time after which transactions time out. Value is a positive integer representing seconds. The default value
represents one hour.

Scope: System

Added in version: 3.0.0


### `com.polarion.platform.txLoggingOfFieldPermissions.enabled`

Default value: false

Enables or disables logging of time spent in checking per-field permissions. Value is Boolean (true or false).

NOTE: Tests have shown that enabling this property causes some small performance degradation. It is recommended to enable it
temporarily if you need to capture this aspect of your system to the logs.

Scope: System

Added in version: 3.10.1 (2016 SR1)


### `com.polarion.print.disableStretchedFooter`

Default value: false

Controls the placement of footer during Work Item printing. Value is Boolean (true or false).

If set to true and Work Item print is used, then the footer is placed immediately after Work Item content. (Footer will not be aligned to the
end of the document).

Scope: System

Added in version: 3.5.2 (2011 SR2)


### `com.polarion.purevariants.optimisticMultithreading`

Default value: false

Value is Boolean (true or false). If true, use a single ConsulCorePlugin instance to do all communication with Pure Variants server.


Pertains to variant management using the Polarion VARIANTS add-on and the PureVariants server. For information about the feature,
see Polarion online Help topic Managing Variants.

Scope: System

Added in version: 3.9.0 (2015)


### `com.polarion.purevariants.server.disabled`

Default value: false

Enables or disables automatic startup of the Pure Variants server. Value is Boolean (true or false).

Pertains to variant management using the Polarion VARIANTS add-on and the PureVariants server. For information about the feature,
see Polarion online Help topic Managing Variants.

Scope: System

Added in version: 3.9.0 (2015)


### `com.polarion.purevariants.server.home`

Default value: $[com.polarion.home]/bundled/purevariants

Stores the path to the installation folder of Pure Variants server. Value is a string.

Pertains to variant management using the Polarion VARIANTS add-on and the PureVariants server. For information about the feature,
see Polarion online Help topic Managing Variants.

Scope: System

Added in version: 3.9.0 (2015)


### `com.polarion.purevariants.server.log.file`

Default value: $[com.polarion.data]/logs/purevariants.log

Stores the path to the log file used by the Pure Variants server. Value is a string.

Pertains to variant management using the Polarion VARIANTS add-on and the PureVariants server. For information about the feature,
see Polarion online Help topic Managing Variants.

​

Scope: System

Added in version: 3.9.0 (2015)


### `com.polarion.purevariants.server.log.level`

Default value: 0

Defines the log-level used by the Pure Variants server. Value is a positive integer or zero (0).

Pertains to variant management using the Polarion VARIANTS add-on and the PureVariants server. For information about the feature,
see Polarion online Help topic Managing Variants.

Scope: System

Added in version: 3.9.0 (2015)


### `com.polarion.purevariants.server.port`

Default value: 4711

Defines the default port number used by the Pure Variants server. Value is a positive integer.

Pertains to variant management using the Polarion VARIANTS add-on and the PureVariants server. For information about the feature,
see Polarion online Help topic Managing Variants.

Scope: System

Added in version: 3.9.0 (2015)


### `com.polarion.purevariants.server.projects.data.folder`

Default value: $[com.polarion.data]/purevariants

Stores the path to the data folder used by the Pure Variants server. Value is a string.

Pertains to variant management using the Polarion VARIANTS add-on and the PureVariants server. For information about the feature,
see Polarion online Help topic Managing variants.

Scope: System

Added in version: 3.9.0 (2015)


### `com.polarion.purevariants.singleThreaded`

Default value: false

Controls thread requests in the Pure Variants backend server. Value is Boolean (true or false). If true, the backend server will only
process one request at a time.

Pertains to variant management using the Polarion VARIANTS add-on and the PureVariants server. For information about the feature,
see Polarion online Help topic Managing variants.

Scope: System

Added in version: 3.9.0 (2015)


### `com.polarion.repository.pollingPeriod`

Default value: 5000

Defines the polling period of external repositories. Value is milliseconds.

Scope: System

Added in version: 3.5.2 (2011 SR2)


### `com.polarion.repositorySessionTimeout`

Default value: 600

Repository session timeout in seconds. This timeout is checked periodically based on the value set in
property `com.polarion.repositorySessionTimeoutCheckInterval`.

Scope: System

Added in version: 3.7.2 (2013 SR2)


### `com.polarion.repositorySessionTimeoutCheckInterval`

Default value: 180

Repository session timeout check interval in seconds. Defines how often repositories are checked for timeout as defined in
property `com.polarion.repositorySessionTimeout`.

Scope: System

Added in version: 3.7.2 (2013 SR2)


### `com.polarion.reqif.archiveCharset`

Default value: Cp437

Specifies the character set used to encode/decode the names of entries in ZIP archive files used with ReqIF Import/Export. Value is a
string.

NOTE: The default value is correct according to the ZIP specification. However, different encoding may be commonly used in some
countries.

For more information about the feature, see Polarion online Help topic ReqIF Import/Export.

Scope: System

Added in version: 3.8.3 (2014 SR3)


### `com.polarion.reqif.bulkLoadTemplateEnabled`

Default value: false

Value is Boolean (true or false). If set to true a dialog is displayed to end-users that allows the application of a template to all
specifications that are currently being imported or exported.

Pertains to the ReqIF import/export feature. For more information about the feature, see Polarion online Help topic ReqIF Import/Export.

Scope: System

Added in version: 3.9.2 (2015 SR2)


### `com.polarion.richPages.maxNumberOfPointInLineChart`

Default value: 1000

Defines the maximum number of points in line charts in Pages (LiveReport, Info). Value is a positive integer.

For more information about the feature, see Polarion online Help topic Work with Pages.

Scope: System

Added in version: 3.9.0 (2015)


### `com.polarion.scripting.allowedSecurityServiceMethods`

Default value: none

Used to unblock methods in script calls that are blocked by default.

Accepted Values: Comma-separated method names and the wildcard *.

Examples:
```
com.polarion.scripting.allowedSecurityServiceMethods=addGlobalRoleToUser
(addGlobalRoleToUser is allowed and other methods are blocked when called from scripts.)
com.polarion.scripting.allowedSecurityServiceMethods=*
(All methods are allowed when called from scripts.)
```
Scope: System

Added in version: 3.23.4 (2304 - current)


### `com.polarion.scripting.job.allowedSecurityServiceMethods`

Default value: none

Used to unblock methods in script calls that are blocked by default.

Accepted Values: Comma-separated method names and the wildcard *.

Examples:
```
com.polarion.scripting.job.allowedSecurityServiceMethods=addGlobalRoleToUser
(addGlobalRoleToUser is allowed and other methods are blocked when called from scripts inside a job.)
com.polarion.scripting.job.allowedSecurityServiceMethods=*
(All methods are allowed when called from scripts.)
```
Scope: System

Added in version: 3.23.4 (2304 - current)


### `com.polarion.scripting.servlet.enabled`

Default value: false

Provides system-level control over use of scripting servlet. Scripting servlet is also controlled by permissions. Value is Boolean (true or
false).

Set this property to true if you want to enable use of scripting servlet.

Scope: System

Added in version: 3.9.0 (2015)


### `com.polarion.security.enablePerFieldSecurity`

Default value: true

Enables or disables per-field security features. Value is Boolean (true or false). Set this property to false only if you want to disable perfield security features, especially the read-deny.

NOTE: Enabled per-field security can have negative performance impact on some use cases, such as time matrix.

Scope: System

Added in version: 3.8.3 (2014 SR3)


### `com.polarion.showOutlineNumberBeforeTitle`

Default value: false

Value is Boolean (true or false). If set to true, Polarion displays outline numbers before title.


Scope: System

Added in version: 3.6.0 (2012)


### `com.polarion.startup.workers`

Default value: Number of processor cores

Defines the number of workers (threads) used during a reindex, the execution of the AttachmentIndexer and DBHistoryCreator
jobs, and the application server startup.

It can also be defined for individual reindex phases via the following property:

`com.polarion.startup.workers.phase#`

Applies to phases:
- Context initialization - phase 3 of startup
- Data indexing - phase 7 of startup
- Application server startup - phase 9 of startup
	- The property sets how many applications can be run in parallel in the Tomcat application server.
	- The property should be set to a value greater than 1 if you run Polarion in cluster mode.
- Attachment indexing - phase 10 of startup (AttachmentIndexer job)
- Historical indexing - phase 11 of startup (DBHistoryCreator job)

Scope: System

Added in version: 3.7.2 (2013 SR2)


### `com.polarion.subterra.ObjectIndex.batchLimit`

Default value: 100

When objects are indexed during the "Data indexing" phase of reindex, they are divided into batches to prevent OutOfMemory (OOM)
errors.

This property specifies the size of such batches. Value is a positive integer representing number of objects.

You can try to set the value lower if you are getting OOM errors during phase 7 of reindex or during the DB History Creator job.

Batch size:
- Common objects = batchLimit x 1
- Revision = batchLimit x 100
- Test Run = batchLimit / 10

Scope: System

Added in version: 3.8.0 (2014)


### `com.polarion.synchronizer.commitChunkSize`

Default value: 500

Defines the size of chunks in which Work Items are committed when creating or updating Work Items during ReqIF or RIF
synchronization. Value is a positive integer representing number of Work Items.

Scope: System

Added in version: 3.9.1 (2015 SR1)


### `com.polarion.titleQueriesExpansionEnabled`

Default value: false

Value is Boolean (true or false). If true, Polarion alters Work Item queries so that whenever the title field is searched for, field title.1 is
also taken into account.

Roughly speaking, this means that Polarion then replaces subqueries title:XXX with subqueries title:XXX OR title.1:XXX.

Scope: System

Added in version: 3.6.0 (2012)


### `com.polarion.tracker.allowLinkingWorkItemByOutlineNumber`


Default value: true

This property enables or disables searching of the Outline Number Index when linking Work Items. Value is Boolean (true or false).

Example: `com.polarion.tracker.allowLinkingWorkItemByOutlineNumber=true`
Scope: System

Added in version: 3.9.1 (2015 SR1)


### `com.polarion.tracker.disableResolvedOnSetting`

Default value: false

Enables or disables automatic setting or clearing of the resolvedOn field of Work Items when the resolution field is being set or
cleared. Value is Boolean (true or false).

Scope: System

Added in version: 3.5.2 (2011 SR2)


### `com.polarion.txwatchdog.delay`

Default value: -1

"TX Watchdog" (or ThreadDumper) watches out for transactions that take too long. Whenever such a transaction occurs, stack traces of
all threads in the system are logged on INFO level.

This property defines how much time is "too long" for a transaction: Value is in milliseconds.

Thus, a value of 120000 means that transactions that take more than 2 minutes are too long, and logging occurs.

A value of -1 in this property disables this logging.

NOTES:
- Web services transactions are affected
- Administrators can manually trigger thread dumps via a button in the Maintenance page of Administration.

See also: `com.polarion.txwatchdog.period`
​

Scope: System

Added in version: 3.5.0 (2011)


### `com.polarion.txwatchdog.period`

Default value: -1

"TX Watchdog" (or ThreadDumper) watches out for transactions that take too long. Whenever such transaction occurs, stack traces of
all threads in the system are logged on INFO level.

This property defines how often this logging should happen. Value is in milliseconds.

Thus, a value of 60000 means that logging will occur once per minute for any single transaction that is taking too long.

A value of -1 in this property disables this logging.

NOTES:
- Web services transactions are affected.
- Administrators can manually trigger thread dumps via a button in the Maintenance page of Administration.

See also: `com.polarion.txwatchdog.delay`
​

Scope: System

Added in version: 3.5.0 (2011)


### `com.polarion.ui.bulkEditBatchSize`

Default value: 500

To handle changes to large numbers of Work Items, such as my occur with the Bulk Edit feature, scripts, jobs, etc. it is possible to split
the change into multiple commits of smaller batches of items,
if necessary. This property defines the batch size - i.e. the number of Work Items. Value is an integer.


The number of Work Items in a commit (batch size) cannot be zero (0).

A value of -1 means that all changed Work Items are processed in one transaction, with potential impact on system performance
for the duration of the processing.

Scope: System

Added in version: 3.10.0 (2016)


### `com.polarion.ui.bulkEditRestrictedLimit`

Default value: 100

Controls the maximum number of Work Items that can be edited using normal Bulk Edit. Value is a positive integer. If more than the
specified maximum are selected, "Restricted" Bulk Edit is activated. A panel of options is then shown to end users, and the word
"Restricted" appears on the Bulk Edit button, which leads to a limited view in which the user can edit field values, but the current values
are not loaded in order to optimize server performance for all users.

Scope: System

Added in version: 3.10.0 (2016)


### `com.polarion.ui.defaultQuery`

Default value: NOT HAS_VALUE:resolution

Specifies the system-wide default query for the Work Items table. Value is a string. Used when end users select Work Items in
Navigation and no overriding user-defined query is configured.

NOTE: This default query is applied within the scope where the user is currently working: project, project group, or Repository. The
default value of this property queries for all unresolved Work Items.

Scope: System

Added in version: 3.10.0 (2016)


### `com.polarion.ui.diagrams.fonts`

Default value: null

Defines a list of fonts to be shown in the Diagram Editor. Value is a string, specified as a comma-separated list of font names, e.g.

"Helvetica,Verdana".

The first font is the list will become the default font. If this property is not set, a default list of fonts is used, consisting of: Helvetica,
Verdana, Times New Roman, Garamond, Comic Sans MS, Courier New, Georgia, Lucida Console and Tahoma, and the default font is
Helvetica.

Scope: System

Added in version: 3.7.0 (2013)


### `com.polarion.ui.document.lazyLoad`

Default value: true

"Lazy-loading" means that the Work Items contained in a LiveDoc Document, and their content, are loaded "on demand" as the user
scrolls in the Document Editor, rather than loading all contained Work Items when the user opens the Document. This is the default
system behavior, as it can significantly improve performance and reduce wait time, especially for large LiveDocs containing many Work
Items.

However, it is possible for individual users to enable/disable lazy-loading in each specific Document. This property controls whether or
not the UI control for this (i.e. on/off buttons) is shown to users in the in Document Properties panel. Value is Boolean (true or false). If
true, the control is visible, the user's choice is applied to the currently open LiveDoc for that user only, and the setting persists until
changed. If false, the control is hidden, lazy-loading is always enabled and users cannot disable it.

Scope: System

Added in version: 3.10.1 (2016 SR1)


### `com.polarion.ui.documentCompare.workItemsLimit`

Default value: 1000

When users invoke the Compare feature while editing a LiveDoc Document, the default compare view loaded is Document. In this view,
all elements are compared (headings, images, etc.), not just Work Items. However, this view is slower to load than the compare views
for Work Items and Fields. In larger LiveDocs containing many items, this can force a much longer wait time on users who only want to
compare Work Items or Fields, not waiting for the Document compare view to load before they can choose that compare view.

This property defines the maximum number of Work Items a LiveDoc can contain and still present the Document compare view
immediately when users invoke the Compare feature. Value is a positive integer. When this maximum is exceeded, a intermediate page
displays enabling the user to choose which compare view to load: Document or Work Items.

Factors to consider when setting this property include server and network resources, common size of LiveDocs and compare view most
often needed by your end users.

Scope: System

Added in version: 3.10.0 (2016)


### `com.polarion.ui.lock.timeout`

Default value: 480

Defines the timeout in minutes for locking of diagrams in the Diagram Editor. Value is a positive integer.

NOTES:
User who opens a diagram obtains a lock with timeout as set in this property.

User attempting to open a locked diagram is notified with info about who locked it and when.

Lock is "soft" - another user can override it and obtain their own lock.

If this property is not set in the properties file, the default value is used.

Scope: System

Added in version: 3.7.0 (2013)


### `com.polarion.ui.login.resetPasswordLinkLabel`

Default value: null

Specify link text to display on the Polarion portal login page, leading to your password reset page. Value is a string. You must also set
the `com.polarion.ui.login.resetPasswordLinkLabel` property.

Example:
com.polarion.ui.login.resetPasswordLinkLabel=Reset Password
For more information, see online Help topic Enable users to reset password.

Scope: System

Added in version: 3.9.1 (2015 SR1)


### `com.polarion.ui.login.resetPasswordLinkURL`

Default value: null

Optionally specify the URL of a page on your system that you have provided for users to reset their password. Value is a string.

IMPORTANT: You must also set the `com.polarion.ui.login.resetPasswordLinkLabel` property.

Example:
com.polarion.ui.login.resetPasswordLinkURL=http://www.mydomain.com/user/recoverpw.php
For more information, see online Help topic Enable users to reset password.

Scope: System

Added in version: 3.9.1 (2015 SR1)


### `com.polarion.ui.maxRenderedItemsInCombo`

Default value: 100

Defines the maximum number of items rendered in the combo box and bubble query controls in the user interface. Value is a positive
integer. Allowing too many items can adversely impact performance. The default value has proved optimal for many installations, but
there is no hard and fast rule. Factors such as the number of users, amount of memory, and settings of other configuration options can
all affect overall performance. If the property is not included in the Polarion Configuration, by default in the combo box and bubble
query there are 100 items visible.

Scope: System

Added in version: 3.9.1 (2015 SR1)


### `com.polarion.ui.maxRenderedItemsInGroupsDialogs`

Default value: 100
Defines the maximum number of items shown in the Add Users and Add Global Roles dialog boxes on the Groups administration
page.

Value is a positive integer. Note that setting a value significantly higher than the default can negatively affect performance, and lead to
long data loading times.

​

Scope: System

Added in version: 3.20.1 (20 R1)


### `com.polarion.ui.richText.fonts`

Default value: ""

Specifies a custom list of fonts available in rich text type fields and edit controls and the Document Editor, and font substitution (which
on import or paste replaces certain fonts with fonts available in the Polarion system). Value is a string. Specify available fonts as a
semicolon-delimited list. Delimit font substitutions within each list item using a comma (see example).

Example:
```
com.polarion.ui.richText.fonts=Arial, Helvetica; "Courier New", Georgia, Garamond;
```
The above specifies a custom list of fonts that includes only Arial and Courier New fonts with the following substitutions:
- Helvetica is substituted by Arial
- Georgia and Garamond are substituted by Courier New

Scope: System

Added in version: 3.7.2 (2013 SR2)


### `com.polarion.ui.richText.fonts.append`

Default value: false

This property works in conjunction with DPP-90628 - `com.polarion.ui.richText.fonts`.

The default Polarion font set is extended with newly configured fonts when set to true. Otherwise, it is replaced.

Scope: System

Added in version: 3.22.1 (22 R1)


### `com.polarion.ui.table.hardLimit`

Default value: 10000

Specifies the hard limit for the number of items displayed in the Work Items table (tracker) and various others (users, projects, etc).

Tables will never display more items than this limit. Value is a positive integer.

​

Scope: System

Added in version: 3.9.2 (2015 SR2)


### `com.polarion.ui.timeSheet.hardLimit`

Default value: 10000

Specifies the maximum number of cells that can be displayed for editing in the Time Sheet view of Work items.


See also: `com.polarion.ui.timeSheet.softLimit`

Scope: System

Added in version: 3.7.3 (2013 SR3)


### `com.polarion.ui.timeSheet.softLimit`

Default value: 2000

Specifies the soft limit for the number of cells rendered in the Time Sheet view of Work Items. Value is a positive integer. If the number
of cells exceeds this limit, then a confirmation dialog informs the user that rendering of the table may take long time and provides the
option to cancel.

See also: `com.polarion.ui.timeSheet.hardLimit`

Scope: System

Added in version: 3.7.3 (2013 SR3)


### `com.polarion.ui.treeTable.hardLimit`

Default value: 100000

The configurable hard limit for the total number of items in the tree that can be displayed in the view.

If the user does not accept the soft limit `com.polarion.ui.treeTable.softLimit`, then the tree will be limited to the
`com.polarion.ui.treeTable.hardLimit` number of total items.

NOTE: Before 3.20.2 (20 R2), this property only limited the number of root items in the tree view, not the total, and the default value was
10000.

Scope: System

Added in version: 3.7.2 (2013 SR2)


### `com.polarion.ui.treeTable.softLimit`

Default value: 5000

The configurable soft limit for the total number of items in the tree when a user gets a confirmation dialog for constructing the whole tree.

NOTE: Before 3.20.2 (20 R2), this property only limited the number of root items in the tree view, not the total, and the default value was
1000.

See also: `com.polarion.ui.treeTable.hardLimit`

Scope: System

Added in version: 3.7.2 (2013 SR2)


### `com.polarion.ui.useOldSortingInEnumerationBubbles`

Default value: false

Used to define cases when alphabetical sort order is used for enumeration values in Visual Query Builder elements
(a.k.a."bubbles"). Value is Boolean (true or false).


- If true, legacy behavior is used, which may render some sorts in ways users find strange or confusing.
- If false, Polarion will try to use sorting by the sort order defined in enumeration configurations in more cases in enumeration
  bubbles.

Scope: System

Added in version: 3.9.3 (2015 SR3)


### `com.polarion.variants.featureModelStructureRole`

Default value: parent

Specifies the the link role to use for the Feature selection tree. Value is a string containing the ID of an existing Link Role (e.g. "parent"
for Link Role named "Parent").


Pertains to variant management using the Polarion VARIANTS add-on and the PureVariants server.

Scope: System

Added in version: 3.9.0 (2015)


### `com.polarion.variants.featureModelType`

Default value: featureModel
Defines the document type of the document containing the variants projects Feature Model. Value is a string containing the ID of an
existing document type. Example: "featureModel" as ID for a document type named "Feature Model".

Pertains to variant management using the Polarion VARIANTS add-on and the PureVariants server.

Scope: System

Added in version: 3.8.3 (2014 SR3)


### `com.polarion.variants.featureSelection.sortByOutlineNumber`

Default value: false

Controls how Features are sorted. Value is Boolean (true or false).

- If false, the features displayed in the Feature Selection view and Variants compare view are sorted by variation type.
- If true, the above are sorted in these views by outline number.

Pertains to variant management using the Polarion VARIANTS add-on and the PureVariants server.

Scope: System

Added in version: 3.9.1 (2015 SR1)


### `com.polarion.variants.featureType`

Default value: feature

Defines the Work Item type that represents Features. Value is a string containing the ID of an existing Work Item type. Example:
"feature" as ID for a type named "Feature".

Pertains to variant management using the Polarion VARIANTS add-on and the PureVariants server.

Scope: System

Added in version: 3.8.3 (2014 SR3)


### `com.polarion.variants.variantType`

Default value: variant

Specifies the Work Item type that represents Variants. Value is a string containing the ID of an existing Work Item type. Example
"variant" as ID for a type named "Variant".

Pertains to variant management using the Polarion VARIANTS add-on and the PureVariants server.

Scope: System

Added in version: 3.8.3 (2014 SR3)


### `com.polarion.variants.variationTypeField`

Default value: variationType

Specifies the enumeration that should be used for the variation type of a Variant. Value is a string containing the ID of an existing
enumeration. Example "variationType" as ID for an enumeration named "Variation Type".

Pertains to variant management using the Polarion VARIANTS add-on and the PureVariants server.

Scope: System

Added in version: 3.8.3 (2014 SR3)


### `com.polarion.velocity.allow.internal.api`

Default value: false

Disables or enables calls from Velocity of API methods which are internal. Value is Boolean (true or false).

NOTE: Property was introduced to disable such code especially in Pages (Live Report, etc.) in cases where it would be undesirable in
some customers' systems.

Scope: System

Added in version: 3.9.0 (2015)


### `com.polarion.velocity.autoUnindentScripts`

Default value: true

Value is Boolean (true or false). When true, all Velocity scripts are automatically unindented - all spaces at the beginning of lines before
the first '#' character are removed.

Scope: System

Added in version: 3.7.3 (2013 SR3)


### `com.polarion.wiki.allowedSecurityServiceMethods`

Default value: none

Some methods of ISecurityService are restricted from use in wiki (Classic Wiki) pages. This property makes it possible to remove
this restriction for some of them (some methods are allowed always). The value is a string that can contain a comma separated list of
method names.

Example: addGlobalRoleToUser,removeGlobalRoleFromUser
NOTE: The legacy wiki technology for non-LiveDoc pages, now referred to as Classic Wiki, is considered deprecated.

Scope: System

Added in version: 3.8.0 (2014)


### `com.polarion.wiki.forceWikiBaseUrl`

Default value: true

Value is Boolean (true or false). If true wiki uses `base.url` as server name instead of reading the value from requests.

NOTE: The legacy wiki technology for non-LiveDoc pages, now referred to as Classic Wiki, is considered deprecated.

Scope: System

Added in version: 3.5.0 (2011)


### `com.polarion.wiki.sharedVelocity`

Default value: false

Value is Boolean (true or false). If true, the wiki (Classic Wiki) uses one shared instance of Velocity. That is legacy behavior.

NOTE: Classic Wiki technology is currently deprecated. Migration to and use of newer widget-based Pages is recommended.

Scope: System

Added in version: 3.9.1 (2015 SR1)


### `com.polarion.wordRoundTrip.allowImportOfSuspectDocument`

Default value: false

Value is Boolean (true or false). If set to true it is possible, after confirmation, to import a round-trip Word document even if Polarion
detects that it was edited by an unsupported editor or Microsoft Word version.

Scope: System

Added in version: 3.5.2 (2011 SR2)


### `com.polarion.zookeeper.logsPurgePeriodMins`

Default value: 1440

Applies to clustered server setups. Set this property on the Coordinator. Specifies the time interval, in minutes, between purges of the
Zookeeper's transaction logs from the data folder. Setting value to zero (0) disables purging of these logs, which will then grow without
limitation other than disk space. The default configuration purges the folder every day. The purge process preserves the three most
recent snapshots unless otherwise specified in `com.polarion.zookeeper.retainedSnapshotsNum`.

For information on multi-server and clustered setups, see the Deployment and Maintenance Guide, available as a PDF download in
the Polarion product center on Support Center.

Scope: System

Added in version: 3.19.2 (19.2)


### `com.polarion.zookeeper.retainedSnapshotsNum`

Default value: 3

Applies to clustered server setups. Set this property on the Coordinator. When purging of Zookeeper's transaction logs is enabled in
property `com.polarion.zookeeper.logsPurgePeriodMins`, this property specifies the number of snapshots, and their
corresponding logs, that are retained in the data folder after a purge. The most recent corresponding files are retained, and all others
are deleted. Minimum value: 3.

For information on multi-server and clustered setups, see the Deployment and Maintenance Guide, available as a PDF download in
the Polarion product center on Support Center.

Scope: System

Added in version: 3.19.2 (19.2)


### `com.siemens.polarion.analytics.enabled`

Default value: false

This property enables Analytics and related logging of events and sending the data to the analytics server. Value is Boolean (true or
false).

- true = analytics feature is enabled
- false = analytics feature is disabled

Scope: System

Added in version: 3.21.1 (21 R1)


### `com.siemens.polarion.ci.externalBuild.timeout`

Default value: 1440

Specifies the maximum time, in minutes, that Polarion waits for builds launched from Polarion, but run with a configured external
building tool such as Jenkins. Such external builds are typically launched by a Test Run workflow function. Default value represents 24
hours.

Scope: System

Added in version: 3.19.3 (19.3)


### `com.siemens.polarion.cluster.excludedSessionAttributes`

Default value: empty

Background Information

Extra data could be stored in user sessions in some page scripts or external applications. These components could generally store
anything in the sessions. In a clustered server configuration, the sessions are serialized and replicated to other nodes in the cluster. To
be replicated, all the data stored in the sessions must be serializable. (They must implement the `java.io.Serializable` interface.)
An attempt to serialize a non-serializable session attribute will raise a `java.io.NotSerializableException` in the replication
process, visible in the log file, and the attribute will not be replicated.

Usage of this property

To avoid raising the exception, the problematic attributes can be added to this property. Then they will not be replicated. Missing
attributes may of course, cause incorrect behavior of the page script or external application. Therefore, a recommended solution is to
update these page scripts and external applications to make all the session attributes serializable. Then, the relevant class(es) should
be removed from this property.

The value is a string that can contain a comma-separated list of fully qualified Java class names, without spaces.

For information in multi-server and clustered setups, see the Deployment and Maintenance Guide, available as a PDF download in
the Polarion product center on Support Center.

Scope: System

Added in version: 3.18.2 (18.2)


### `com.siemens.polarion.cluster.membershipChannel.port`

Default value: 45564

This parameter defines the cluster membership communication port when using a multi-cluster configuration (for Active Load
Balancing) to manage cluster nodes in the underlying Tomcat server.

The default value is 45564.

You should set the parameters to operate other (non Polarion) Tomcat servers in a cluster configuration on the same network.

For information on multi-server and clustered setups, see the Deployment and Maintenance Guide, available as a PDF download in
the Polarion product center on Support Center.

Scope: System

Added in version: 3.18.2 (18.2)


### `com.siemens.polarion.cluster.nodeHostname`

Default value: null
This parameter can override the host name of the default network interface used for session replication in a clustered server
configuration on a particular node.

The Tomcat application server opens a socket listener on the default network interface. However, the default interface might not be the
one used for session replication. It depends on how the nodes are set up for the network interfaces.

It can hold either the correct network interface IP address or the appropriate host name, which is then translated into the valid network
interface IP address. If the property is empty or not set, Polarion tries to auto-detect the host name. If an error occurs during autodetection, the error is logged with the following message:
"Error while getting the node host name" (And the "null" value is used.)
The network interface name and IP address used are logged in the Polarion log file. Search for:
"TomcatAppServer cluster local bind host name:" string (class
`com.polarion.portal.tomcat.TomcatAppServer`, level INFO).

Define this parameter if the session replication doesn't work and/or the used network interface differs from the required one.

Scope: System

Added in version: 3.18.2 (18.2)


### `com.siemens.polarion.cluster.stickyCookieMaxAge`

Default value: 0 or 300

Defines the user session stickiness cookie timeout/expiration in a clustered server configuration. Used to enable user distribution and
balancing across the cluster nodes.

Value is in seconds and should initially be set to 300 (= 5 minutes, the default value). You may experiment a bit with the value to find the
most optimal value for your purposes. The reasonable range for the value is between 120 and 600 seconds.

For information on multi-server and clustered setups, see the Deployment and Maintenance Guide, available as a PDF download in
the Polarion product center on Support Center.


Scope: System

Added in version: 3.18.2 (18.2)


### `com.siemens.polarion.cluster.stickyCookieName`

Default value: ROUTEID

Sets the cookie's name that ensures Polarion user stickiness to particular nodes in a cluster environment. The value is a string.

Important!
- The value must the same as the cookie name configured in the Apache load balancer configuration. (The default ROUTEID value
  is compatible with the default Apache load balancer configuration templates.)
- If the name of the sticky cookie in the polarion-cluster.conf and polarion.properties files is different, then two cookies will be
  generated (one from the Polarion server and one from the Apache cluster configuration), and they will not work.

For complete information on configuring Polarion in a clustered server setup, see the Deployment and Maintenance Guide, available
as a PDF download in the Polarion product center on Support Center.

​

Scope: System

Added in version: 3.18.2 (18.2)


### `com.siemens.polarion.collaborationNotifications.enabled`

Default value: false

Enables or disables the Collaboration Notifications feature in LiveDoc documents. When enabled, users who are simultaneously
editing the same LiveDoc can see that other users are present, see who they are, and all are visually alerted to the possibility of
conflicting changes.

Scope: System

Added in version: 3.21.1 (21 R1)


### `com.siemens.polarion.collaborationNotifications.maxNumberOfUsersShown`

Default value: 10

Defines the maximum number of users shown in the Collaboration Notification drop-down menu in the Document Editor toolbar. Users'
names and avatars are shown. Value is an integer.

If the number of users currently interacting with a Document exceeds this limit, an additional menu item will show a count of how many
more users are interacting with the Document. Users can select Show All to invoke a dialog box that shows the names of all interacting
users.

Scope: System

Added in version: 3.21.1 (21 R1)


### `com.siemens.polarion.collaborationNotifications.port`

Default value: 40608

Defines the port number used for the Collaboration Notifications service. This service reports the users who are concurrently working on
a LiveDoc document. The information appears on the toolbar of the Document Editor.

If you change the port number in this property, you also need to change it in polarion.conf (Apache configuration). In cluster
deployment, the property must be set in the cluster Coordinator's polarion.properties file (when changing the default only).

Scope: System

Added in version: 3.21.1 (21 R1)


### `com.siemens.polarion.connectors.attachmentsLazyLoadingEnabled`

Default value: true

Enables or disables on-demand (a.k.a. "lazy") loading of Work Item attachments. Reading many Work Items with large attachments can
cause memory problems like OutOfMemoryException. If Work Items in your system tend to have large attachments, you may want to
enable this property.


Scope: System

Added in version: 3.21.1 (21 R1)


### `com.siemens.polarion.connectors.projectLock.timeout`

Default value: 9223372036854775807

Time in milliseconds that synchronizer jobs will wait for the project lock. During that timeout period, any sync job in the same project
that cannot acquire the lock will fail immediately. After the timeout period, the project lock will be released for the next synchronizer job
in the project to acquire it, and therefore start running again.

This property is intended to be used to prevent synchronizer jobs from stacking up and depleting heap memory completely, if the
synchronization is scheduled frequently.

Scope: System

Added in version: 3.20.2 (20 R2)


### `com.siemens.polarion.connectors.retryStrategy`

Default value: 2,10,2

Describes the Polarion-retry-strategy which defines the maximum number of times, and the waiting period, that HTTP requests to
external systems like TFS, JIRA and HP should be retried in case of any failure.

Value is comma-delimited list of the following integer values representing, in order:
- Retry Count,
- Delay (in seconds) and
- Multiplication Factor

The waiting period of each retry is calculated with formula:
(Multiplication Factor ^ Current Retry #Attempt) * Delay

Example: `com.siemens.polarion.connectors.retryStrategy=3,4,2`

1st attempt = (2^1)*4 = 2*4 = 8s  
2nd attempt = (2^2)*4 = 4*4 = 16s  
3rd attempt = (2^3)*4 = 8*4 = 32s  

Note: Retries are not supported for Doors, ReqIF, and Jenkins.

Scope: System

Added in version: 3.21.1 (21 R1)


### `com.siemens.polarion.dle.comparison.enableFragmentComparison`

Default value: true

This property enables the enhanced Document comparison algorithm, which preprocesses compared Documents and splits them into
smaller chunks, which are then compared separately. It usually gives faster and better results while using less memory.

Scope: System

Added in version: 3.19.0 (19)


### `com.siemens.polarion.document.listStyle`

Default value: 1

Sets representation style of numbered lists in the entire application. Value is a string; alpha and numeric characters can be entered.

Possible characters are:
- "1" for decimal numbers "1,2,3"
- "a" for lowercase letters "a,b,c"
- "A" for uppercase letters "A,B,C"
- "i" for lowercase Roman numbers "i,ii,iii"
- "I" for uppercase Roman numbers "I,II,III"

Examples:
default: "1"

Word Multilevel list default: "1ai" (it will effectively make itself "1ai1ai1ai" as Word supports maximum 9 levels)
​

Scope: System

Added in version: 3.10.3 (2016 SR3)


### `com.siemens.polarion.documentation.baseUrl`

Default value: https://docs.sw.siemens.com

This property defines the base URL of the Polarion Help server.

By default, it points to Polarion Help hosted on Siemens Support Center.

If Polarion users are on an isolated network that restricts internet access, you can install a local version of Siemens Documentation
Server.

You would then add the base URL of your Polarion Server to this property (just the HTTPS protocol, hostname, and port), so that
Polarion users could access Help within your closed network.

Example:
https://<Your_Doc_Server_Host_Name>:[port]

See the following to download, install, and add new documentation packages to Siemens Documentation Server.

https://support.sw.siemens.com/en-US/product/266603595/download/PL20220207266296647

Scope: System

Added in version: 3.22.2 (22 R2)


### `com.siemens.polarion.doorsconnector.connectionCheckTimeout`

Default value: 60

Defines the number of seconds that Polarion tries to connect to a DOORS server before giving up. Value is a positive integer.

NOTE: This property is faster and differs from `com.siemens.polarion.doorsconnector.timeout`. (Used while executing
commands when already connected to the DOORS server.)

Scope: System

Added in version: 3.18.3 (18.3)


### `com.siemens.polarion.doorsconnector.ole2FilenameBlacklist`

Default value: \u0002OlePres000,RichEditFlags

Value is a string that can contain a comma-separated list of filenames to be excluded from OLE2 hash calculation. Used to blacklist files
within the OLE2 file system (such as flags and caches) that tend to change even if the OLE content remains intact.

Scope: System

Added in version: 3.18.1 (18.1)


### `com.siemens.polarion.doorsconnector.timeout`

Default value: 300

Time that the DOORS connector will wait for a response to a command sent to the DOORS client. Value is a positive integer
representing seconds.

Scope: System

Added in version: 3.17.1 (17.1)


### `com.siemens.polarion.externalRepo.branchProcessingWait`

Default value: 3000

Defines the amount of time in milliseconds that a branch matching thread has to process all branches matched by regular expression
(regex). The default value may be increased by a small amount if necessary.

Scope: System

Added in version: 3.22.1 (22 R1)


### `com.siemens.polarion.externalRepo.branchReindexReprocessingWait`

Default value: 60
Defines the amount of time in seconds that Polarion waits for reprocessing of branches previously mismatched by branch filter during
reindexing.

CAUTION: The value should not be less than 45 (seconds), as that is the minimum time it takes Kafka Streams to process KTables.

Scope: System

Added in version: 3.22.1 (22 R1)


### `com.siemens.polarion.externalRepo.currentNodeIndexKafka`

Default value: true
Enables (by default) the processing of data from Kafka on the current Polarion node.

If disabled, the node reads the messages from Kafka to advance the topic index, but it does not do anything with them.

​

Scope: System

Added in version: 3.22.1 (22 R1)


### `com.siemens.polarion.externalRepo.externalRevisionsCacheCapacity`

Default value: 10000000
Defines a maximum size for the Guava cache used for polling the repositories from Kafka.

For really big repositories, where the total of all revisions is greater than the default value of this property, the value can be adjusted
upward.

If the total number of all revisions in repositories in Kafka polling is higher than the value set for this property, polling will fail with an error
"Revision not found in cache".

Scope: System

Added in version: 3.22.1 (22 R1)


### `com.siemens.polarion.externalRepo.sessionTimeoutWait`

Default value: 11
Defines the amount of time in seconds that Kafka Streams wait for session timeout. In general, the value should be the sum of the
following properties:
session.timeout.ms=8000 + heartbeat.interval.ms=3000 (values of these properties are milliseconds)
You can increase the value of this property if you find that the amount of time defined by the default value is too short for restarting
Kafka Streams.

Scope: System

Added in version: 3.22.1 (22 R1)


### `com.siemens.polarion.feedback.link`

Default value: none
As of Polarion 21 R1, the Send Feedback link is disabled in navigation by default, but administrators can enable it by adding
this property to the polarion.properties file with a target email or hyperlink.

Example:
com.siemens.polarion.feedback.link=polarion_support@your_company.com
Scope: System

Added in version: 3.21.1 (21 R1)


### `com.siemens.polarion.hpqcconnector.numberOfParentIdsPerGetRequest`

Default value: 500
Used to set the number of parentIds that are used in a single GET request. Necessary because HPQC may not accept GET requests
with a header larger than 8192 bytes. (Length depends on server configuration.) Value is a positive integer.

Scope: System

Added in version: 3.10.2 (2016 SR2)


### `com.siemens.polarion.impex.excel.template.columnsLimit`

Default value: 100
Limits the number of columns that an Excel export template may contain, in order to avoid memory issues.

Value is an integer. Polarion checks the limit set here only when a user initiates export using the template.

If template columns exceed the specified limit, the operation stops and the user receives an error message that explains the limitation.

Scope: System

Added in version: 3.20.2 (20 R2)


### `com.siemens.polarion.impex.excel.template.rowsLimit`

Default value: 300
Limits the number of rows that an Excel export template may contain, in order to avoid memory issues.

Value is an integer. Polarion checks the limit set here only when a user initiates export using the template.

If template rows exceed the specified limit, the operation stops and the user receives an error message that explains the limitation.

Scope: System

Added in version: 3.20.2 (20 R2)


### `com.siemens.polarion.javasvndriver.retryDelay`

Default value: 500
Delay time before a Subversion operation will be retried after a temporary problem.

Value is an integer representing milliseconds.

Zero (0) or negative value means no delay.

Delay is applied before each retry. Has no effect if retrying is not allowed due to setting
in `com.siemens.polarion.javasvndriver.retryLimit`.

Scope: System

Added in version: 3.10.2 (2016 SR2)


### `com.siemens.polarion.javasvndriver.retryLimit`

Default value: 5
Defines how many times a Subversion operation can be retried because of a temporary problem.

Currently applies only to read operations throwing Malformed network data exception, and connection timeout.

Value is an integer.

A negative value or zero (0) means no retry allowed.

See also: `com.siemens.polarion.javasvndriver.retryDelay`

Scope: System

Added in version: 3.10.2 (2016 SR2)


### `com.siemens.polarion.jiraconnector.connectionCheckMutualTls`

Default value: N/A
When attempting to connect to a Jira server instance with mutual or two-way authentication, you need a keystore with a client certificate.

The configuration property `com.siemens.polarion.jiraconnector.connectionCheckMutualTls` can be used to configure
the keystore with the client certificate. The configuration is optional:


### `com.siemens.polarion.jiraconnector.connectionCheckMutualTls =[server],[path],[alias],[user]`

server: The server URL.

path: The path to the keystore.

alias : The certificate alias in the keystore.

user: Key entry in the User Account Vault with the password to the keystore.

Example:
com.siemens.polarion.jiraconnector.connectionCheckMutualTls=https://my-first-jiraserver.de/,/opt/polarion/my-keystore.jks,first-jira-alias,first-jira-vault-user
Note: You can define settings for several servers. Each server setting is separated by a semicolon and the configurations of each server
setting are separated by a comma. See Polarion online Help topic Special considerations when connecting to Jira.

Scope: System

Added in version: 3.19.3 (19.3)


### `com.siemens.polarion.license.statistics.mbeanUpdateInterval`

Default value: 0
If set to a non-zero value, it enables statistics about Polarion license utilization in the Java Management Extensions MBean and
configures an interval (in milliseconds) for updating the statistics.

To use this functionality, you must enable the Java Management Extensions functionality in Java.

We recommend that you update the statistics every 5 minutes (i.e. 300 000 milliseconds).

Otherwise, statistic collection can result in a performance penalty on license check operations.

If you have a clustered server environment, perform this setup on the coordinator machine.

The default is set to 0 (Collecting license statistics information in MBean is disabled.)
​

Scope: System

Added in version: 3.22.1 (22 R1)


### `com.siemens.polarion.lucene.outlineNumbers.historicalIndexing.enabled`

Default value: false
Enables or disables building of the historical part of the WorkItem-OutlineNumbers index.

Enabling it can greatly increase the index size, leading to significant utilization of the Java heap space, and running out index disk
storage capacity. Consequently, disabling this historical index by setting this property to false is generally recommended. When
disabled, users can only query on, or sort by Work Item Outline Number in the HEAD revision, and not in historical revisions.

Scope: System

Added in version: 3.22.1 (22 R1)


### `com.siemens.polarion.nodeJsServer.autoStart`

Default value: true
Controls whether or not the NodeJs process starts automatically during Polarion startup. Value is Boolean (true or false). When set
to true, the process starts automatically.

NOTES:
The Node.js server script is used to convert SVG from a passed LaTeX formula
A service implemented in Polarion makes HTTP call to Node.js
For information about Node.js visit: https://nodejs.org/en/about/
Scope: System

Added in version: 3.19.0 (19)


### `com.siemens.polarion.nodeJsServer.host`


Default value: 127.0.0.1
Use this property to overwrite the default host on which the NodeJs server process will be started. The default host name for NodeJs
process is 127.0.0.1.

Scope: System

Added in version: 3.19.0 (19)


### `com.siemens.polarion.nodeJsServer.killOldProcess`

Default value: true
Controls whether to kill an old NodeJs process before starting a new one. For example, this may be needed when Polarion shuts down
abnormally, and the corresponding NodeJs process was not stopped. When set to true, then during the next Polarion start-up, the old
NodeJs process will be killed before Polarion tries to start the new NodeJs process.

Scope: System

Added in version: 3.19.0 (19)


### `com.siemens.polarion.nodeJsServer.port`

Default value: 34568
Use this property to overwrite the default port on which NodeJs server process will be started. The default port for NodeJs process is
34568.

Scope: System

Added in version: 3.19.0 (19)


### `com.siemens.polarion.objectindexing.runtimeWorkers`

Default value: min(num_of_cores/2+1, 8)
Displays the number of worker threads used during data indexing once the application starts.

Scope: System

Added in version: 3.23.4 (2304 - current)


### `com.siemens.polarion.oslc.enumFieldsDataComplexMode.enabled`

Default value: false
When using Polarion with the Teamcenter integration, this property can be used to change mode of including all single- and multi-value
enumeration attributes into the RDF (XML/JSON) representation of Work Items in OSLC API.

If false, simple mode is used.

If true, complex mode is used.

NOTE: Set to use simple mode if you experience Teamcenter going into an infinite loop when users open the relation browser.

Scope: System

Added in version: 3.17.0 (17)


### `com.siemens.polarion.oslc.loadOslcResources.threadsPoolSize`

Default value: 5
Use this property to optimize the processing time, based on system configuration, while loading OSLC resources to the OSLC cache.

Value is an integer representing number of threads.

A usage scenario would be in a Velocity script, in a Live Report Page, to preload OSLC resources to the cache, using multiple threads.

$transaction.oslcResources.prefetchOslcResources($workItems)
$workItems = list of Polarion work Items
Scope: System

Added in version: 3.22.1 (22 R1)


### `com.siemens.polarion.oslc.oslcLinkCacheInvalidationTime`

Default value: 180000
Timeout interval for OSLC links in cache. Value is an integer representing milliseconds. At the end of the configured interval, the cache
will be cleared and fresh data will be loaded during the next refresh.

Scope: System

Added in version: 3.21.1 (21 R1)


### `com.siemens.polarion.oslc.prefetchOslcResource.limit`

Default value: 10000
This property limits the number of OSLC remote resources loaded in the OSLC cache.

This property is used during the prefetching of OSLC resources from a Velocity Script.

Example:
$transaction.oslcResources.prefetchOslcResources($workItem)
Note:
The limit should never exceed the maximum OSLC cache size. (The default cache size is 20000 entries.)
You can configure the OSLC cache size in the ehcache.xml file.

Scope: System

Added in version: 3.22.1 (22 R1)


### `com.siemens.polarion.oslc.secureVault`

Default value: null
Controls where to store OSLC Friend Server Configurations. It must be the absolute path to a vault folder. If the folder does not exist
then it will be created. By default the property is not specified and the configuration file will be stored in the SVN repository to
folder .polarion/oslc
Scope: System

Added in version: 3.10.2 (2016 SR2)


### `com.siemens.polarion.persistence.objectMaps.inMemory`

Default value: false
Enables administrators to toggle between "In Memory Object Maps" and the older "HDD" based memory settings. Polarion will consume
additional memory proportionate to the size of the old object maps /polarion-data/object-maps.

The in-memory object maps are less robust than HDD-based, so in case of a hard crash, there is higher chance that the maps will be
corrupted. The map is automatically flushed to disk every 10 seconds if there are any changes.

Scope: System

Added in version: 3.17.0 (17)


### `com.siemens.polarion.platform.baseline.preloadInDays`

Default value: 180
Specifies the maximum age, in days, of Baselines that are preloaded (for rendering in Live Report widgets and other operations).

Setting this limit can significantly improve trend chart rendering. Value is an integer.

Preload goes from oldest revision to the newest one to fill up a cache with more recent results, even when preload in days value is more
days than the cache can contain. If the cache eliminates some items, it eliminates the oldest ones.

Scope: System

Added in version: 3.20.1 (20 R1)


### `com.siemens.polarion.platform.hardSearchSizeLimit`

Default value: 100000
Defines a "hard" limit of maximum Lucene and database query result size to prevent Out of Memory Errors. Value is an integer
representing total number or returned objects. If exceeded, the query is stopped, and a warning message appears to the user, or a user-

friendly exception is thrown to API/WS calls.

NOTE: After evaluation of internal and customer-supplied usage data, it is possible that the default value of this property might change
in a future release, or the possibility to configure this limit may be removed, and the limit value hard-coded. If so, it will be announced in
the Configuration.txt file bundled with the relevant release distributions, and documented in online Help.

Scope: System

Added in version: 3.19.3 (19.3)


### `com.siemens.polarion.platform.jsServerStartupCheckDelay`

Default value: 300000
Time between startup of the NodeJs/PhantomJS server, and the system's request to check if startup succeeded. Value is in
milliseconds.

Scope: System

Added in version: 3.19.1 (19.1)


### `com.siemens.polarion.platform.kafkaExternalRepo.enabled`

Default value: false
Enables the External Repository Aggregator solution for Change Traceability feature.

(Data is fetched from Kafka storage instead of straight from the repositories.)
If disabled (the default), the Direct Polling method is used for Change Traceability.

Scope: System

Added in version: 3.22.1 (22 R1)


### `com.siemens.polarion.platform.softSearchSizeLimit`

Default value: 20000
Defines a "soft" limit of maximum Lucene and database query result size to prevent Out of Memory Errors. This limit is imposed on
queries. If exceeded, a warning message is written to the log files. Query execution is not stopped.

CAUTION: If you set too low a value in this property, and many users subsequently run queries that exceed the limit, then the
logs can become heavily polluted.

NOTE: After evaluation of internal and customer-supplied usage data, it is possible that the default value of this property might change
in a future release, or the possibility to configure this limit may be removed, and the limit value hard-coded. If so, it will be announced in
the Configuration.txt file bundled with the relevant release distributions, and documented in online Help.

Scope: System

Added in version: 3.19.3 (19.3)


### `com.siemens.polarion.platform.sql.maxPoolSize`

Default value: Number of processors * 2
Sets the maximum pool size for PostgreSQL connections.

The following rules are used if the value is not defined:
1. If the number of processors * 2 is less than 10, the value used is 10.

2. If the number of processors * 2 is more than 20, the value 20 is used.

If the value is defined, the following rules apply:
1. If the defined value is less than 10, the value 10 is used.

WARNING: If the value is more than 20, the user MUST adjust the max_connections value in the PostgreSQL server configuration to a
number that is more than 4 times the value used.

Why you would set a maximum pool size:
Polarion uses 3 connection pools:
- Head DB connection
- Head DB ReadOnly connection
- History DB connection

The Resource Traceability database connection pool is also configured separately (the default is 10).

The formula for PostgreSQL max_connections must take this into account and can look like the following:
max_connections = 3 * <com.siemens.polarion.platform.sql.maxPoolSize> + <RT connection pool size> +
<extra-for-admin-needs>
For the defaults settings, the number of maximum connections is approximately 80.

Scope: System

Added in version: 3.20.1 (20 R1)


### `com.siemens.polarion.platform.threadKillingLogStackTrace`

Default value: false
Define the thread killing log's level of detail. Value is Boolean (true or false).

false: The log file only mentions that a thread was killed/interrupted.

true: The log file will also contain the stack traces of threads that were killed/interrupted.

Scope: System

Added in version: 3.19.2 (19.2)


### `com.siemens.polarion.platform.threadKillingMode`

Default value: killAll
Defines the kill mode for an execution thread monitoring request. Value is a string.

Possible values:
killAll: All long-running read-only UI requests will be killed (default value).

reportOnly: Only requests related to Pages or Classic Wiki pages (read-only) will be killed.

disabled: Long-running transactions are logged, but not interrupted.

Scope: System

Added in version: 3.18.2 (18.2)


### `com.siemens.polarion.platform.threadKillingTimeout`

Default value: 590000
The time after which a request can be potentially interrupted by ExecutionThreadMonitoring. Value is an integer representing
milliseconds.

NOTE: If the value equals or is less then zero, the default value will be used.

TIP: Set this property with a time period less than then Apache timeout configured in the polarion.conf or polarion-cluster.conf files.

Scope: System

Added in version: 3.18.2 (18.2)


### `com.siemens.polarion.previewgenerator.displayNoExtensionImages`

Default value: false
Controls whether Polarion should attempt to display existing images that have no file extension in rich text fields, LiveDocs, and
Pages. Value is Boolean (true or false).

Scope: System

Added in version: 3.18.1 (18.1)


### `com.siemens.polarion.previewgenerator.external.app`

Default value: null
Defines the external application which will be executed for conversion of extensions defined in property
`com.siemens.polarion.previewgenerator.external.extensions`. Value is a string.


Example:
com.siemens.polarion.previewgenerator.external.app=C:/Program Files/Siemens/Teamcenter11.2/Visualization/VVCP/prepare.exe
Scope: System

Added in version: 3.17.1 (17.1)


### `com.siemens.polarion.previewgenerator.external.extensions`

Default value: null
Comma separated list of extensions which are supported by the external preview generator application defined property
`com.siemens.polarion.previewgenerator.external.app` . Value is a string.

Example:
com.siemens.polarion.previewgenerator.external.extensions=docx,doc,xlsx,xls,pdf,vsd,vsdx
Scope: System

Added in version: 3.17.1 (17.1)


### `com.siemens.polarion.previewgenerator.external.param`

Default value: null
Used to define one or more enumerated parameters for the external preview generator application specified in
property `com.siemens.polarion.previewgenerator.external.app`. Parsed parameters are passed as arguments to that
application.

Usage:
com.siemens.polarion.previewgenerator.external.param#=value
...where # is a number starting from 1 (see example below). Value is a string.

Example:
```
com.siemens.polarion.previewgenerator.external.param1=-png
com.siemens.polarion.previewgenerator.external.param2=-overwrite
```
Scope: System

Added in version: 3.17.1 (17.1)


### `com.siemens.polarion.previewgenerator.wmfemf.enabled`

Default value: true
Enables or disables an internal pseudo preview generator for wmf and emf files. Value is Boolean (true or false). If the preview
generator application defined in property `com.siemens.polarion.previewgenerator.external.app` is capable of handling
those file types, you can set this property to false to disable the pseudo preview generator.

Scope: System

Added in version: 3.17.1 (17.1)


### `com.siemens.polarion.purevariants.propagationDeterminedByRestriction`

Default value: false
Value is Boolean (true or false). If set to true, then all Work Items with a restriction that are also connected via propagation links, will
use the restriction as the propagation condition.

However, this behavior also has one consequence: If a child Work Item in the Document structure is included in variant selection via
propagation, then its parent Work Item from the Document structure will be included as well, even if its restriction does not allow it. This
would normally trigger a validation error, but with this property set, it will be allowed and not reported to the user. Therefore, only enable
this property during early adoption of the propagation and plan to disable it as soon as your data are in a consistent state.

Pertains to variant management using the Polarion VARIANTS add-on and the PureVariants server.

Scope: System

Added in version: 3.17.3 (17.3)


### `com.siemens.polarion.repository.git.timeout`

Default value: 30000
Timeout for poll action on external repository(ies). Value is an integer representing milliseconds.

NOTE: Polarion polls external repositories in a clustered server environment. The timeout set in this property ensures that if something
happens on the external repo side (e.g. while pulling changes from Git repository) and the socket is closed and the connection
disconnected, Polarion does not keep attempting to poll it. When polling of a repository times out, an error is written to the log files and
committed revisions are collected after next successful polling.

Scope: System

Added in version: 3.18.1 (18.1)


### `com.siemens.polarion.rest.bodySizeLimit`

Default value: 2097152
This property limits the size of the request body in an HTTP request.

The limit is only valid for HTTP POST, HTTP PATCH, and HTTP DELETE requests with application/json content type.

The value is given as bytes.

Note: This limit also applies to the size of the JSON file that is used when POSTing or PATCHing attachments. Also, using a high value
for this property might make the Polarion server vulnerable from a security point of view.

Scope: System

Added in version: 3.22.2 (22 R2)


### `com.siemens.polarion.rest.cors.allowedOrigins`

Default value: empty list -- CORS disabled
This property enables CORS (Cross-Origin Resource Sharing) access to all REST endpoints.

Supported values:
Empty list --> CORS is disabled.

* --> CORS requests from any host are allowed.

Comma separated list of URI (schema://host:port) --> Only CORS requests from these origins are allowed. (Standard ports - 80 for
HTTP, 443 for HTTPS - should be omitted.

For example, https://secured.host.name instead of https://secured.host.name:443)
Notes:
- Requests from the same origin that Polarion is running on are always allowed, regardless of the value in this property.

- Requests from origin set in `com.siemens.polarion.rest.baseUrl` are always allowed, regardless of the value of this property.

(If not defined, baseUrl is used as the default value.)
- For a Cluster deployment, we recommend that you set the property in the shared polarion.properties file on the cluster machine to
ensure that all the nodes use the same setting.

Scope: System

Added in version: 3.22.2 (22 R2)


### `com.siemens.polarion.rest.defaultPageSize`

Default value: 100
This configuration property defines the default value of returned items for REST API endpoints when there is no parameter for page
size.

The default value is 100.

If you set this configuration property to a number greater than the maxPageSize, the defaultPageSize value is replaced by
the maxPageSize value.

Scope: System

Added in version: 3.23.4 (2304 - current)


### `com.siemens.polarion.rest.enabled`

Default value: false
This property determines access to all REST endpoints.

If it is disabled, all requests result in a 503 (Service Unavailable) status code.

Note:
For a Cluster deployment, we recommend that you set the property in the shared polarion.properties file on the cluster machine to
ensure that all the nodes use the same setting.

Scope: System

Added in version: 3.22.2 (22 R2)


### `com.siemens.polarion.rest.maxIncludedSize`

Default value: 500
This property specifies the number of entities in the included section that are returned in the results for REST API endpoints.

If the number of entities exceeds the maxIncludedSize, they will not be added to the included section if requested.

The default value of this property is 500 items, with a maximum limit of 10 000.

If the provided value exceeds the 10 000 limit, it is capped.

If the relationship section resources are capped by the maxRelationshipSize property, they will not appear in the include
section.

Scope: System

Added in version: 3.23.4 (2304 - current)


### `com.siemens.polarion.rest.maxPageSize`

Default value: 100
This property sets the limit for the maximum page size that can be request by a REST API client.

The default value is 100.

The absolute maximum page size is 10000.

(Setting this property to a number larger than 10000 has no effect.)
Note:
For a Cluster deployment, we recommend that you set the property in the shared polarion.properties file on the cluster (aka shared
services) machine to ensure that all the nodes use the same setting.

Scope: System

Added in version: 3.22.2 (22 R2)


### `com.siemens.polarion.rest.maxRelationshipSize`

Default value: 500
Specifies the maximum number of entities that can be returned for each of the resource(s) relationship field(s).

If any related resource is excluded by this limit, then it will not be included in the "included" section if it is requested.

The default value of this property is 500 items, with a maximum limit of 10.000. If the provided value exceeds the 10.000 limit, it is
capped.

​

Scope: System

Added in version: 3.23.4 (2304 - current)


### `com.siemens.polarion.rest.security.restApiToken.enabled`

Default value: false
This property enables REST API calls via javascript within Polarion Pages with an active Polarion session.

Type: Boolean

Example: com.siemens.polarion.rest.security.restApiToken.enabled=true
It is a system file property and must be added to the polarion.properties file.

Search for "REST API access from the Polarion portal without PAT" in Polarion Help for more information.

Scope: System

Added in version: 3.23.4 (2304 - current)


### `com.siemens.polarion.rest.swaggerUi.enabled`

Default value: false
This property determines the availability of the Swagger UI.

If disabled, accessing {serverUrl}/polarion/rest/v1 results in a "503 - Service Unavailable" status code.

You must also set `com.siemens.polarion.rest.enabled` to true to enable the Swagger UI.

Note:
For a Cluster deployment, we recommend that you set the property in the shared polarion.properties file on the cluster machine to
ensure that all the nodes use the same setting.

Scope: System

Added in version: 3.22.2 (22 R2)


### `com.siemens.polarion.rest.swaggerUi.persistAuthorization`

Default value: false
If this property is set to true, the Swagger UI remembers a personal access token when the Swagger UI page is reloaded or opened in
the same browser.

This property affects all users of the Swagger UI of this Polarion instance. (It is a global parameter, users cannot individually
choose to have their personal access tokens remembered or not.)
Users can still use the Swagger UI action Authorize > Logout to explicitly ask the browser to forget their personal access token.

The remembered access token is persisted in the browser's local storage. It will be forgotten when the browser's local storage
data are cleaned or invalidated based on the browser settings.

Caution: Any user accessing the same terminal and browser can easily copy the access token using the Swagger UI and use it
elsewhere, impersonating the token owner. If this is a concern, the users should be instructed to explicitly log out of the Swagger UI, or
the property should not be turned on. If the property is kept turned off, closing the browser tab will suffice to have the personal access
token forgotten by the Swagger UI.

Scope: System

Added in version: 3.23.4 (2304 - current)


### `com.siemens.polarion.rt.configurationUpdateDelay`

Default value: 1800000
Defines time interval used by the Resource Traceability (RT) server to check for configuration changes in Polarion. Value is an integer
representing milliseconds.

See also:
- `com.siemens.polarion.rt.writerNodeUrl`
- `com.siemens.polarion.rt.tokenLifeTime`
- `com.siemens.polarion.rt.startRtServer`
- `com.siemens.polarion.rt.sharedSecret`
- `com.siemens.polarion.rt.polarionUrl`
- `com.siemens.polarion.rt.db.jdbcUrl`
- `com.siemens.polarion.rt.db.password`
- `com.siemens.polarion.rt.db.username`

### `com.siemens.polarion.rt.dataCollectingEnabled`

Scope: System

Added in version: 3.17.0 (17)


### `com.siemens.polarion.rt.dataCollectingEnabled`

Default value: true
Defines whether the current Resource Traceability (RT) server should start as a writer or reader-node. Value is Boolean (true or false).

If true then current node will be able to update RT-configurations in the database, and collect and parse links (which also will be stored
in the database). Also, it will have all possibilities of reader-node.

If false then current node will only be able to give away parsed RT-links by request. Other requests (e.g. to update something) will be
ignored.

See also:
- `com.siemens.polarion.rt.db.jdbcUrl`
- `com.siemens.polarion.rt.polarionUrl`
- `com.siemens.polarion.rt.db.password`
- `com.siemens.polarion.rt.db.username`

Scope: System

Added in version: 3.17.0 (17)


### `com.siemens.polarion.rt.db.jdbcUrl`

Default value: n/a
JDBC URL of the database that will be used to persist Resource Traceability (RT )server related information. Value is a string.

See also:
- `com.siemens.polarion.rt.writerNodeUrl`
- `com.siemens.polarion.rt.tokenLifeTime`
- `com.siemens.polarion.rt.startRtServer`
- `com.siemens.polarion.rt.sharedSecret`
- `com.siemens.polarion.rt.polarionUrl`
- `com.siemens.polarion.rt.db.password`
- `com.siemens.polarion.rt.db.username`
- `com.siemens.polarion.rt.dataCollectingEnabled`
- `com.siemens.polarion.rt.configurationUpdateDelay`

Scope: System

Added in version: 3.17.0 (17)


### `com.siemens.polarion.rt.db.password`

Default value: n/a
Password credential to access database that is used to persist Resource Traceability (RT) server related information. Value is a string.

See also:
- `com.siemens.polarion.rt.writerNodeUrl`
- `com.siemens.polarion.rt.tokenLifeTime`
- `com.siemens.polarion.rt.startRtServer`
- `com.siemens.polarion.rt.sharedSecret`
- `com.siemens.polarion.rt.polarionUrl`
- `com.siemens.polarion.rt.db.jdbcUrl`
- `com.siemens.polarion.rt.db.username`
- `com.siemens.polarion.rt.dataCollectingEnabled`
- `com.siemens.polarion.rt.configurationUpdateDelay`

Scope: System

Added in version: 3.17.0 (17)


### `com.siemens.polarion.rt.db.username`

Default value: n/a

User name credential to access the database used to persist Resource Traceability (RT) server related information. Value is a string.

See also:
- `com.siemens.polarion.rt.writerNodeUrl`
- `com.siemens.polarion.rt.tokenLifeTime`
- `com.siemens.polarion.rt.startRtServer`
- `com.siemens.polarion.rt.sharedSecret`
- `com.siemens.polarion.rt.polarionUrl`
- `com.siemens.polarion.rt.db.jdbcUrl`
- `com.siemens.polarion.rt.db.password`
- `com.siemens.polarion.rt.dataCollectingEnabled`
- `com.siemens.polarion.rt.configurationUpdateDelay`

Scope: System

Added in version: 3.17.0 (17)


### `com.siemens.polarion.rt.polarionUrl`

Default value: n/a
Stores the base URL of the Polarion server with which the Resource Traceability (RT) server (URL specified in property
`com.siemens.polarion.rt.db.jdbcUrl`) is to communicate for resource trace operations. Value is a string.

NOTE: The Polarion server adds in the authorization token its baseUrl as issuer, and the RT server, using this property, checks that the
issuer is really the expected one. If RT runs in embedded mode (and this property is not set), then the base.url is also used on the RT
side.

See also:
- `com.siemens.polarion.rt.writerNodeUrl`
- `com.siemens.polarion.rt.tokenLifeTime`
- `com.siemens.polarion.rt.startRtServer`
- `com.siemens.polarion.rt.sharedSecret`
- `com.siemens.polarion.rt.db.jdbcUrl`
- `com.siemens.polarion.rt.db.password`
- `com.siemens.polarion.rt.db.username`
- `com.siemens.polarion.rt.dataCollectingEnabled`
- `com.siemens.polarion.rt.configurationUpdateDelay`

Scope: System

Added in version: 3.17.0 (17)


### `com.siemens.polarion.rt.sharedSecret`

Default value: n/a
Sets the shared secret key for tokens between the Resource Traceability (RT) and Polarion servers. This shared key is used to sign
json tokens sent from Polarion to RT server. Value is a string.

See also:
- `com.siemens.polarion.rt.writerNodeUrl`
- `com.siemens.polarion.rt.tokenLifeTime`
- `com.siemens.polarion.rt.startRtServer`
- `com.siemens.polarion.rt.polarionUrl`
- `com.siemens.polarion.rt.db.jdbcUrl`
- `com.siemens.polarion.rt.db.password`
- `com.siemens.polarion.rt.db.username`
- `com.siemens.polarion.rt.dataCollectingEnabled`
- `com.siemens.polarion.rt.configurationUpdateDelay`

Scope: System

Added in version: 3.17.0 (17)


### `com.siemens.polarion.rt.startRtServer`

Default value: true

Defines whether to start the Resource Traceability (RT) web application automatically when Polarion server starts. Value is Boolean
(true or false).

If true the RT web application will be deployed to Polarion Tomcat and started with Polarion.

If false RT web application won't be deployed to Polarion Tomcat.

See also:
- `com.siemens.polarion.rt.writerNodeUrl`
- `com.siemens.polarion.rt.tokenLifeTime`
- `com.siemens.polarion.rt.sharedSecret`
- `com.siemens.polarion.rt.polarionUrl`
- `com.siemens.polarion.rt.db.jdbcUrl`
- `com.siemens.polarion.rt.db.password`
- `com.siemens.polarion.rt.db.username`
- `com.siemens.polarion.rt.dataCollectingEnabled`
- `com.siemens.polarion.rt.configurationUpdateDelay`

Scope: System

Added in version: 3.17.0 (17)


### `com.siemens.polarion.rt.tokenLifeTime`

Default value: 60000
Specifies the length of time that json tokens sent by Polarion to the Resource Traceability (RT) server remain valid. Value is an integer
representing milliseconds.

See also:
- `com.siemens.polarion.rt.writerNodeUrl`
- `com.siemens.polarion.rt.startRtServer`
- `com.siemens.polarion.rt.sharedSecret`
- `com.siemens.polarion.rt.polarionUrl`
- `com.siemens.polarion.rt.db.jdbcUrl`
- `com.siemens.polarion.rt.db.password`
- `com.siemens.polarion.rt.db.username`
- `com.siemens.polarion.rt.dataCollectingEnabled`
- `com.siemens.polarion.rt.configurationUpdateDelay`

Scope: System

Added in version: 3.17.0 (17)


### `com.siemens.polarion.rt.writerNodeUrl`

Default value: null
URL of the writer node that enables Polarion to determine which server to notify about configuration changes. Value is a string. If set,
then Polarion will notify this node for collecting purposes (when configuration changes, for example). If not set ,then the URL specified in
property `com.siemens.polarion.rt.url` is used. If the that property is also not set, then the value of the baseUrl property is
used.

See also:
- `com.siemens.polarion.rt.tokenLifeTime`
- `com.siemens.polarion.rt.startRtServer`
- `com.siemens.polarion.rt.sharedSecret`
- `com.siemens.polarion.rt.polarionUrl`
- `com.siemens.polarion.rt.db.jdbcUrl`
- `com.siemens.polarion.rt.db.password`
- `com.siemens.polarion.rt.db.username`
- `com.siemens.polarion.rt.dataCollectingEnabled`
- `com.siemens.polarion.rt.configurationUpdateDelay`

Scope: System

Added in version: 3.17.0 (17)


### `com.siemens.polarion.scriptInjection.loginBody`


Default value: null
This property allows you to inject custom HTML or JavaScript snippets into the <body> tag of Polarion's login page.

This functionality can be used to customize Polarion UI, add analytics on top of Polarion, or integrate an onboarding solution into
Polarion.

Type: String
Default value: null
Example: `<script type="text/javascript">window.alert("example")</script>`
A system file property. Must be added to the polarion.properties file.

Scope: System

Added in version: 3.22.2 (22 R2)


### `com.siemens.polarion.scriptInjection.loginHead`

Default value: null
This property allows you to inject custom HTML or JavaScript snippets into the <head> tag of Polarion's login page.

This functionality can be used to customize Polarion UI, add analytics on top of Polarion, or integrate an onboarding solution into
Polarion.

Type: String
Default value: null
Example: `<script type="text/javascript">window.alert("example")</script>`
A system file property. Must be added to the polarion.properties file.

Scope: System

Added in version: 3.22.2 (22 R2)


### `com.siemens.polarion.scriptInjection.mainBody`

Default value: null
This property allows you to inject custom HTML or JavaScript snippets into the <body> tag of Polarion's main page.

This functionality can be used to customize Polarion UI, add analytics on top of Polarion, or integrate an onboarding solution into
Polarion.

Type: String
Default value: null
Example: `<script type="text/javascript">window.alert("example")</script>`
A system file property. Must be added to the polarion.properties file.

Scope: System

Added in version: 3.22.2 (22 R2)


### `com.siemens.polarion.scriptInjection.mainHead`

Default value: null
This property allows you to inject custom HTML or JavaScript snippets into the <head> tag of Polarion's main page.

This functionality can be used to customize Polarion UI, add analytics on top of Polarion, or integrate an onboarding solution into
Polarion. Type: String
Default value: null
Example: `<script type="text/javascript">window.alert("example")</script>`
A system file property. Must be added to the polarion.properties file.

Scope: System

Added in version: 3.22.2 (22 R2)


### `com.siemens.polarion.security.appId`

Default value: Polarion
ID of the security application for single sign-on (SSO) configuration. Value is a string.

For Kerberos and Tcss usage, use JAAS configuration file with the following syntax (this file is mandatory for Kerberos login)
See links below for detailed syntax and usage specification:
http://docs.oracle.com/javase/7/docs/technotes/guides/security/jaas/JAASRefGuide.html

http://docs.oracle.com/javase/7/docs/technotes/guides/security/jgss/tutorials/LoginConfigFile.html
<entry name> {
<LoginModule> <flag> <LoginModule options>; <LoginModule> <flag> <LoginModule options>; . . . }
<entry name>
is ID of application that is used for Polarion, the default value is Polarion
NOTE: If your system is configured to use authentication.xml (introduced in version 21 R1) to authenticate users, you do not need
to set this property in polarion.properties.

For complete information on SSO configuration, see the Authentication guide section of Polarion Help. The content is available on
Support Center in HTML and PDF formats.

Scope: System

Added in version: 3.17.0 (17)


### `com.siemens.polarion.security.auth.cluster.folder`

Default value: $coordinator_workspace/cluster-data/
For a cluster setup, this property specifies the root folder for the authentication.xml file's hierarchy on the Coordinator.

The hierarchy under the folder will be following: $clusterId/authentication/authentication.xml
The default value is $coordinator_workspace/cluster-data
For Linux it is /opt/polarion/data/workspace/cluster-data
NOTE: Don't forget to reindex entire cluster.

Scope: System

Added in version: 3.21.1 (21 R1)


### `com.siemens.polarion.security.auth.fallback`

Default value: false
Enables or disables login fallback. Login fallback is hard coded to the FORM authentication. Value is Boolean (true or false). Login
fallback is enabled on following endpoint: /polarion/login/fallback.

Scope: System

Added in version: 3.17.1 (17.1)


### `com.siemens.polarion.security.auth.method`

Default value: form
Sets the authentication method used in the embedded Tomcat server. Value is a string. Valid values are: form, spnego, tcss, saml, and
oauth2.

Administrators should change the value of this property only when ready to switch their Polarion system to use a different authentication
mechanism. That mechanism should already be configured in accordance with the applicable documentation in the Single Sign On
(SSO) with Polarion document, available on Support Center. Detailed usage information for this property is provided in the
"Authentication method property for Tomcat" topic in that document.

NOTE: If your system is configured to use authentication.xml (introduced in version 21 R1) to authenticate users, you do not need
to set this property in polarion.properties.

For complete information on SSO configuration, see the Authentication guide section of Polarion Help. The content is available on
Support Center in HTML and PDF formats.

​

Scope: System

Added in version: 3.10.3 (2016 SR3)


### `com.siemens.polarion.security.auth.replaceForbiddenCharacters.enabled`

Default value: false
This property is one of several that need to be set when configuring user authentication. If this property is set to true, then Polarion
replaces forbidden characters in a user name when a user name from an identity provider (IdP) response contains them. If the property
is not set (false), then user names with forbidden characters in IdP responses are rejected during Auto-create. This is the default
behavior.

Security note:
Allowing automatic replacement of forbidden characters can lead to a security vulnerability where two IdP user names are mapped to
the same user name on the Polarion side. Administrators need to ensure that replacement is safe from a security standpoint for all
possible users, and automatic replacement is not ambiguous when mapping them.

For example:
user_id maps to user_id
user|id maps to user_id
Note: The forbidden chars are:
"!\"#$%&'()*+,/: ;<=>?[\\]^`{|}~\t\n\r"
The ampersand (@) and dash (-) characters at the beginning of a user name are also replaced by underscore ( _ ). For example:
@user1 maps to _user1
NOTE: If your system is configured to use authentication.xml (introduced in version 21 R1) to authenticate users, you do not need
to set this property in polarion.properties.

For complete information on SSO configuration, see the Authentication guide section of Polarion Help. The content is available on
Support Center in HTML and PDF formats.

Scope: System

Added in version: 3.20.2 (20 R2)


### `com.siemens.polarion.security.certificate`

Default value: absent
Specifies the certificate file location within the file system. Used for signing the authentication request sent to the identity provider. The
identity provider should also have this certificate to be able to verify this signature.

Scope: System

Added in version: 3.19.1 (19.1)


### `com.siemens.polarion.security.corsRequestRetry.enabled`

Default value: true
Controls how a client handles erroneous HTTP requests with a "0" status code. (Most likely a CORS issue.)
If disabled, the client will not attempt to retry the request with reauthentication.

Note: An HTTP "0" Status Code is not a valid HTTP status, so it might indicate other issues like firewall blocks. (So these requests
are only retried once.)
Scope: System

Added in version: 3.21.2 (21 R2)


### `com.siemens.polarion.security.disableIFrameLogin`

Default value: false (but see description)
Controls whether login inside an iFrame is allowed in the internal login dialog. Value is Boolean (true or false).

If disallowed for security reasons, then Polarion will display a link that end users can log in with via a new browser tab.

The default value depends on the authentication method used in Polarion. (Specified in the
`com.siemens.polarion.security.auth.method` property.)
If the authentication method is SAML or OAUTH2 , then the default value of this property is true - otherwise, it's false.

Scope: System

Added in version: 3.17.2 (17.2)


### `com.siemens.polarion.security.executeCommandJob.enabled`

Default value: true
Value is Boolean (true or false). "execute.command" jobs can potentially execute harmful jobs. You can opt to disable the execution of
"execute.command" jobs by setting this property to false:
com.siemens.polarion.security.executeCommandJob.enabled=false
NOTE: Add the above line to the polarion.properties system configuration file if the property is not already present.

Scope: System

Added in version: 3.10.3 (2016 SR3)


### `com.siemens.polarion.security.executingBuilds.enabled`

Default value: true
Enables or disables execution of build scripts. Value is Boolean (true or false). When set to false builds will fail and an error message
will be written to the logs.

NOTES:
Build scripts have the potential to pose a security threat because they have read/write access to the host file system.

This setting does not affect calculations. To disable calculations,
see `com.siemens.polarion.security.executingCalculations.enabled`.

Scope: System

Added in version: 3.10.3 (2016 SR3)


### `com.siemens.polarion.security.executingCalculations.enabled`

Default value: true
Value is Boolean (true or false). Provides the option to disable the execution of calculation jobs if you have security concerns.

See also: `com.siemens.polarion.security.executingBuilds.enabled`

Scope: System

Added in version: 3.10.3 (2016 SR3)


### `com.siemens.polarion.security.forbiddenFieldsInQuery`

Default value: empty set
The list of field suffixes that cannot be used in SQL queries and fields excluded from Lucene full-text searches.

All SQL queries containing a field that equals to or ends with one of the listed suffixes will be blocked.

The values of forbidden fields will be normally indexed but not searchable in full-text queries.

Important note:
When using this property to prevent full-text Lucene searches of the contents of certain previously indexed fields, it is necessary to
perform a full reindex.

When creating a brand new field that should not be searchable in full-text, it's enough to add the field to the property followed by a
Polarion restart (without reindex) before the field is first filled with a value on some object. (For example, a Work Item).

The reports and pages can use the forbidden fields for rendering purposes, trusting the fact that proper persons can edit and view
reports.

DEFAULT value: empty list
Examples:
com.siemens.polarion.security.forbiddenFieldsInQuery=forbiddenField1, forbiddenField2
1. Lucene queries like:

'value'
will NOT return fulltext results from
fields forbiddenField1, forbiddenField1.KEY, forbiddenField1.1, forbiddenField.name, forbiddenField2, forbiddenField2.KEY
etc.

WILL return results containing the term 'value' in other fields (for example, in the "description" field).

'forbiddenField1:value'
WILL return results that contain the given value in the field itself (unless the User does not have permission to read the
field forbiddenField1 and they have a restricted role listed
in `com.siemens.polarion.security.permission.globalRolesWithQueryFieldRestriction`)
description: 'forbiddenSuffix1'
forbiddenSuffix1Author: 'author'
'HAS_VALUE: forbiddenField1'
WILL return results that contain the given value in the field itself (unless the User does not have permission to read the
field forbiddenField1 and they have a restricted role listed 
in `com.siemens.polarion.security.permission.globalRolesWithQueryFieldRestriction`)

2. SQL query:
Blocked
select c_pk from Workitem where myFieldWithforbiddenField1='value'
select c_pk from Workitem where forbiddenField1='value'
select fk_uri_workitem from cf_workitem where c_name='myFieldWithforbiddenField2'
select fk_uri_workitem from cf_workitem where c_name='forbiddenField2'
select fk_uri_workitem from cf_workitem where description='myFieldWithforbiddenField2'
Not Blocked
select c_pk from Workitem where description='I would like to avoid having myFieldWithforbiddenField1'
select c_pk from Workitem where forbiddenField2Title='title2'
select fk_uri_workitem from cf_workitem where c_name='forbiddenField2Id'
select fk_uri_workitem from cf_workitem where description='myFieldWithforbiddenField2Id'

Scope: System

Added in version: 3.23.4 (2304 - current)


### `com.siemens.polarion.security.oauth2.authorizeUrl`

Default value: null
This property is one of several that need to be set when configuring user authentication using the oAuth
(https://www.oauth.com) protocol. It stores the authorization URL. Value is a string.

Also see the `com.siemens.polarion.security.oauth2*` property.

NOTE: If your system is configured to use authentication.xml (introduced in version 21 R1) to authenticate users, you do not need

to set this property in polarion.properties.

For complete information on SSO configuration, see the Authentication guide section of Polarion Help. The content is available on
Support Center in HTML and PDF formats.

Scope: System

Added in version: 3.20.2 (20 R2)


### `com.siemens.polarion.security.oauth2.clientId`

Default value: null
This property is one of several that need to be set when configuring user authentication using the oAuth
(https://www.oauth.com)protocol. It stores the value of the client_id parameter of the Authorization code request, which the
identity provider should supply. Value is string type. See also the `com.siemens.polarion.security.oauth2.clientSecret`,
and `com.siemens.polarion.security.oauth2.*` properties.

NOTE: If your system is configured to use authentication.xml (introduced in version 21 R1) to authenticate users, you do not need
to set this property in polarion.properties.

For complete information on SSO configuration, see the Authentication guide section of Polarion Help. The content is available on
Support Center in HTML and PDF formats.

Scope: System

Added in version: 3.20.2 (20 R2)


### `com.siemens.polarion.security.oauth2.clientSecret`

Default value: null
This property is one of several that need to be set when configuring user authentication using the oAuth
(https://www.oauth.com) protocol. It stores the value of the client_secret parameter of the Authorization code request, which
the identity provider should supply if the provider requires that the server must authenticate the client. Consult the provider's developer
documentation. Value is string type.

See also `com.siemens.polarion.security.oauth2.clientId`, and `com.siemens.polarion.security.oauth2*` properties.

NOTE: If your system is configured to use authentication.xml (introduced in version 21 R1) to authenticate users, you do not need
to set this property in polarion.properties.

For complete information on SSO configuration, see the Authentication guide section of Polarion Help. The content is available on
Support Center in HTML and PDF formats.

Scope: System

Added in version: 3.20.2 (20 R2)


### `com.siemens.polarion.security.oauth2.paramUrl.(id|email|name|description)`

Default value: null
This property is one of several that need to be set when configuring user authentication using
the oAuth (https://www.oauth.com) protocol. Value is a string. One of the following values, which correspond to the fields of
the UserProfile class, should be used as the property ending: id, email, name, or description. Some identity providers do not provide
some data in user profiles, so it is necessary to request it from a separate endpoint. The profile field value specified in this property will
be fetched from the given endpoint URL.

See also properties `com.siemens.polarion.security.oauth2*`

NOTE: If your system is configured to use authentication.xml (introduced in version 21 R1) to authenticate users, you do not need
to set this property in polarion.properties.

For complete information on SSO configuration, see the Authentication guide section of Polarion Help. The content is available on
Support Center in HTML and PDF formats.

Scope: System

Added in version: 3.20.2 (20 R2)


### `com.siemens.polarion.security.oauth2.scope`


Default value: openid profile email
This property is one of several that need to be set when configuring user authentication using the oAuth
(https://www.oauth.com) protocol. It specifies the scope of the permissions the Authorization request is asking for. Value is string
type. The value itself should be a scope/permission identifier recognized by the identity provider you are configuring. For example, on
the Microsoft identity platform's Microsoft Graph resource, Mail. Send in the request asks only to grant permission to send an email and
nothing else beyond that scope. The value set in this property is passed as a URL parameter to the request. Consult the provider's
documentation for valid values.

See also the `com.siemens.polarion.security.oauth2.*` properties.

NOTE: If your system is configured to use authentication.xml (introduced in version 21 R1) to authenticate users, you do not need
to set this property in polarion.properties.

For complete information on SSO configuration, see the Authentication guide section of Polarion Help. The content is available on
Support Center in HTML and PDF formats.

Scope: System

Added in version: 3.20.2 (20 R2)


### `com.siemens.polarion.security.oauth2.tokenUrl`

Default value: null
This property is one of several that need to be set when configuring user authentication using the oAuth (https://www.oauth.com)
protocol. It stores the URL of the endpoint from which an access token is requested.
See also the `com.siemens.polarion.security.oauth2.*` properties.

NOTE: If your system is configured to use authentication.xml (introduced in version 21 R1) to authenticate users, you do not need
to set this property in polarion.properties.

For complete information on SSO configuration, see the Authentication guide section of Polarion Help. The content is available on
Support Center in HTML and PDF formats.

Scope: System

Added in version: 3.20.2 (20 R2)


### `com.siemens.polarion.security.oauth2.tokenUrlMethod`

Default value: POST
This property is one of several that need to be set when configuring user authentication using the oAuth (https://www.oauth.com)
protocol. It stores the method to be used by Polarion to submit a request for an access token. Value is a string. Valid values are GET or
POST. The value you use depends on what the provider you are configuring for requires, which should be specified in their developer
documentation. See also the `com.siemens.polarion.security.oauth2.*` properties.

NOTE: If your system is configured to use authentication.xml (introduced in version 21 R1) to authenticate users, you do not need
to set this property in polarion.properties.

For complete information on SSO configuration, see the Authentication guide section of Polarion Help. The content is available on
Support Center in HTML and PDF formats.

Scope: System

Added in version: 3.20.2 (20 R2)


### `com.siemens.polarion.security.oauth2.userMapping.description`

Default value: null
This property is one of several that may need to be set when configuring user authentication using
the oAuth (https://www.oauth.com) protocol. It is used in mapping user credentials from a third-party identity provider to existing
users in a Polarion system, if the administrator chooses that option. (Otherwise, it is not used.) It specifies which field from the user's
detail, or from the id_token provided by the Oauth2 identity provider, will be mapped to the user's description on the Polarion side.

NOTE: If your system is configured to use authentication.xml (introduced in version 21 R1) to authenticate users, you do not need
to set this property in polarion.properties.

For complete information on SSO configuration, see the Authentication guide section of Polarion Help. The content is available on
Support Center in HTML and PDF formats.


Scope: System

Added in version: 3.20.2 (20 R2)


### `com.siemens.polarion.security.oauth2.userMapping.email`

Default value: email
This property is one of several that may need to be set when configuring user authentication using
the oAuth (https://www.oauth.com) protocol. It is used in mapping user credentials from a third-party identity provider to existing
users in a Polarion system if the administrator chooses that option. (Otherwise, it is not used.) It specifies which field from the user's
detail, or from the id_token provided by the Oauth2 identity provider, will be mapped to the user's email address on the Polarion side.

NOTE: If your system is configured to use authentication.xml (introduced in version 21 R1) to authenticate users, you do not need
to set this property in polarion.properties.

For complete information on SSO configuration, see the Authentication guide section of Polarion Help. The content is available on
Support Center in HTML and PDF formats.

Scope: System

Added in version: 3.20.2 (20 R2)


### `com.siemens.polarion.security.oauth2.userMapping.id`

Default value: "id" or "sub"
This property is one of several that may need to be set when configuring user authentication using
the oAuth (https://www.oauth.com) protocol. It is used in mapping user credentials from a third-party identity provider to existing
users in a Polarion system if the administrator chooses that option. (Otherwise, it is not used.) It specifies which field from the user's
detail, or from the id_token provided by the Oauth2 identity provider, will be mapped to the user's ID on the Polarion side.

The default value varies according to whether or not the `com.siemens.polarion.security.oauth2.userUrl` property is set. If it
is, then the default value is "id", otherwise it is "sub".

NOTE: If your system is configured to use authentication.xml (introduced in version 21 R1) to authenticate users, you do not need
to set this property in polarion.properties.

For complete information on SSO configuration, see the Authentication guide section of Polarion Help. The content is available on
Support Center in HTML and PDF formats.

Scope: System

Added in version: 3.20.2 (20 R2)


### `com.siemens.polarion.security.oauth2.userMapping.name`

Default value: name
This property is one of several that may need to be set when configuring user authentication using
the oAuth (https://www.oauth.com) protocol. It is used in mapping user credentials from a third-party identity provider to existing
users in a Polarion system if the administrator chooses that option. (Otherwise, it is not used.) It specifies which field from the user's
detail, or from the id_token provided by the Oauth2 identity provider, will be mapped to the user's user name on the Polarion side.

NOTE: If your system is configured to use authentication.xml (introduced in version 21 R1) to authenticate users, you do not need
to set this property in polarion.properties.

For complete information on SSO configuration, see the Authentication guide section of Polarion Help. The content is available on
Support Center in HTML and PDF formats.

Scope: System

Added in version: 3.20.2 (20 R2)


### `com.siemens.polarion.security.oauth2.userUrl`

Default value: null
This property is one of several that need to be set when configuring user authentication using the oAuth (https://www.oauth.com)
protocol. It stores the URL of the provider endpoint that issues an ID token as part of the process of issuing an Access token. Not all

providers do this. Check developer documentation of the provider you are configuring to see if they use this approach. If not needed,
leave the default null value. See also the `com.siemens.polarion.security.oauth2.*` properties.

NOTE: If your system is configured to use authentication.xml (introduced in version 21 R1) to authenticate users, you do not need
to set this property in polarion.properties.

For complete information on SSO configuration, see the Authentication guide section of Polarion Help. The content is available on
Support Center in HTML and PDF formats.

Scope: System

Added in version: 3.20.2 (20 R2)


### `com.siemens.polarion.security.permission.globalRolesWithQueryFieldRestriction`

Default value: empty set
Allows the blocking of queries that contain fields restricted to the user in permission management.

Takes a list of comma-separated global roles.

Users with a defined role will have their Lucene queries parsed and Polarion compares the User's permission to read fields contained in
the query and either allows for the query to be processed or denies it.

It also limits options in the query panels (filtering bubbles) based on these permission restrictions.

For the global and project group contexts, permissions are checked against all projects contained within it.

(For Web Services the global context is always assumed.)
If a user does not have permission to read a field in any of those projects (including the permission to read or access the project itself),
they will not be allowed to search using the field in the query for that context.

Example configuration:
com.siemens.polarion.security.permission.globalRolesWithQueryFieldRestriction=user,external
In this example, users with user or/and external global role are limited to only use those fields in Lucene queries that they have read
permission for.

(Along with any parent permissions, for example, to read Work Items.

Note:
Restrictions are not currently applied to the external codebase (extensions).

Scope: System

Added in version: 3.23.4 (2304 - current)


### `com.siemens.polarion.security.personalAccessToken.maxDaysBeforeExpiry`

Default value: 90
The maximum allowed time (in days) before a personal access token expires.

Scope: System

Added in version: 3.23.4 (2304 - current)


### `com.siemens.polarion.security.privateKey`

Default value: absent
Specifies a private key file location within a file system. The key is used for signing an authentication request sent to the identity
provider.

Scope: System

Added in version: 3.19.1 (19.1)


### `com.siemens.polarion.security.rememberMe.enabled`

Default value: true
Controls the presence of the Stay logged in option on all log on entry points, including the main log on page, and the popup window
shown after a session timeout. Also enables or disables the Remember me functionality during an authentication.


When the value is set to true or is empty, the option appears and Remember me is enabled.

​

Scope: System

Added in version: 3.22.1 (22 R1)


### `com.siemens.polarion.security.saml.assertionConsumerServiceUrl`

Default value: <base.url>/polarion/
Pertains to configuring Polarion for Single Sign-on (SSO). Stores the assertion consumer service URL (ACS URL). Value is a string.

IMPORTANT: IdP URLs in SAML SSO must contain a trailing slash character:
com.siemens.polarion.security.saml.assertionConsumerServiceUrl=https://polarion.ourserver.com/polarion/
NOTE: If your system is configured to use authentication.xml (introduced in version 21 R1) to authenticate users, you do not need
to set this property in polarion.properties.

For complete information on SSO configuration, see the Authentication guide section of Polarion Help. The content is available on
Support Center in HTML and PDF formats.

Scope: System

Added in version: 3.17.1 (17.1)


### `com.siemens.polarion.security.saml.certificatePath`

Default value: null
Pertains to configuring Polarion for Single Sign-on (SSO). Specifies the path where Polarion will search for a certificate for SAML
response validation. Value is a string. Polarion will search the specified directory for *.crt or *.cer files. The first certificate found is
used for SAML authentication.

NOTE: If your system is configured to use authentication.xml (introduced in version 21 R1) to authenticate users, you do not need
to set this property in polarion.properties.

For complete information on SSO configuration, see the Authentication guide section of Polarion Help. The content is available on
Support Center in HTML and PDF formats.

Scope: System

Added in version: 3.17.1 (17.1)


### `com.siemens.polarion.security.saml.forceAuthn`

Default value: false
Pertains to configuring Polarion for Single Sign-on (SSO). Controls whether or not the Identity Provider will force the user to reauthenticate even if user still has a valid session. Value is Boolean (true or false).

NOTE: If your system is configured to use authentication.xml (introduced in version 21 R1) to authenticate users, you do not need
to set this property in polarion.properties.

For complete information on SSO configuration, see the Authentication guide section of Polarion Help. The content is available on
Support Center in HTML and PDF formats.

Scope: System

Added in version: 3.17.1 (17.1)


### `com.siemens.polarion.security.saml.identityProviderMetadataUrl`

Default value: null
Pertains to configuring Polarion for Single Sign-on (SSO). Value is a string that can be used to store the Identity Provider metadata
location where Polarion will read login/logout endpoints and certificate, and other information to configure the application for SAML
authentication. The location can be on a remote server on HTTPS protocol or a local file.

Examples:

https://saml-server.yourdomain.com/FederationMetadata/2007-06/FederationMetadata.xml
file:///C:/Polarion/configuration/metadata.xml
NOTE: If your system is configured to use authentication.xml (introduced in version 21 R1) to authenticate users, you do not need
to set this property in polarion.properties.

For complete information on SSO configuration, see the Authentication guide section of Polarion Help. The content is available on
Support Center in HTML and PDF formats.

Scope: System

Added in version: 3.17.2 (17.2)


### `com.siemens.polarion.security.saml.issuer`

Default value: (see Description)
Pertains to configuring Polarion for Single Sign-on (SSO). Value is a string that can be used to store the URL of the Identity Provider
(IdP) that will issue the SAML 2.0 security token with user authentication info. The default value is the base URL of identityProvider.

NOTE: If your system is configured to use authentication.xml (introduced in version 21 R1) to authenticate users, you do not need
to set this property in polarion.properties.

For complete information on SSO configuration, see the Authentication guide section of Polarion Help. The content is available on
Support Center in HTML and PDF formats.

Scope: System

Added in version: 3.17.1 (17.1)


### `com.siemens.polarion.security.saml.relyingPartyIdentifier`

Default value: (see Description)
Pertains to configuring Polarion for Single Sign-on (SSO). Value is a string that can be used to store the entity identification or the issuer
for SAML AuthnRequest. The default value is <base.url> without a trailing slash character (/) at the end.

NOTE: If your system is configured to use authentication.xml (introduced in version 21 R1) to authenticate users, you do not need
to set this property in polarion.properties.

For complete information on SSO configuration, see the Authentication guide section of Polarion Help. The content is available on
Support Center in HTML and PDF formats.

Scope: System

Added in version: 3.17.1 (17.1)


### `com.siemens.polarion.security.saml.sloServiceUrl`

Default value: null
Pertains to configuring Polarion for Single Sign-on (SSO). Value is a string that can be used to store the URL to the Identity Provider's
(IdP) Single Logout service.

NOTES:
The logout response will be posted to this URL as the SAMLRequest parameter.

The configuration of Single Logout Service is optional and then nullable.


TIP: If your system is configured to use authentication.xml (introduced in version 21 R1) to authenticate users, you do not need to
set this property in polarion.properties.

For complete information on SSO configuration, see the Authentication guide section of Polarion Help. The content is available on
Support Center in HTML and PDF formats.

Scope: System

Added in version: 3.17.1 (17.1)


### `com.siemens.polarion.security.saml.ssoServiceUrl`

Default value: null
Pertains to configuring Polarion for Single Sign-on (SSO). Value is a string that can be used to store the URL to the Identity Provider's
(IdP) AuthnRequest service. The AuthnRequest will be posted to this URL as a SAMLRequest parameter.

NOTE: If your system is configured to use authentication.xml (introduced in version 21 R1) to authenticate users, you do not need
to set this property in polarion.properties.

For complete information on SSO configuration, see the Authentication guide section of Polarion Help. The content is available on
Support Center in HTML and PDF formats.

Scope: System

Added in version: 3.17.1 (17.1)


### `com.siemens.polarion.security.saml.userMapping.alternativeId`

Default value: null
Pertains to configuring Polarion for Single Sign-on (SSO). Value is a string optionally used to override the NameID attribute which is
used by default as userId attribute. Specifying this property, you can select an attribute other than the NameID attribute. If the chosen
attribute is empty, then an error message is shown.

Example values need to be in the following format:
http://schemas.xmlsoap.org/ws/2005/05/identity/claims/nameidentifier or http://schemas.xmlsoap.org/ws/2005/05/i
For a short list of possible example values see: http://www.miicard.com/for/developers/ws-federation/supportedsaml-claims
NOTE: If your system is configured to use authentication.xml (introduced in version 21 R1) to authenticate users, you do not need
to set this property in polarion.properties.

For complete information on SSO configuration, see the Authentication guide section of Polarion Help. The content is available on
Support Center in HTML and PDF formats.

Scope: System

Added in version: 3.17.2 (17.2)


### `com.siemens.polarion.security.saml.userMapping.description`

Default value: null
Pertains to configuring Polarion for Single Sign-on (SSO). You can configure SAML to send more attributes than just the Name ID. In
Polarion, the user attributes that can be automatically updated from the SAML response are Name, Email and Description. Value of this
property is a string that can be used to store the name of the SAML attribute used to fill Description.

See also:
- `com.siemens.polarion.security.saml.userMapping.name`
- `com.siemens.polarion.security.saml.userMapping.email`

NOTE: If your system is configured to use authentication.xml (introduced in version 21 R1) to authenticate users, you do not need
to set this property in polarion.properties.

For complete information on SSO configuration, see the Authentication guide section of Polarion Help. The content is available on
Support Center in HTML and PDF formats.

Scope: System

Added in version: 3.17.2 (17.2)


### `com.siemens.polarion.security.saml.userMapping.email`

Default value: http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress
Pertains to configuring Polarion for Single Sign-on (SSO). You can configure SAML to send more attributes than just the Name ID. In
Polarion, the user attributes that can be automatically updated from the SAML response are Name, Email and Description. Value of this

property is a string that can be used to store the name of the SAML attribute used to fill Email.

See also:
- `com.siemens.polarion.security.saml.userMapping.name`
- `com.siemens.polarion.security.saml.userMapping.description`

NOTE: If your system is configured to use authentication.xml (introduced in version 21 R1) to authenticate users, you do not need
to set this property in polarion.properties.

For complete information on SSO configuration, see the Authentication guide section of Polarion Help. The content is available on
Support Center in HTML and PDF formats.

Scope: System

Added in version: 3.17.2 (17.2)


### `com.siemens.polarion.security.saml.userMapping.name`

Default value: http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name
Pertains to configuring Polarion for Single Sign-on (SSO). You can configure SAML to send more attributes than just the Name ID. In
Polarion, the user attributes that can be automatically updated from the SAML response are Name, Email and Description. Value of this
property is a string that can be used to store the name of the SAML attribute used to fill Name.

See also:
- `com.siemens.polarion.security.saml.userMapping.email`
- `com.siemens.polarion.security.saml.userMapping.description`

NOTE: If your system is configured to use authentication.xml (introduced in version 21 R1) to authenticate users, you do not need
to set this property in polarion.properties.

For complete information on SSO configuration, see the Authentication guide section of Polarion Help. The content is available on
Support Center in HTML and PDF formats.

Scope: System

Added in version: 3.17.2 (17.2)


### `com.siemens.polarion.security.skipAuthenticationForNotificationImages`

Default value: false
Value is Boolean (true or false). If true, then no authentication is required for images referenced from notifications that uses the wiattachment-auth servlet.

Scope: System

Added in version: 3.17.0 (17)


### `com.siemens.polarion.security.sso.groupSync.retries`

Default value: 2
In Single Sign-On User Group synchronization, this property changes the number of attempts performed before failing synchronization.

(Polarion synchronizes its User Groups with those supplied by SSO providers if the User Group synchronization is enabled in the
authentication.xml file.) If there is a conflict with any resource during the process, the changes are rolled back, and the synchronization
will fail. This property limits the number of attempts performed before completely failing the synchronization process and eventually the
logon process with it.

Do not increase it to more than three attempts because it will make others wait for the user to synchronize before synchronizing their
User Groups. It is better to ask the user to log on again rather than create a long queue that could result in login timeouts.

​

Scope: System

Added in version: 3.21.2 (21 R2)


### `com.siemens.polarion.security.sso.groupSync.timeout`

Default value: 60000

In Single Sign-On User Group synchronization, this property changes the maximum waiting time in milliseconds before failing the
synchronization. Polarion synchronizes its User Groups with those supplied by SSO providers if the User Group synchronization is
enabled in authentication.xml. The SSO User Group synchronization process is locked cluster-wise, and each user must wait for their
turn when another user is already synchronizing their User Groups. The waiting process does not follow a queue (any user can be
chosen next), so this property gives the maximum waiting time a user should wait for the synchronization.

There are two main reasons for this property to exist:
1. Users cannot wait forever to log on, and the login request will most likely eventually timeout.

2. If a user attempted to log on repeatedly because of a login timeout or didn't want to wait for synchronization to complete, they

would be added to the queue again.

This would make it unnecessarily long. (Or potentially infinite, causing the server to become unresponsive.)
Scope: System

Added in version: 3.21.2 (21 R2)


### `com.siemens.polarion.security.ssoHomePageUrl`

Default value: null
Pertains to configuring Polarion for Single Sign On (SSO). Value is a string that can be used to specify the URL of a "Home Page" on
the Identity Provider (IdP) server where a user can navigate in case there is nothing to present on the Polarion side, like a logout page
or landing page with some warning or error message coming from the IdP.

The link should navigate a user to a page on the IdP side where he/she can contact the administrator or perform logout or do any SSO
related tasks.

NOTE: If your system is configured to use authentication.xml (introduced in version 21 R1) to authenticate users, you may not
need to set this property in polarion.properties. In fact, there is no equivalent in authentication.xml. When multiple log-on
options are configured, users who log off are returned to the log-on screen, where the different options are presented. However, the
URL value is still read from polarion.properties when using just one SSO authentication provider, as the login screen is skipped in
this special case.

For complete information on SSO configuration, see the Authentication guide section of Polarion Help. The content is available on
Support Center in HTML and PDF formats.

Scope: System

Added in version: 3.17.2 (17.2)


### `com.siemens.polarion.security.tcsso.loginUrl`

Default value: null
Value is a string that can be used to store a URL that leads to the Teamcenter Security Service - Login Service.

NOTE: If your system is configured to use the authentication.xml file (introduced in Polarion 21 R1) to authenticate users, you do
not need to set this property in the polarion.properties file.

Scope: System

Added in version: 3.17.0 (17)


### `com.siemens.polarion.security.tcsso.serviceUrl`

Default value: null
Value is a string that can be used to store a URL that leads to the Teamcenter Security Service - Identity Service (a.k.a SSO Service).

NOTE: If your system is configured to use the authentication.xml file (introduced in Polarion 21 R1) to authenticate users, you do
not need to set this property in the polarion.properties file.

Scope: System

Added in version: 3.17.0 (17)


### `com.siemens.polarion.systemload.loggingTimeInterval`

Default value: 10000
Specifies the time interval for logging of system load average. Value is an integer representing milliseconds.


Scope: System

Added in version: 3.18.2 (18.2)


### `com.siemens.polarion.systemload.minimalValueToLog`

Default value: 1
The threshold value is a double value.

The threshold from which to start logging the system load average, the values refer to the load of a single CPU core.

The system load average value of a single-core is (system load average/core number).

The value provided from the system load average is not a percentage of the CPU usage.

For example, with a CPU usage of 88.3, the system load average could be 43.

A useful article can be found at: http://www.brendangregg.com/blog/2017-08-08/linux-load-averages.html
Scope: System

Added in version: 3.18.2 (18.2)


### `com.siemens.polarion.tc.sso.app.id`

Default value: -The following property should be set in the polarion.properties file to integrate Teamcenter Configurator.

The Teamcenter Application ID must be set to integrate Teamcenter Configurator in a Single Sign-On setup.

`com.siemens.polarion.tc.sso.app.id=<TeamcenterAppID>`

This value should be the same value that is set when configuring Teamcenter Security Services (TcSS) for the Teamcenter Application ID.

​

Scope: System

Added in version: 3.23.4 (2304 - current)


### `com.siemens.polarion.tc.uri`

Default value: -The following property should be set in the polarion.properties file to integrate Teamcenter Configurator.

The Teamcenter URI must be set to integrate Teamcenter Configurator.

`com.siemens.polarion.tc.uri=http{s}://node:port/tc`

Example:
com.siemens.polarion.tc.uri=https://vc6s012:7001/tc
Scope: System

Added in version: 3.23.4 (2304 - current)


### `com.siemens.polarion.tfsconnector.bypassrules.enabled`

Default value: true
Enable or disable the bypassrules option in REST calls .The option is used to bypass the existing rules for creating and updating items
in Microsoft Team Foundation Server (TFS). However, to set this option in REST calls, the user must have specific permissions in TFS,
and granting this user-permission is not always desirable.

Scope: System

Added in version: 3.19.3 (19.3)


### `com.siemens.polarion.tfsconnector.connectionCheckCollections`


Default value: DefaultCollection
If a Connection configured for a Team Foundation Server (TFS) server fails to establish a connection (error "Not a TFS Server"), and
"DefaultCollection" isn't configured on the TFS server, then you can set this property to specify the name of the TFS collection to use for
the connection check by a specific Connection. Please note that setting this property is not necessary if the user specified in the
Connector configuration has permissions to access the TFS REST resource <SERVER>/_apis/projectcollections.

The expected value is a comma-separated list of tuples that each consist of Connection ID and TFS collection name, with the tuple
elements separated by colons. Value format: connection.id.1:tfs-collection-a,connection.id.2:tfs-collection-b
Example:
com.siemens.polarion.tfsconnector.connectionCheckCollections=tfs-2018-dev:TeamEpsilonCollection,tfs2018-qa:DefaultCollection
Connection with the ID tfs-2018-dev will use the TFS collection TeamEpsilonCollection to check the connection
between Polarion and TFS, and the Connection with the ID tfs-2018-qa will use TFS collection DefaultCollection.

Scope: System

Added in version: 3.19.1 (19.1)


### `com.siemens.polarion.ui.document.lazyLoad.enabledByDefault`

Default value: 200
Controls the state of on-demand Work Item ("lazy") loading. Value is a positive integer. Lazy loading is enabled for LiveDoc
documents when the count of contained Work Items is equal to or greater than the value of this property.

NOTE: Used only when the on-demand Work Item loading feature ("lazy loading") is enabled for the system in property
`com.polarion.ui.document.lazyLoad`.

Scope: System

Added in version: 3.10.3 (2016 SR3)


### `com.siemens.polarion.ui.documents.table.breakWord.enabled`

Default value: true
This property allows you to disable word wrapping (breaking up) of long words in tables within Polarion Documents.

(Word wrapping prevents text from overflowing document borders.)
In Polarion's Document Editor, if there is a long word in a table cell, it is wrapped by default and divided once its characters reach the
defined borders.

In some cases, for example, if a table column is only a couple of characters wide, this makes the text hard to read.

Use this property to disable the default word wrap and enable tables to overflow the document borders.

Scope: System

Added in version: 3.22.2 (22 R2)


### `com.siemens.polarion.ui.inlineEditingInWiTable.enabled`

Default value: true
Set to false to disable Inline editing of Work Item attributes in flat and tree table views.

Scope: System

Added in version: 3.22.2 (22 R2)


### `com.siemens.polarion.ui.internalLoginHeight`

Default value: 390
Pertains to configuring Polarion for Single Sign-on (SSO). Value is a positive integer that specifies the height in pixels of the internal
login window - mainly needed in a Single Sign-on (SSO) environment.

See also: `com.siemens.polarion.ui.internalLoginWidth`

NOTE: If your system is configured to use authentication.xml (introduced in version 21 R1) to authenticate users, you do not need
to set this property in polarion.properties.

For complete information on SSO configuration, see the Authentication guide section of Polarion Help. The content is available on
Support Center in HTML and PDF formats.

Scope: System

Added in version: 3.17.0 (17)


### `com.siemens.polarion.ui.internalLoginWidth`

Default value: 431
Pertains to configuring Polarion for Single Sign-on (SSO). Value is a positive integer that specifies the width in pixels of the internal login
window - mainly needed in a Single Sign-on (SSO) environment.

See also: `com.siemens.polarion.ui.internalLoginHeight`

NOTE: If your system is configured to use authentication.xml (introduced in version 21 R1) to authenticate users, you do not need
to set this property in polarion.properties.

For complete information on SSO configuration, see the Authentication guide section of Polarion Help. The content is available on
Support Center in HTML and PDF formats.

Scope: System

Added in version: 3.17.0 (17)


### `com.siemens.polarion.ui.linkedRevisions.renderingLimit`

Default value: 20
Sets the maximum number of Linked Revisions shown on the Work Item Properties sidebar.

This property does not affect how many Linked Revisions will be loaded when viewing the Work Item itself. (It's only for what Linked
Revisions appear in the Work Item Properties sidebar.) If the number of Linked Revisions is higher than this limit, then a Show more
link appears. When users click Show more, they are directed to the Work Item where all Linked Revisions are visible in the Linked
Revisions extension.

Scope: System

Added in version: 3.19.3 (19.3)


### `com.siemens.polarion.ui.matrix.hardLimit`

Default value: 50000
Value is a positive integer that specifies the hard limit of the number of cells in the comparison view when comparing Variants.

WARNING: Setting too high a value might exhaust browser memory, consume excessive CPU and make the page unresponsive.

See also: `com.siemens.polarion.ui.matrix.softLimit`

Pertains to variant management using the Polarion VARIANTS add-on and the PureVariants server.

Scope: System

Added in version: 3.17.2 (17.2)


### `com.siemens.polarion.ui.matrix.softLimit`

Default value: 10000
Value is a positive integer that specifies the soft limit of the number of cells in the comparison view when comparing Variants.

When the limit is reached, users are notified and given the option to continue or cancel. If the users opts to accept a number that equals
or exceed the hard limit set in `com.siemens.polarion.ui.matrix.hardLimit`, that limit is enforced.

Pertains to variant management using the Polarion VARIANTS add-on and the PureVariants server.

Scope: System

Added in version: 3.17.2 (17.2)


### `com.siemens.polarion.ui.maxReferencedWorkItemsForInsert`

Default value: 5000
Value is a positive integer that specifies the maximum number of referenced Work Items that can be inserted into a LiveDoc
("Document") in a single operation. It is not a limit on the total number of referenced items the Document can contain.

Scope: System

Added in version: 3.10.2 (2016 SR2)


### `com.siemens.polarion.ui.nameIdAutoFilling.enabled`

Default value: true
Enables/disables auto-filling for the Name(ID) field in Polarion dialog boxes like the following:
Create LiveDoc Document
Create Classic Wiki Page
Create LiveReport Page
Create Info Page
Create Space
Create Plan (for all Plan types)
Scope: System

Added in version: 3.22.1 (22 R1)


### `com.siemens.polarion.ui.referencingDocuments.softLimit`

Default value: 20
Value is a positive integer that specifies the maximum number of Documents that are loaded for a Work Item when asking for the
Documents that reference it.

The Documents are displayed in the "Documents" section of the Work Item Properties sidebar of the Document Editor.

Also defines the number of Documents that are immediately loaded and displayed in the "Open in Document" drop-down menu of
a Work Item page. (If the total number of Documents exceeds this number, then they will only be loaded when a user clicks on the
drop-down menu.)
NOTE: Increasing the value of this property might slow down the opening of Documents or Work Item pages.

Scope: System

Added in version: 3.19.0 (19)


### `com.siemens.polarion.ui.showStackTraces`

Default value: false
Defines whether or not to show a stack trace and error report in the error dialog box when an error occurs. Value is Boolean (true or
false).

If true, the stack trace appears in the error dialog box when the user clicks Show Details.

If false, only the Error ID is shown. The user can search for this ID in the system log to find the stack trace.

Scope: System

Added in version: 3.20.1 (20 R1)


### `com.siemens.polarion.ui.testExecution.oldExecutionView.enabled`

Default value: false
Enables the use of the following runtime property:

### `testManagement.useOldExecutionView`

(See the Runtime Properties section of this document for more information.)
Warning
This feature is no longer tested, is disabled by default, and will be removed entirely in Polarion 2304.


Scope: System

Added in version: 3.22.1 (22 R1)


### `com.siemens.polarion.ui.testExecution.testRunSearchLimit`

Default value: 100
Value is an integer that specifies the maximum number of Test Runs that are checked for the purpose of creating a list of usable Test
Runs in the Execute Test extension of a Test Case. A value of -1 means no limit.

NOTE: Performance can be improved by limiting the number of persisted Test Runs if there are many unfinished ones.

Scope: System

Added in version: 3.10.2 (2016 SR2)


### `com.siemens.polarion.ui.treeTable.autoRefreshEnabled`

Default value: true
Enables or disables automatic refresh of query results in the Tree view of Work Items. Value is Boolean (true or false).

If true (enabled), the search is triggered, and the results refreshed automatically when entering the Tree View, and every time the query
changes. This is the behavior before version 20 R2. Due to the potential depth of the results in this view, there can be some impact on
performance if many users use it frequently, triggering automatic refresh when it may not actually be needed.

If false (disabled), the search is never triggered automatically in the Tree view. Users must explicitly trigger the search, either by clicking
the magnifying glass icon, or the Refresh button in the toolbar.

Scope: System

Added in version: 3.20.2 (20 R2)


### `com.siemens.polarion.ui.treeTable.deduplicationLimit`

Default value: 500000000
Sets the maximum allowed "amount of work" that can be done while trying to remove duplicate roots when constructing a Tree View
result. The amount of work is internally measured as the number of tree nodes and/or Work Items that are traversed during the process
of removing duplicate roots. The value of this property specifies the upper limit of that number.

This property can be used to prevent users from depleting server resources by launching multiple Tree View queries with very resourceintensive duplicate root removal. If the limit is reached during construction of a Tree View result, the construction is restarted with
removal of duplicate roots disabled. In that case, the user is notified that the tree may possibly contain duplicate roots.

The value of this property is taken into consideration only when the `workitems.treeTable.removeDuplicateRoots` property is
set to true. If it is set to false, no duplicate root removal is undertaken.

Scope: System

Added in version: 3.22.1 (22 R1)


### `com.siemens.polarion.ui.workitemPreview.refreshButton.show`

Default value: true
Shows or hides the Refresh button in the Linked Work Items section of the Work Items page. The button refreshes the list of linked Work
Items in that section.

When set to true, the button is shown. When set to false, the button is hidden.

Scope: System

Added in version: 3.21.2-p2 (Cumulative patch 21 R2 P2)


### `com.siemens.polarion.userMap.cleaningInterval`

Default value: 60000
Value is a positive integer that specifies the time interval (in milliseconds) after which the coordinator in a multi-server configuration
clears the user map to free slots and prevent logging that the license has a shortage of user slots.


For information on multi-server and clustered setups, see the Deployment and Maintenance Guide, available as a PDF download in
the Polarion product center on Support Center.

Scope: System

Added in version: 3.17.3 (17.3)

controlHostname
Default value: localhost
The hostname for shutdown requests and communication in a Polarion Cluster setup.

Add the port for the hostname in the following property:
controlPort=
Note: See the Deployment and Maintenance Guide on Support Center for more information on Clustered setups.

Scope: System

Added in version: 3.4.0

controlPort
Default value: 8887
The port for the hostname used for shutdown requests and communication in a Polarion Cluster setup.

Add the hostname in the following property:
controlHostname=
Note: See the Deployment and Maintenance Guide on Support Center for more information on Clustered setups.

Scope: System

Added in version: 3.4.0


### `createproject.default.location`

Default value: none
Value is a string that can be used to specify a custom default repository location for a new project in the New Project wizard. If not
defined, the hard coded default location is used.

NOTE:
When this property is specified and the property `createproject.default.useUserId` is enabled (true), then the New Project
wizard is pre-filled with value of this property + userId, and the project ID is pre-filled with userId (i.e. the ID of the current user).

Scope: System

Added in version: 3.3.1


### `createproject.default.useUserId`

Default value: false
Value is Boolean (true or false). When set to true, the New Project wizard is pre-filled with value set in property
`createproject.default.location` + `userId` and the project ID is pre-filled with `userId` (i.e. the ID of the current user).

Scope: System

Added in version: 3.3.1


### `createproject.limitedAccessMessage`

Default value: none
Value is of string type that can be used to store HTML to be displayed in the Create New Project wizard when the user doesn't have the
global administrator role but does have permission to create a new project.

Scope: System

Added in version: 3.3.1

curator-dont-log-connection-problems
Default value: true
In a multi-server/clustered setup, tells Curator if it should log some connection problems. Value is Boolean (true or false). If set to true it
will not log them.

For information on multi-server and clustered setups, see the Deployment and Maintenance Guide, available as a PDF download in
the Polarion product center on Support Center.

Scope: System

Added in version: 3.8.0 (2014)


### `default.project.template.(licenseId)`

Default value: see Description

Defines what project template is offered as the default in the Create Project dialog.

There is a separate property for each license. If the license-based property is not defined, then no default template is used.

Default Values:
```
default.project.template.ALM=alm_vmodel
default.project.template.Pro=alm_vmodel
default.project.template.QA=qa_vmodel
default.project.template.Requirements=req_vmodel
default.project.template.XEnterprise=alm_vmodel
default.project.template.XPro=alm_vmodel
default.project.template.XBase=alm_vmodel
```
Project template names can be found in Global Administration > Project Templates.

Scope: System

Added in version: 3.4.0

disableKeyboardShortcuts
Default value: none
You can disable all Polarion keyboard shortcuts (including those for multi-edit) by setting this parameter to true in the
polarion.properties file.

Scope: System

Added in version: 3.1.2

disableLicenseAssignmentInLDAPSynchronize
Default value: false
Enables or disables assigning of the "default (configured)" license to new users during LDAP synchronization. Value is Boolean (true or
false).

Scope: System

Added in version: 3.3.0

dontUseSmartDecimalHoursDurationFormatParsing
Default value: false
Disables smart parsing when set to true.

The value for hours in time reporting fields (Initial Estimate, Time Spent, and so on) must be entered as a decimal value rather than the default fra
If the useDecimalHoursDurationFormat property is set to true, hour durations in all of the time reporting fields are displayed and entered as
example 22.33.


The examples displayed by clicking on the "?" next to time input fields are changed when this feature is enabled, and the export option Convert Du
hours is not displayed in the export dialog.

Storage in XML persistence and pre-2011 LiveDocs is still in the fractional format; only hours are not converted to days. So the value in the example
stored as 22 1/3h. It is stored that way rather than 22 33/100h because of the smart parsing of user-entered values to the fractional format, whi
decimal representation of fractions (y/3, y/6, and y/12). So, for example, entering 0.08 or 0.083 is parsed as 1/12h.

Setting dontUseSmartDecimalHoursDurationFormatParsing to true disables this smart parsing.

Scope: System

Added in version: 3.2.3

enableCreateAccountForm
Default value: false
Controls whether the Create your Polarion Account link appears on the log-on screen.

If true, the self-registration link appears.

If false, it is hidden.

Scope: System

Added in version: 3.1.3


### `error.report.email`

Default value: none
Add the email address you want error reports sent to.

This property is empty by default for new Polarion installations.

Scope: System

Added in version: 3.0.0

headingsObeyDeletePermission
Default value: false
Controls deleting of Work Items of type heading. Value is Boolean (true or false). If false, then Work Items of type heading can be
deleted by users who do not have the permission to delete Work Items - specifically, the WorkItem.DELETE permission.

Scope: System

Added in version: 3.5.0 (2011)

hideErrorDialogs
Default value: false
Value is Boolean (true or false). When set to true, never show any error dialog icon in the Polarion UI.

Scope: System

Added in version: 3.1.2

lazyAllowedValuesLoadLimit
Default value: 10
Value is a positive integer that controls how many list items are loaded into combo boxes by default. When the full list of items exceeds
the specified number, additional items are loaded only on demand as the user scrolls. Optimizes the handling of the list by using "lazy"
(i.e. on-demand) loading" of list items when a list is extensive.

NOTE: Setting too large a value can degrade performance, as users are then forced to wait for many items to load. On systems with
many active users, the cumulative effect can be significant.

​

Scope: System

Added in version: 3.1.2

licenseForNewUserAccount
Default value: none
Controls how licenses are allocated when users log on or new user accounts are created via different authentication methods or
providers.

Example:
licenseForNewUserAccount=[LICENCE-TYPE.FEATURE-SET]
[LICENSE-TYPE] is one of the following:
named
concurrent
concurrentGroup

[FEATURE-SET] may vary according to the current Polarion licenses available. It will be something
like QA, ALM, REQUIREMENTS, REVIEWER, etc.

To find the licenses currently on your system, open global Administration, and in Navigation, select License.

Examples:
licenseForNewUserAccount=namedALM
licenseForNewUserAccount=concurrentQA
licenseForNewUserAccount=concurrentGroupREVIEWER
Note: If concurrent license groups are defined in the global configuration, it is possible to specify a concurrent license group in the
licenseForNewUserAccount property rather than a license. For information on these groups, see the embedded Quick Help on the
License page of global Administration and the Manage Polarion licenses section in Polarion's Administrator and User Help on
Support Center.

How a license is assigned:
If no value is specified in the property, users are given the first available "lowest" license - that is, the most restrictive. For example, if no
free concurrent slots are available, Polarion will try to allocate a named license, and so on. It goes from the fewest features
(currently REVIEWER), incrementally towards full features (currently ALM), depending on what slots are available.

Scope: System

Added in version: 3.2.1

loadAllLimit
Default value: 3000
Value is a positive integer that specified a limit on the number of items in the Table view of Work Items that can be loaded by the Load
more button. If the total number of items found is less than the limit specified in this property, then the button label changes to Load all.

Scope: System

Added in version: 3.4.2


### `log.ssoentries.on.sessionevent`

Default value: false
Value is Boolean (true or false). If true, then the system logs additional information about user sessions in Polarion’s internal Single
Sign-On support. This can help administrators to analyze issues preventing users from being logged out.

Scope: System

Added in version: 3.2.1


### `login.companylogo`

Default value: null

Enables an administrator to add a custom logo image to the Polarion login page. Value is a string that can specify the relative or
absolute URL of the logo image.

If a multi-instance system configuration is used:
The entry page uses `login.companylogo` that appears next to the Polarion logo
Login screen of individual instances shows `com.polarion.logoURL`
The UI displays `com.polarion.logoURL` in the Navigation header
If multi-instance system configuration is not used:
There is no entry page
The login page shows `login.companylogo` that appears next to the Polarion logo
The UI displays `com.polarion.logoURL` in the Navigation header
Scope: System

Added in version: 3.5.0 (2011)

luceneFSyncOnCommit
Default value: false
Value is Boolean (true or false). If set to true, Lucene does fsync during commit to index, forcing the OS to flush the written files to the
physical storage, which is normal Lucene behavior. To optimize overall system performance, Polarion development has patched Lucene
not to do this by default, and implemented this property to restore default Lucene behavior in case any customer prefers it.

Scope: System

Added in version: 3.8.1 (2014 SR1)

luceneMaxClauseCount
Default value: 20000
Defines how many AND/OR components that a Lucene query can have. This includes simple range queries that are expanded internally
to this form by Lucene. Value is a positive integer.

NOTE: Polarion itself requires queries with many OR components if there are many links (thousands) to a single Work Item.

Scope: System

Added in version: 3.0.3

luceneMaxFieldLength
Default value: 50000
Defines the maximum number of terms that will be indexed for a single field in a LiveDoc Document. Value is a positive or negative
integer (see note below re: negative value).

Words that appear too far from the beginning of a field (like "Description" in a Work Item), will not be searchable. A unique example is an
artificial field that contains words that are searched for via a full-text search.

This property's value should be set higher if the following error is logged:
"Lucene: maxFieldLength 50000 reached, ignoring following tokens".

NOTE: Setting it to a negative value (-1) will remove a limit but according to Lucene’s documentation an "OutOfMemory" error may still
occur.

ATTENTION: If the value of this property is increased due to errors in the Polarion log, an index must be refreshed to fix the index
entries of truncated fields.

Scope: System

Added in version: 3.2.1

luceneRAMBufferSizeMB
Default value: 128

Controls the amount of RAM that may be used for buffering added documents and deletions before they are flushed to the Directory.

Value is a positive integer representing megabytes. More detailed information is available in the Apache Lucene javadoc:
http://lucene.apache.org/core/4_7_0/core/org/apache/lucene/index/IndexWriterConfig.html#setRAMBufferSizeMB(do
Scope: System

Added in version: 3.8.1 (2014 SR1)

maxAttachmentSize
Default value: 200000000
Controls the maximum size of any attachment in Polarion. Value is a positive integer representing bytes. If an attached file is larger than
the specified limit, the upload is stopped. Applies to Work Item attachments, Wiki attachments, Document attachments and imported
Documents.

Scope: System

Added in version: 3.5.1 (2011 SR1)

password
Default value: none
The password for Polarion.

Scope: System

Added in version: 3.0.0


### `pdf.export.fonts.dir`

Default value: none
The location of the folder containing the fonts that you want to use in exported PDFs.

Example values:
Windows
pdf.export.fonts.dir=file:///C:/workdir/fonts
Linux
pdf.export.fonts.dir=file:///opt/fonts
Scope: System

Added in version: 3.5.0 (2011)


### `polarion.files.repository`

Default value: none
It is set by Polarion before a build and cannot be changed.

It is the BIR location top-level folder.

Scope: Build

Added in version: 3.0.0


### `polarion.link.merged.revisions`

Default value: false
Value is Boolean (true or false). If true, this property causes merged revisions to also be linked to the proper Work Items.

NOTE: Duration of reindexing is significantly prolonged if this property is true.

Scope: System

Added in version: 3.3.0


### `polarion.parameter.buildTimeout`

Default value: 1440min

You can use this property to define a specific timeout for a build.

Example:
polarion.parameter.buildTimeout=[Enter the number of minutes before a build times out. If not
defined, the default is 1440 minutes.]
Scope: Build

Added in version: 3.20.1 (20 R1)


### `polyglot.js.nashorn-compat`

Default value: false
This Graaljs property provides full compatibility with Nashorn scripts.

The property is delivered with the GraalVM and may become unavailable in future releases. (It is just a temporary transitional mode, and
all customers should migrate to using GraalVM without using this compatibility mode.

The Scripting SDK (Polarion Scripting Guide & Examples) provides information and links on how to migrate.

TIP: See https://docs.oracle.com/en/graalvm/enterprise/20/docs/reference-manual/js/NashornMigrationGuide/ for additional information.

​

Scope: System

Added in version: 3.22.1 (22 R1)

prioritizationModeField
Default value: null
Value is a string that can be used to contain the ID of a custom field to be used as the "priority" field for prioritization or re-scaling
operations using the Easy Prioritization feature of Plans. If valus is null, the default Priority field of Work Items is used. If a custom field
is desired for prioritizing Work Items in Plans, you can add this property to the polarion.properties file and specify the field ID in its
value.

Example: prioritizationModeField=my_plan_priority_field
NOTE: The custom field should already exist in the configuration, and its type must be float.

For more information on the feature, see online Help topic Plan and prioritize Work Items.

Scope: System

Added in version: 3.7.2 (2013 SR2)

prioritizationModeIncrement
Default value: 10
Value is a positive integer that specifies the amount by which the configured Priority field is incremented or decremented during
prioritization or re-scaling operations using the Easy Prioritization feature for Plans. The specified value is applied when moving an item
to top position in the tracker table when using Easy Prioritization.

For more information on the feature, see online Help topic Plan and prioritize Work Items.

Scope: System

Added in version: 3.7.2 (2013 SR2)

repo
Default value: http://localhost:80/repo/
Points Polarion to the repository you want to use.

By default, the value is set to repo=http://localhost:81/repo/ or http://polarion.yourdomain.com/repo/
Note: If you want to grant secure access to the repository, use https:// instead of http://
Scope: System

Added in version: 3.0.0

repoSystem
Default value: null
Value is a string that can optionally be used to provide an alternative repository URL to be used for read-only access by the system user.

If this property is not set (i.e. is not present, or is commented out in the polarion.properties file, or its value is null), the system user
uses the normal access URL that's set in the repo property.

Examples:
repoSystem=file:///C:/Polarion/data/svn/repo
repoSystem=svn://localhost/C:/Polarion/data/svn/repo
Scope: System

Added in version: 3.7.2 (2013 SR2)

rolesForNewUserAccount
Default value: user
Specifies the global roles that will be assigned to new users that were created, either by self-registration via the Create your Polarion
Account link on the logon form, or by the LDAP synchronization feature. The value is a string that can contain a comma-separated list
of global role IDs.

WARNING: The user role must be present in the list, or users will not be able to log in.

NOTE: If your system is configured to use authentication.xml (introduced in version 21 R1) to authenticate users, you do not need
to set this property in polarion.properties.

For complete information on SSO configuration, see the Authentication guide section of Polarion Help. The content is available on
Support Center in HTML and PDF formats.

Scope: System

Added in version: 3.1.3


### `search.wordBoundaries`

Default value: splitByPattern
Defines how word boundaries are defined for indexing. Value is string type. Two values are supported:
splitByPattern - the input is split to words using a regex pattern
standard - the word boundaries are defined according to the Unicode standard
(http://www.unicode.org/reports/tr29/#Word_Boundaries).

NOTE: Always use standard for Asian languages.

Scope: System

Added in version: 3.8.1 (2014 SR1)


### `search.wordBoundaries.splitByPattern`

Default value: \s+
Defines the pattern to be used when using search.wordBoundaries=splitByPattern. It is used
with java.lang.String.split(String)Value is string type. The default value ensures that the text is split by white space. Leading
and trailing non-alphanumeric characters are trimmed.

Example: "Hello! DPP-1234 _help_." is split to 3 words - "Hello", "DPP-1234", and "help".

Scope: System

Added in version: 3.8.1 (2014 SR1)


### `secure.approvals`


Default value: false
Enable or disable secure approvals of Work Items. Value is Boolean (true or false).

To enable the secure approvals feature, add or uncomment this line in the polarion.properties file: secure.approvals=true
Scope: System

Added in version: 3.4.3


### `secure.approvals.comment`

Default value: null
Value is a string that can be used to specify the message displayed to end users after an item is securely signed. Value is used as the
text of a new comment created when a user enters a password to confirm a secure approval.

Example: secure.approvals.comment=The current item has been securely e-signed
NOTE: The default value is an internal reference to a system process that renders a default text: Item was e-signed.

Scope: System

Added in version: 3.5.2 (2011 SR2)


### `secure.approvals.comment.onBehalfOf`

Default value: null
Displays the state of the approval. Value is a string, similar to `secure.approvals.comment`, except it supports one user confirming
secure approval on behalf of another user.

Supports the following variables: $img, $verdict, $user, $otheruser:
$img (inserts an approval verdict image)
$verdict (inserts the approval verdict)
$user (expands to the name of the currently logged-in user),
$otheruser (expands to the name of the user on whose behalf $user is approving)
Variable $img should not be changed, as it will be evaluated when approval state is set.

Example:
secure.approvals.comment.onBehalfOf=Current approval verdict: $img $verdict (by $user on behalf of
$otheruser)
NOTE: The default value is an internal reference to a system process that renders a default text: Approval verdict: $img
$verdict (on behalf of $otheruser)
Scope: System

Added in version: 3.8.2 (2014 SR2)


### `secure.approvals.comment.text`

Default value: null
Displays the state of the approval. Value is a string, that displays the state of the approval.

Supports the following variables: $img, $verdict, $user:
$img (inserts an approval verdict image)
$verdict (inserts the approval verdict)
$user (expands to the name of the currently logged-in user)
Variable $img should not be changed, as it will be evaluated when approval state is set.

Example:
secure.approvals.comment.text=Current approval verdict from $user is: $img $verdict
NOTE: The default value is an internal reference to a system process that renders a default text: Approval verdict: $img
$verdict

Scope: System

Added in version: 3.18.2 (18.2)


### `secure.dialog.message`

Default value: none
The value of this property is a string of characters.

The string appears as a message in the password dialog box when an end user invokes one of the configured secure workflow actions.

You only need to set this property if you want to override the system default message for the dialog box.

Scope: System

Added in version: 3.4.3


### `secure.dialog.title`

Default value: none
The value of this property is a string of characters.

The string appears as the title of the password dialog box when an end user invokes one of the configured secure workflow actions.

You only need to set this property if you want to override the system default title for the dialog box.

Scope: System

Added in version: 3.4.3

showJobCancelButton
Default value: false
Value is Boolean (true or false). When set to true, this property enables the Cancel button in the Monitor topic of Navigation, which
allows users to invoke cancellation of a running job.

NOTE: Not all jobs can be cancelled. The button has no effect in such cases.

Scope: System

Added in version: 3.4.1


### `skip.data.preloading`

Default value: false
Enables or disables the preloading of data - i.e. the loading of various configurations and objects to cache after the Polarion server has
started. Value is Boolean (true or false).

Scope: System

Added in version: 3.0.0


### `support.license.email`

Default value: license@polarion.com
Value is a string that contains the actual email address to contact to get support for license activation.

Scope: System

Added in version: 3.9.0 (2015)


### `svn.access.file`

Default value: none
The path to the Subversion's access file. This file defines access rights as they are shown in (and manipulated through) Administration /
User Management / Access Management.

Scope: System

Added in version: 3.0.0


### `svn.passwd.file`


Default value: null
Specifies Subversion passwd file to be accessed by Polarion for internal SVN access.

Before 21 R1, this file was used for both internal SVN access and Polarion user authentication. Since 21 R1, this property specifies only
the file for internal SVN access. This file now contains only generated passwords.

Password file for user authentication is not configurable directly. Its name is always the value of this property plus "_credentials" prefix.

Default value is not specified, so this property is mandatory for Polarion startup.

Scope: System

Added in version: 3.0.0


### `svnkit.http.encoding`

Default value: none
1. If the Polarion server is running on Linux, LDAP users can have non-ASCII passwords, provided the following line exists

uncommented in the polarion.properties system configuration properties file:
`svnkit.http.encoding=UTF-8`

2. If the Polarion server is running on Windows, LDAP users can have passwords containing characters from a subset of non-ASCII

characters if one of the following lines exists
uncommented in the polarion.properties file:
`svnkit.http.encoding=iso-8859-1svnkit.http.encoding=<LOCAL_CHARSET>`
Scope: System

Added in version: 3.3.1


### `TomcatService.ajp.secret`

Default value: ""
Enables Tomcat to require a secret in every request. Note: Apache must be configured to add the secret to requests. This property, and
the secret, are not used by default. Enable them only if you require the extra secret functionality.

Scope: System

Added in version: 3.21.1 (21 R1)


### `TomcatService.ajp13-port`

Default value: 8889
Value is a positive integer that specified the port number for the Tomcat AJP/1.3 connector.

Scope: System

Added in version: 3.0.0


### `TomcatService.connector-maxThreads`

Default value: 200
Tomcat's maxThreads limit.

maxThreads is the maximum number of request processing threads created by the Tomcat Connector.

(It determines the maximum number of simultaneous requests that can be handled.)
Set this property in the polarion.properties file if you do not want to use Tomcat's default maxThreads value of 200.

See https://tomcat.apache.org/tomcat-9.0-doc/config/http.html#Standard_Implementation for more information.

Scope: System

Added in version: 3.22.2 (22 R2)


### `TomcatService.connector.address`

Default value: 127.0.0.1

Specify the IP or host that Tomcat will listen for.

Default is 127.0.0.1.

Before the update to Tomcat 9.0.40, a default address of 0.0.0.0 was used.

After the update, it changed to 127.0.0.1. (Which is now set as the default of this property.)
You can configure your preferable IP address or host in this property.

Scope: System

Added in version: 3.21.1 (21 R1)


### `TomcatService.cookieProcessor.sameSite`

Default value: lax
Tomcat uses the SameSite cookie attribute: lax by default.

You can also set the other options below.

Default value: lax
Possible Values:
unset - Do not set the SameSite cookie attribute.

none - Cookie is always sent in cross-site requests.

lax - Cookie is only sent on same-site requests and cross-site, top-level navigation GET requests.

strict - Prevents the cookie from being sent by the browser in all cross-site requests.

Scope: System

Added in version: 3.21.1 (21 R1)


### `TomcatService.port`

Default value: 8889
Value is a positive integer that specifies the Tomcat port for the connector. See https://tomcat.apache.org/tomcat-8.5doc/config/http.html
The default value is 8889 and it is used as the AJP connector. If there is a need to use a different port, as in the case of an HTTP
connector, the value can be set to 80 after which Polarion will be directly accessible by Tomcat on http.

Scope: System

Added in version: 3.18.2 (18.2)


### `TomcatService.protocol`

Default value: AJP
Value is a string that specifies the Tomcat protocol for the connector. See https://tomcat.apache.org/tomcat-8.5doc/config/http.html
The default value is AJP. The AJP connector can be plugged to Apache or it can be HTTP and Tomcat will expose Polarion directly on
the http protocol.

Scope: System

Added in version: 3.18.2 (18.2)


### `TomcatService.request.safeListedHosts`

Default value: localhost, polarionBaseUrl hostname, cluster node host name
Add this property to the polarion.properties file to list the client request host header hostnames that Polarion is allowed to
respond to. (On top of the defaults.)
Security Risk Mitigation: Client requests that contain unexpected hostnames or IP addresses in the request Host header may indicate
a "Man-in-the-middle" host header injection attack that can send Polarion's response to an untrusted site.

If a client request contains a hostname or IP address that is NOT in the list, Polarion returns an HTTP 400 status code and logs a
WARN in the main Polarion log.

If a hostname or IP reported in the Polarion log is a legitimate, alternative hostname of your Polarion service, then add it to this
property.


If the reported hostname is unknown, consult your local security officer or network administrator to understand where the request
is coming from and determine if it's a potential security incident.

The default list includes localhost and the hostnames (or host addresses) specified in the following properties:
1. `base.url`
2. `com.siemens.polarion.cluster.nodeHostname`
Example 1:
If `TomcatService.request.safeListedHosts` is not added to the polarion.properties file or is empty,
base.url=http://mylpolarionhost/, and com.siemens.polarion.cluster.nodeHostname=node1,
then the list is: localhost,mylpolarionhost,node1
Example 2:
If TomcatService.request.safeListedHosts= hostname1,hostname2, the base.url=http://mypolarionhost/ and
com.siemens.polarion.cluster.nodeHostname=node1,
then the list is: localhost, mypolarionhost,node1,hostname1,hostname2
Scope: System

Added in version: 3.22.2 (22 R2)

useDecimalHoursDurationFormat
Default value: false
Controls whether or not the value for hours in time reporting fields (Initial Estimate, Time Spent, and so on) must be entered as a
decimal value rather than the default fractional.

When set to true, hour durations in all of the time reporting fields are displayed and entered as decimal hours only, for example 22.33.

The examples displayed by clicking the "?" next to time input fields are changed when this feature is enabled, and the export option
Convert Durations to decimal hours is not displayed in the export dialog.

Storage in XML persistence and pre-2011 LiveDocs is still in the fractional format; only hours are not converted to days. So the value in
the example above is actually stored as 22 1/3h. It is stored that way rather than 22 33/100h because of the smart parsing of userentered values to the fractional format, which recognizes the decimal representation of fractions (y/3, y/6, and y/12). So, for example,
entering 0.08 or 0.083 is parsed as 1/12h.

Note: You can disable smart parsing by setting the following property to true.

dontUseSmartDecimalHoursDurationFormatParsing
Scope: System

Added in version: 3.2.3

wikiProtocolSchema
Default value: N/A
Value is a string that can contain a protocol designation to overwrites the http server protocol in the wiki component. Use it for problems
with reverse proxy, etc. By default schema is taken from the server URL. Example of possible value: https
Scope: System

Added in version: 3.4.3


### `wordImport.ignore.CLASS`

Default value: false
Controls whether run content of a given type is reported using the "sorry bear" image during import from Microsoft Word. The CLASS is
the short name of the class of the object from the docx4j library, e.g. R.DayLong. By default some not-imported content of the run is
replaced by a "sorry bear" image. If this is inconvenient in some cases, you can look at the tool tip of the "sorry bear" image to find the
class name in the case. For example: Unsupported content: R.DayLong. You can then add the
property wordImport.ignore.R.DayLong=true to the polarion.properties file. Value is Boolean (true or false).

Scope: System

Added in version: 3.5.1 (2011 SR1)


## 3. Runtime properties

These properties have several special attributes:
They can affect the system either globally, or only specific projects.

Administrators set, view, and modify them in the Administration user interface in Polarion.

Server restart is not required. Changes take effect immediately after saving.



### `authentication.xmlReload.enabled`

Default value: false
A runtime property (set in Administration >Configuration Properties) that's only available at the global administration level.

Value: Boolean (true or false)
If set to "true" you can reload the authentication.xml configuration file after editing it directly on the file system.

(For administrators without access to Polarion itself.)
Useful if, for example, you want to update the bind password or change the SAML certificates.

If set to "false" the call will be rejected.

Note: This reload feature should not be used to create or remove the initial authentication.xml file. It should only be used to refresh the
configuration on the fly without restarting the Polarion service. (After editing the existing authentication.xml file on the file-system level.)
For cluster installations, .../authentication-reload can be called from the cluster's (or any node's) URL.

The endpoint returns a JSON formatted response.


Scope: Runtime

Added in version: 3.21.2 (21 R2)


### `collections.showOutOfCollectionLinks`

Default value: false
Controls whether or not to show Work Item links and backlinks in the Collection context, even when they point to/from Work Items
outside of the Collection. When set to true, links and backlinks are shown. When set to false, they are hidden.

Scope: Runtime

Added in version: 3.20.1 (20 R1)


### `documents.create.japanese.kanji.transliteration`

Default value: false
The same ideogram can be transliterated differently in different languages. Chinese is set by default, but this property lets you switch
the transliteration to Japanese romanization.

Transliterated values in Polarion are used for auto-filling fields that require ASCII symbols in the Document, Page, and Plan creation
dialog boxes.

When set to true: transliterates ideograms to Romaji (Japanese romanization).

When set to false: Chinese transliteration is used for ideograms.

Scope: Runtime

Added in version: 3.21.2 (21 R2)


### `documents.skipPermissionCheckForNavigationTree`

Default value: false

When enabled, all users can see the titles of all Documents in the Navigation tree, regardless of their current user permissions. Users
must still have the requisite permissions in order to open Documents, and view or modify their content. Navigation tree loading is faster,
but because the titles of all Documents in a project will be exposed in Navigation to all users, consider carefully, and consult with project
leaders before enabling this property. The configuration is per project.

Scope: Runtime

Added in version: 3.20.1 (20 R1)


### `documents.workItemPicker.defaultSearchScope`

Default value: project
This runtime configuration property defines the search scope for the Work Item picker for Polaron Documents.

When a user tries to add Work Items from the Work Item Picker to a Document, this property adds a predefined search scope.

Currently supported values: document, project, repository.

If set to document: "in Document" is selected as the search scope when a user opens the Work Item Picker.

If set to project: "In Project" is selected as the search scope when a user opens the Work Item Picker.

If set to repository: "In Repository" is selected as the search scope when a user opens the Work Item Picker.

Scope: Runtime

Added in version: 3.22.2 (22 R2)


### `quickCreate.buttonName`

Default value: ""
A custom name for the Navigation Header button. When clicked, it opens a dialog with the content defined in the `quickCreate.templatePath` p
The button label is CREATE... if this property is not defined. We recommend using short (1-3 word) descriptive values.

It applies to the current project context.

It uses the global button name if nothing is defined in the project context.

Example: quickCreate.buttonName=CREATE...

Scope: Runtime

Added in version: 3.22.2 (22 R2)


### `quickCreate.buttonTooltip`

Default value: ""
A custom tooltip for the Navigation Header button.

It appears when users hover over the button.

The tooltip is "Quick Create - Create new objects of any type from anywhere." if this property is not defined.

It applies to the current project context.

It uses the global button tooltip if nothing is defined in the project context.

Example: quickCreate.buttonTooltip=Quick Create - Create new objects of any type from anywhere.

Scope: Runtime

Added in version: 3.22.2 (22 R2)


### `quickCreate.dialogTitle`

Default value: ""
A custom title for the dialog with content defined in the `quickCreate.templatePath` property.

The title is Create New... if this property is not defined. We recommend using short (1-3 word) descriptive values.

It applies to the current project context.

It uses the global title if nothing is defined in the project context.

Example: quickCreate.dialogTitle=Create New...

Scope: Runtime

Added in version: 3.22.2 (22 R2)


### `quickCreate.templatePath`

Default value: ""
The relative path to the LiveReport that defines what options appear when users click CREATE... in the Navigation Header.

(Create Work Items, LiveDocs, Plans, and so on.)
It applies to the current project context.

It uses the global path name if nothing is defined in the project context.

Project-level example: quickCreate.templatePath=spaceID/richpageID (Takes the configuration from the current
project.)
You can specify a projectID (quickCreate.templatePath=projectID/spaceID/richpageID) to use a
configuration from another project.

(You can even use projectID for your current project, but it is not required because the relative path is enough.)
Global-level example: quickCreate.templatePath=/spaceID/richpageID (The / at the beginning indicates the global
level.)
(For the Global level, you can also use a relative path, but if you want to reference the Global level from a project you must use
/spaceID/pageID.)
Revert to default: Use quickCreate.templatePath=default to revert to the default Quick Create configuration.

Hide the Create... button: Use quickCreate.templatePath= (with no value) to hide the Create... button in the
Navigation Header.

If the property is added but no value is entered, then the CREATE... button is hidden.

If you do not add this property, it behaves like you entered a default value. (It reverts to the default Quick Create configuration.)

Scope: Runtime

Added in version: 3.22.2 (22 R2)


### `scriptInjection.loginBody`

Default value: null
This property allows you to inject custom HTML or JavaScript snippets into the <body> tag of Polarion's login page.

This functionality can be used to customize Polarion UI, add analytics on top of Polarion, or integrate an onboarding solution into
Polarion.

Type: String
Default value: null
Example: `<script type="text/javascript">window.alert("example")</script>`

Added to the Polarion Global Administration -> Configuration Properties section within Polarion.

Note: You can only use it in the Configuration Properties section on the global level. (Project-level entries are ignored.)
Scope: Runtime

Added in version: 3.22.2 (22 R2)


### `scriptInjection.loginHead`

Default value: null
This property allows you to inject custom HTML or JavaScript snippets into the <head> tag of Polarion's login page.

This functionality can be used to customize Polarion UI, add analytics on top of Polarion, or integrate an onboarding solution into
Polarion.

Type: String
Default value: null
Example: `<script type="text/javascript">window.alert("example")</script>`

Added to the Polarion Global Administration -> Configuration Properties section within Polarion.

Note: You can only use it in the Configuration Properties section on the global level. (Project-level entries are ignored.)
Scope: Runtime

Added in version: 3.22.2 (22 R2)


### `scriptInjection.mainBody`


Default value: null
This property allows you to inject custom HTML or JavaScript snippets into the <body> tag of Polarion's main page.

This functionality can be used to customize the Polarion UI, add analytics on top of Polarion, or integrate an onboarding solution into
Polarion.

Type: String
Default value: null
Example: `<script type="text/javascript">window.alert("example")</script>`

Added to the Polarion Global Administration -> Configuration Properties section within Polarion.

Note: You can only use it in the Configuration Properties section on the global level. (Project-level entries are ignored.)
Scope: Runtime

Added in version: 3.22.2 (22 R2)


### `scriptInjection.mainHead`

Default value: null
This property allows you to inject custom HTML or JavaScript snippets into the <head> tag of Polarion's main page.

This functionality can be used to customize Polarion UI, add analytics on top of Polarion, or integrate an onboarding solution into
Polarion.

Type: String
Default value: null
Added to the Polarion Global Administration -> Configuration Properties section within Polarion.

Note: You can only use it in the Configuration Properties section on the global level. (Project-level entries are ignored.)
Scope: Runtime

Added in version: 3.22.2 (22 R2)


### `sychronizer.loadObjectEnumOptionsEnabled`

Default value: true
Controls loading of object enumeration options during synchronization via a Connector.

If set to true, all object enumerations are loaded within the synchronization UI, and also during actual synchronization.

If set to false, object enumerations are not loaded at all during synchronization, and object enumeration values cannot be mapped
anymore in the ReqIF import and export dialog boxes. This is done so as not to load custom object enumerations, which can number in
the thousands, and which could impact synchronization UI operation as well as synchronization performance.

Scope: Runtime

Added in version: 3.21.2 (21 R2)


### `synchronizer.plan.template.id`

Default value: iteration
Define a plan template ID to be used for creation of Polarion Plans during synchronization.

The Plan template ID can be found on the template's Properties page
Scope: Runtime

Added in version: 3.21.1 (21 R1)


### `synchronizer.reqif.ddcMode`

Default value: DDC_FULL_MODULE
This runtime configuration property controls the content of the <doors:DDC-MODE> (or <DDC-MODE>) XML tags in exported ReqIF
files.

When set to NO_DDC, the Polarion ReqIF file is editable in Doors.

When set to DDC_FULL_MODULE, the Polarion ReqIF file is not editable in Doors.

Default Value is DDC_FULL_MODULE.

Scope: Runtime

Added in version: 3.22.2 (22 R2)


### `synchronizer.rif.ddcMode`

Default value: DDC_FULL_MODULE
This runtime configuration property controls the content of the <doors:DDC-MODE> (or <DDC-MODE>) XML tags in exported RIF files.

When set to NO_DDC, the Polarion RIF file is editable in Doors.

When set to DDC_FULL_MODULE, the Polarion RIF file is not editable in Doors.

Default Value is DDC_FULL_MODULE.

Scope: Runtime

Added in version: 3.22.2 (22 R2)


### `testManagement.execution.recentRecordsLimit`

Default value: 10
Value is a positive integer (or zero). A positive number specifies the number of Test Records that are checked for the Recent button.

Value of zero (0) causes that button to be hidden. Applies to the current project context or globally as the default.

Scope: Runtime

Added in version: 3.18.1 (18.1)


### `testManagement.useOldExecutionView`

Default value: false
Enable this property to use the legacy execution extension with Test Cases instead of the revamped execution view introduced in
Polarion 18.

Can be applied on both the project and global levels.

In order for this property to work, a Polarion administrator must set the following system property first:

### `com.siemens.polarion.ui.testExecution.oldExecutionView.enabled`

Warning
This feature is no longer tested, is disabled by default.

Scope: Runtime

Added in version: 3.18.0 (18)


### `userManagement.myPolarionPageTemplate`

Default value: none
Defines the path to a custom template for My Polarion personal dashboard pages. The value is a string.

Global administrators can create this template, and manage it centrally. If the default My Polarion page does not fit your needs, use this
property to point to your custom default template Page that is aligned with your process.

Scope: Runtime

Added in version: 3.19.2 (19.2)


### `workitems.linkedWorkItemsLimit`

Default value: 100
Limits the number of linked Work Items displayed in the Work Item Editor and in the Work Item Properties sidebar. Zero (0) value means
no linked Work Items will be displayed.

Scope: Runtime

Added in version: 3.23.4 (2304 - current)


### `workitems.treeTable.removeDuplicateRoots`

Default value: true
Toggles whether to show or hide duplicate Work Items at the base level of Tree View search results, even if they are found in the nested
tree of another item.


When set to true (default):
Only the parent Work Items that match the filter criteria are displayed.

Child Work Items of the displayed Work Items that also match the search criteria are hidden by default but can be expanded
manually by a user.

When set to false:
All Work Items that match the filter criteria are listed on the base level of the tree results. Any parent and child relationships that
they have with each other are ignored.

All Work Items can be expanded to reveal their descendants.

NOTE: This may result in some Work Items appearing multiple times in the search results.

Scope: Runtime

Added in version: 3.19.1 (19.1)


### `workitems.workItemPicker.defaultSearchScope`

Default value: repository_all
This runtime configuration property controls the search scope for the Work Item Picker for standalone Work Items. (Work Items that are
not in Documents.)
If a user tries to add Work Items from the Work Item Picker to the Linked Work Item section of a Work Item, then the scope defined in
this property is added as a predefined search scope.

Currently supported values: project and repository.

If set to project: "In Project" is selected as the search scope when a user opens the Work Item Picker.

If set to repository: "In Repository" is selected as the search scope when a user opens the Work Item Picker.

Scope: Runtime

Added in version: 3.22.2 (22 R2)


## 4. New properties

The following new properties are introduced in this release. Search the document for the names to see descriptions and default values.


### `com.polarion.scripting.allowedSecurityServiceMethods`

### `com.polarion.scripting.job.allowedSecurityServiceMethods`

### `com.siemens.polarion.objectindexing.runtimeWorkers`

### `com.siemens.polarion.rest.defaultPageSize`

### `com.siemens.polarion.rest.maxIncludedSize`

### `com.siemens.polarion.rest.maxRelationshipSize`

### `com.siemens.polarion.rest.security.restApiToken.enabled`

### `com.siemens.polarion.rest.swaggerUi.persistAuthorization`

### `com.siemens.polarion.security.forbiddenFieldsInQuery`

### `com.siemens.polarion.security.permission.globalRolesWithQueryFieldRestriction`

### `com.siemens.polarion.security.personalAccessToken.maxDaysBeforeExpiry`

### `com.siemens.polarion.tc.sso.app.id`

### `com.siemens.polarion.tc.uri`

### `workitems.linkedWorkItemsLimit`

5. Removed properties
The following properties are removed in the current release. Properties are removed when changes in the software render them
unnecessary or obsolete. If you have added these properties to your polarion.properties file, or to the Configuration Properties
administration page (in the case of Runtime properties), you need not remove the line(s) after installing the update unless otherwise
instructed in the release notes. However, you may want to clean the file so that only active properties appear in your configuration.



### `com.polarion.scripting.useGraalJsEngine`

### `com.polarion.showWord2003Export`

### `com.siemens.polarion.tc.session.wait.time`


