---

copyright:
  years: 2021
lastupdated: "2021-04-20"

keywords: app configuration CLI, app configuration command line, app configuration terminal, app configuration shell

subcollection: app-configuration-cli-plugin

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}

# App Configuration CLI
{: #app-configuration-cli}

The {{site.data.keyword.cloud_notm}} command-line interface (CLI) provides extra capabilities for service offerings. {{site.data.keyword.cloud_notm}} CLI supports a plug-in framework to extend its capability. You can install the {{site.data.keyword.appconfig_short}} CLI plug-in from the {{site.data.keyword.cloud_notm}} plug-in repository. With the {{site.data.keyword.appconfig_short}} service CLI plugin, you can easily manage {{site.data.keyword.appconfig_short}} service instances by using the CLI commands available.
{:shortdesc}

To run {{site.data.keyword.cloud_notm}} {{site.data.keyword.appconfig_short}} commands, use `ibmcloud app-configuration` or `ibmcloud ac`.
{: tip}

## Prerequisites
{: #ac-prereqs}

* An {{site.data.keyword.cloud_notm}} account. If you do not have an account, click [here](https://cloud.ibm.com/) to create one.
* An instance of [{{site.data.keyword.cloud_notm}} {{site.data.keyword.appconfig_short}}](https://cloud.ibm.com/catalog/services/app-configuration) service.
* [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-getting-started).

## Installing {{site.data.keyword.appconfig_short}} CLI plug-in
{: #ac-install-cli}

Install the {{site.data.keyword.appconfig_short}} CLI plug-in by running the following command from the IBM plug-in repo `{{site.data.keyword.cloud_notm}}`:

```sh
ibmcloud plugin install app-configuration
```
{: pre}


You're notified on the command line when updates to the {{site.data.keyword.cloud_notm}} CLI and plug-ins are available. Be sure to keep your CLI up-to-date so that you can use the latest commands. You can view the current version of all installed plug-ins by running `ibmcloud plugin list`.
{: tip}

### Output
{: #ac-install-cli-output}

The command returns the following output:

```
Looking up 'app-configuration' from repository 'IBM Cloud'...
Plug-in 'app-configuration/0.0.1' found in repository 'IBM Cloud'
Attempting to download the binary file...
 14.9 MiB / 14.9 MiB [==============================================================================================================================================] 100.00% 14s
14900000 bytes downloaded
Installing binary...
OK
Plug-in 'app-configuration 0.0.1' was successfully installed into /Users/<username>/.bluemix/plugins/app-configuration. Use 'ibmcloud plugin show app-configuration' to show its details.
```
{: screen}

## ibmcloud ac init
{: #ac-ibmcloud-ac-init}

Before proceeding with initializing the CLI plug-in make sure that you have selected the correct API Endpoint, region & account in your ibmcloud CLI.
{: note}

Initialize the cli plug-in by using the following command:

```sh
ibmcloud ac init
```
{: pre}

### Example
{: #ac-ibmcloud-ac-init-example}

Log in to {{site.data.keyword.cloud_notm}} CLI and initialize the CLI to {{site.data.keyword.appconfig_short}} service instance `App Configuration Instance 1`.

```sh
ibmcloud ac init
```
{: pre}

### Output
{: #ac-ibmcloud-ac-init-output}

The command returns the following output:

```
Initializing IBM Cloud App Configuration Service plug-in...

Select a App Configuration instance:
1. App Configuration Instance 1
2. App Configuration Instance 2
Enter a number> 1
App Configuration instance selected is - 'App Configuration Instance 1'
```
{: screen}

## ibmcloud ac show
{: #ac-ibmcloud-ac-show}

To see the name of the instance that is currently being used, use this command.

```sh
ibmcloud ac show
```
{: pre}

### Example
{: #ac-ibmcloud-ac-show-example}

Prerequisite - Use the `ibmcloud ac init` command to select an instance first.
{: note}

```sh
ibmcloud ac show
```
{: pre}

### Output
{: #ac-ibmcloud-ac-show-output}

The command returns the following output:

```
App Configuration instance being used is - 'App Configuration Instance 1'
```
{: screen}

## ibmcloud ac collections
{: #ac-ibmcloud-ac-collections}

You can list all collections, by using the command:

```sh
ibmcloud ac collections [--size SIZE] [--offset OFFSET] [--features FEATURES] [--tags TAGS] [--expand EXPAND] [--include INCLUDE]
```
{: pre}

### Command options
{: #ac-ibmcloud-ac-collections-command-options}

<dl>
<dt>--size SIZE (optional)</dt>
<dd>Used for pagination. Size of the number of records retrieved</dd>
<dt>--offset OFFSET (optional)</dt>
<dd>Used for pagination. Offset used to retrieve records.</dd>
<dt>--features FEATURES (optional)</dt>
<dd>Filter based on the feature's shortname.</dd>
<dt>--tags TAGS (optional)</dt>
<dd>Filter based on the tags.</dd>
<dt>--expand EXPAND (optional)</dt>
<dd>Expanded view of the collection details.</dd>
<dt>--include INCLUDE (optional)</dt>
<dd>Include feature details in the response.</dd>
</dl>

### Example
{: #ac-ibmcloud-ac-collections-example}

To list all collections, run the following command:

```sh
ibmcloud ac collections
```
{: pre}

### Output
{: #ac-ibmcloud-ac-collections-output}

The command returns the following output:

```
name                 collection_id   
sample               sampleId   
GHz Inc              ghzinc1
```
{: screen}

## ibmcloud ac collection create
{: #ac-ibmcloud-ac-collection-create}

You can create a collection, by using the command:

```sh
ibmcloud ac collection create {--file FILE-PATH | --name NAME [--collection_id COLLECTION_ID] [--description DESCRIPTION] [--tags TAGS]}
```
{: pre}

### Command options
{: #ac-ibmcloud-ac-collection-create-command}

<dl>
<dt>--name NAME</dt>
<dd>Collection name. Required field - input either as a flag or from file.</dd>
<dt>--collection_id COLLECTION_ID (optional)</dt>
<dd>Collection Id. If this value is not provided, name will automatically become the Id. Optional field - input either as a flag or from file.</dd>
<dt>--description DESCRIPTION (optional)</dt>
<dd>Description of the collection. Optional field - input either as a flag or from file.</dd>
<dt>--tags TAGS (optional)</dt>
<dd>Tags associated with the collection. Optional field - input either as a flag or from file.</dd>
<dt>--file FILE</dt>
<dd>Input via file. File format Supported - JSON</dd>
</dl>

### Example
{: #ac-ibmcloud-ac-collection-create-example}

To create a collection with name `sample` using flags ([click here](#ac-fileinput) for using commands with '--file' flag), run the following command:

```sh
ibmcloud ac collection create --name sample --collection_id sampleId --description sampleDesc --tags sampleTag
```
{: pre}

### Output
{: #ac-ibmcloud-ac-collection-create-output}

The command returns the following output:

```
collection_id   sampleId   
description     sampleDesc   
created_time    2021-01-18T08:15:45Z   
updated_time    2021-01-18T08:15:45Z   
name            sample   
```
{: screen}

## ibmcloud ac collection get
{: #ac-ibmcloud-ac-collection-get}

You can get a collection, by using the command:

```sh
ibmcloud ac collection get --collection_id COLLECTION_ID
```
{: pre}

### Command options
{: #ac-ibmcloud-ac-collection-get-command}

<dl>
<dt>--collection_id COLLECTION_ID</dt>
<dd>Collection Id for the collection</dd>
</dl>

### Example
{: #ac-ibmcloud-ac-collection-get-example}

To get a collection with Id `sampleId`, run the following command:

```sh
ibmcloud ac collection get --collection_id sampleId
```
{: pre}

### Output
{: #ac-ibmcloud-ac-collection-get-output}

The command returns the following output:

```
name            sample   
collection_id   sampleId
```
{: screen}

## ibmcloud ac collection update
{: #ac-ibmcloud-ac-collection-update}

You can update a collection, by using the command:

```sh
ibmcloud ac collection update {--file FILE-PATH | --name NAME --collection_id COLLECTION_ID --description DESCRIPTION --tags TAGS}
```
{: pre}

### Command options
{: #ac-ibmcloud-ac-collection-update-command}

<dl>
<dt>--collection_id COLLECTION_ID</dt>
<dd>Collection Id. Required field - input either as a flag or from file.</dd>
<dt>--name NAME</dt>
<dd>Collection name. Required field - input either as a flag or from file.</dd>
<dt>--description DESCRIPTION</dt>
<dd>Description of the collection. Required field - input either as a flag or from file.</dd>
<dt>--tags TAGS (optional)</dt>File format Supported
<dd>Tags associated with the collection. Required field - input either as a flag or from file.</dd>
<dt>--file FILE</dt>
<dd>Input via file. File format Supported - JSON</dd>
</dl>

### Example
{: #ac-ibmcloud-ac-collection-update-example}

To update a collection with id `sampleId` using flags ([click here](#ac-fileinput) for using commands with '--file' flag), run the following command:

```sh
ibmcloud ac collection update --collection_id sampleId --name sample --description sampleDesc --tags sampleTag
```
{: pre}

### Output
{: #ac-ibmcloud-ac-collection-update-output}

The command returns the following output:

```
name            sample   
collection_id   sampleId   
description     sampleDescUpdated   
created_time    2021-01-18T08:15:45Z   
updated_time    2021-01-19T05:57:27Z
```
{: screen}

## ibmcloud ac collection delete
{: #ac-ibmcloud-ac-collection-delete}

You can delete a collection, by using the command:

```sh
ibmcloud ac collection delete --collection_id COLLECTION_ID
```
{: pre}

### Command options
{: #ac-ibmcloud-ac-collection-delete-command}

<dl>
<dt>--collection_id COLLECTION_ID</dt>
<dd>Collection Id</dd>
</dl>

### Example
{: #ac-ibmcloud-ac-collection-delete-example}

To delete a collection with id `sampleId` , run the following command:

```sh
ibmcloud ac collection delete --collection_id sampleId
```
{: pre}

### Output
{: #ac-ibmcloud-ac-collection-delete-output}

The command returns the following output:

```
OK
```
{: screen}

## ibmcloud ac features
{: #ac-ibmcloud-ac-features}

You can list all features, by using the command:

```sh
ibmcloud ac features [--size SIZE] [--offset OFFSET] [--tags TAGS] [--collections COLLECTIONS] [--segments SEGMENTS] [--expand EXPAND] [--include INCLUDE]
```
{: pre}

### Command options
{: #ac-ibmcloud-ac-features-command}

<dl>
<dt>--size SIZE (optional)</dt>
<dd>Used for pagination. Size of the number of records retrieved</dd>
<dt>--include INCLUDE (optional)</dt>
<dd>Feature details to include the associated collections or rules details in the response.</dd>
<dt>--offset OFFSET (optional)</dt>
<dd>Used for pagination. Offset used to retrieve records.</dd>
<dt>--collections COLLECTIONS (optional)</dt>
<dd>Filter features by a list of comma separated collections.</dd>
<dt>--segments SEGMENTS (optional)</dt>
<dd>Filter features by a list of comma separated segments</dd>
<dt>--expand EXPAND (optional)</dt>
<dd>Expanded view the feature details.</dd>
<dt>--tags TAGS (optional)</dt>
<dd>Filter features by a list of comma separated tags.</dd>
</dl>

### Example
{: #ac-ibmcloud-ac-features-example}

To list all features, run the following command:

```sh
ibmcloud ac features
```
{: pre}

### Output
{: #ac-ibmcloud-ac-features-output}

The command returns the following output:

```
name            feature_id      segment_exists   
Indian IBMers   ibm-discount    true   
sampleFeature   sampleFeature   true   
Cycle Rentals   cycle-rentals   true
```
{: screen}

## ibmcloud ac feature create
{: #ac-ibmcloud-ac-feature-create}

You can create a feature, by using the command:

```sh
ibmcloud ac feature create {--file FILE-PATH | --name NAME [--feature_id FEATURE_ID] --description DESCRIPTION --type TYPE --enabled_value ENABLED_VALUE --disabled_value DISABLED_VALUE --tags TAGS --segment_rules SEGMENT_RULES --collections COLLECTIONS}
```
{: pre}

### Command options
{: #ac-ibmcloud-ac-feature-create-command}

<dl>
<dt>--name NAME</dt>
<dd> Feature name. Required field - input either as a flag or from file.</dd>
<dt>--feature_id FEATURE_ID (optional)</dt>
<dd>Feature Id. If this value is not provided, name will automatically become the Id. Optional field - input either as a flag or from file.</dd>
<dt>--description DESCRIPTION</dt>
<dd>Description of the feature. Required field - input either as a flag or from file.</dd>
<dt>--type TYPE</dt>
<dd>Type of the feature (Boolean, String, Number). Required field - input either as a flag or from file.</dd>
<dt>--enabled_value ENABLED_VALUE</dt>
<dd>Value of the feature when it is enabled. Required field - input either as a flag or from file.</dd>
<dt>--disabled_value DISABLED_VALUE </dt>
<dd>Value of the feature when it is disabled. Required field - input either as a flag or from file.</dd>
<dt>--tags TAGS</dt>
<dd>Tags associated with the feature. Required field - input either as a flag or from file.</dd>
<dt>--file FILE</dt>
<dd>Input via file. File format Supported - JSON</dd>
</dl>

### Example
{: #ac-ibmcloud-ac-feature-create-example}

To create a collection with name `sample` using flags ([click here](#ac-fileinput) for using commands with '--file' flag), run the following command:

```sh
ibmcloud ac feature create --name "IBMers" --feature_id "ibm-discount" --description "Discount given to IBM employees" --type "BOOLEAN" --enabled_value true --disabled_value false --segment_rules '[{"rules":[{"segments":["ibm_employees"]}],"value": true,"order": 1}]' --collections '[{"collection_id":"corporatediscount","enabled": true}]'  --tags "discount,sale"
```
{: pre}

### Output
{: #ac-ibmcloud-ac-feature-create-output}

The command returns the following output:

```
type             BOOLEAN   
enabled_value    true   
segment_rules    <Array>   
collections      <Array>   
name             IBMers   
feature_id       ibm-discount   
description      Discount given to IBM employees   
disabled_value   false   
created_time     2021-02-02T17:52:46Z   
updated_time     2021-02-02T17:52:46Z
```
{: screen}

## ibmcloud ac feature get
{: #ac-ibmcloud-ac-feature-get}

You can get a feature, by using the command:

```sh
ibmcloud ac feature get --feature_id FEATURE_ID [--include INCLUDE]
```
{: pre}

### Command options
{: #ac-ibmcloud-ac-feature-get-command}

<dl>
<dt>--feature_id FEATURE_ID</dt>
<dd>Feature Id for the feature flag.</dd>
<dt>--include INCLUDE (optional)</dt>
<dd>Feature details to include the associated collections details in the response.</dd>
</dl>

### Example
{: #ac-ibmcloud-ac-feature-get-example}

To get a feature with Id `ibm-discount`, run the following command:

```sh
ibmcloud ac feature get --feature_id ibm-discount
```
{: pre}

### Output
{: #ac-ibmcloud-ac-feature-get-output}

The command returns the following output:

```
name    type     disabled_value  updated_time          feature_id    description                      enabled_value  created_time          order  rules    value   
IBMers  BOOLEAN  false           2021-02-02T17:52:46Z  ibm-discount  Discount given to IBM employees  true           2021-02-02T17:52:46Z  1      <Array>  true
```
{: screen}

## ibmcloud ac feature update
{: #ac-ibmcloud-ac-feature-update}

You can update a feature, by using the command:

```sh
ibmcloud ac feature update {--file FILE-PATH | --name NAME --feature_id FEATURE_ID --description DESCRIPTION --type TYPE --enabled_value ENABLED_VALUE --disabled_value DISABLED_VALUE --tags TAGS --segment_rules SEGMENT_RULES --collections COLLECTIONS}
```
{: pre}

### Command options
{: #ac-ibmcloud-ac-feature-update-command}

<dl>
<dt>--name NAME</dt>
<dd> Feature name. Required field - input either as a flag or from file.</dd>
<dt>--feature_id FEATURE_ID</dt>
<dd>Feature Id. Required field - input either as a flag or from file.</dd>
<dt>--description DESCRIPTION</dt>
<dd>Description of the feature. Required field - input either as a flag or from file.</dd>
<dt>--type TYPE</dt>
<dd>Type of the feature (Boolean, String, Number). Required field - input either as a flag or from file.</dd>
<dt>--enabled_value ENABLED_VALUE</dt>
<dd>Value of the feature when it is enabled. Required field - input either as a flag or from file.</dd>
<dt>--disabled_value DISABLED_VALUE </dt>
<dd>Value of the feature when it is disabled. Required field - input either as a flag or from file.</dd>
<dt>--tags TAGS</dt>
<dd>Tags associated with the feature. Required field - input either as a flag or from file.</dd>
<dt>--file FILE</dt>
<dd>Input via file. File format Supported - JSON</dd>
</dl>

### Example
{: #ac-ibmcloud-ac-feature-update-example}

To update description a feature with id `ibm-discount` using flags ([click here](#ac-fileinput) for using commands with '--file' flag), run the following command:

```sh
ibmcloud ac feature update --name "Indian IBMers" --feature_id "ibm-discount" --description "Discount given to IBM Indian employees" --type "BOOLEAN" --enabled_value true --disabled_value false --segment_rules '[{"rules":[{"segments":["ibm_employees"]}],"value": true,"order": 1}]' --collections '[{"collection_id":"corporatediscount","enabled": true}]'  --tags "discount,sale"
```
{: pre}

### Output
{: #ac-ibmcloud-ac-feature-update-output}

The command returns the following output:

```
updated_time     2021-02-02T18:06:03Z   
description      Discount given to IBM Indian employees   
enabled_value    true   
disabled_value   false   
segment_rules    <Array>   
created_time     2021-02-02T17:52:46Z   
name             Indian IBMers   
type             BOOLEAN   
collections      <Array>   
```
{: screen}

## ibmcloud ac feature delete
{: #ac-ibmcloud-ac-feature-delete}

You can delete a feature, by using the command:

```sh
ibmcloud ac feature delete --feature_id FEATURE_ID
```
{: pre}

### Command options
{: #ac-ibmcloud-ac-feature-delete-command}

<dl>
<dt>--feature_id FEATURE_ID</dt>
<dd>Feature Id</dd>
</dl>

### Example
{: #ac-ibmcloud-ac-feature-delete-example}

To delete a feature with id `ibm-discount`, run the following command:

```sh
ibmcloud ac feature delete --feature_id ibm-discount
```
{: pre}

### Output
{: #ac-ibmcloud-ac-feature-delete-output}

The command returns the following output:

```
OK
```
{: screen}

## ibmcloud ac segments
{: #ac-ibmcloud-ac-segments}

You can list all segments, by using the command:

```sh
ibmcloud ac segments [--size SIZE] [--offset OFFSET] [--tags TAGS] [--features FEATURES] [--expand EXPAND] [--include INCLUDE]
```
{: pre}

### Command options
{: #ac-ibmcloud-ac-segments-command}

<dl>
<dt>--size SIZE (optional)</dt>
<dd>Used for pagination. Size of the number of records retrieved</dd>
<dt>--include INCLUDE (optional)</dt>
<dd>Segment details to include the associated rules in the response.</dd>
<dt>--offset OFFSET (optional)</dt>
<dd>Used for pagination. Offset used to retrieve records.</dd>
<dt>--features FEATURES (optional)</dt>
<dd>Instructs to include the feature details based on the segments association.</dd>
<dt>--expand EXPAND (optional)</dt>
<dd>Expanded view the segment details.</dd>
<dt>--tags TAGS (optional)</dt>
<dd>Filter segments by a list of comma separated tags.</dd>
</dl>

### Example
{: #ac-ibmcloud-ac-segments-example}

To list all segments, run the following command:

```sh
ibmcloud ac segments
```
{: pre}

### Output
{: #ac-ibmcloud-ac-segments-output}

The command returns the following output:

```
name            segment_id   
India IBMers    ibm_employees_01   
IBM Employees   ibm_employees
```
{: screen}

## ibmcloud ac segment create
{: #ac-ibmcloud-ac-segment-create}

You can create a segment, by using the command:

```sh
ibmcloud ac segment create {--file FILE-PATH | --name NAME [--segment_id SEGMENT_ID] --description DESCRIPTION --tags TAGS --rules RULES}
```
{: pre}

### Command options
{: #ac-ibmcloud-ac-segment-create-command}

<dl>
<dt>--name NAME</dt>
<dd>Segment name. Required field - input either as a flag or from file.</dd>
<dt>--segment_id SEGMENT_ID (optional)</dt>
<dd>Segment Id. If this value is not provided, name will automatically become the Id. Optional field - input either as a flag or from file.</dd>
<dt>--description DESCRIPTION</dt>
<dd>Description of the segment. Required field - input either as a flag or from file.</dd>
<dt>--rules RULES</dt>
<dd>Rule array. Required field - input either as a flag or from file.</dd>
<dt>--tags TAGS</dt>
<dd>Tags associated with the segment. Required field - input either as a flag or from file.</dd>
<dt>--file FILE</dt>
<dd>Input via file. File format Supported - JSON</dd>
</dl>

### Example
{: #ac-ibmcloud-ac-segment-create-example}

To create a collection with name `sample` using flags ([click here](#ac-fileinput) for using commands with '--file' flag), run the following command:

```sh
ibmcloud ac segment create --name "IBM Employees" --segment_id "ibm_employees" --description "IBM Employees Segment" --tags "ibm" --rules '[{"attribute_name": "email", "operator": "endsWith", "values": ["@ibm.com"]}]'
```
{: pre}

### Output
{: #ac-ibmcloud-ac-segment-create-output}

The command returns the following output:

```
name           IBM Employees   
segment_id     ibm_employees   
description    IBM Employees Segment
created_time   2021-02-02T19:04:22Z   
updated_time   2021-02-02T19:04:22Z
```
{: screen}

## ibmcloud ac segment get
{: #ac-ibmcloud-ac-segment-get}

You can get a segment, by using the command:

```sh
ibmcloud ac segment get --segment_id SEGMENT_ID [--include INCLUDE]
```
{: pre}

### Command options
{: #ac-ibmcloud-ac-segment-get-command}

<dl>
<dt>--segment_id SEGMENT_ID</dt>
<dd>Feature Id for the feature flag.</dd>
<dt>--include INCLUDE (optional)</dt>
<dd>Instructs to include the feature details based on the segments association.</dd>
</dl>

### Example
{: #ac-ibmcloud-ac-segment-get-example}

To get a segment with Id `ibm_employees`, run the following command:

```sh
ibmcloud ac segment get --segment_id ibm_employees
```
{: pre}

### Output
{: #ac-ibmcloud-ac-segment-get-output}

The command returns the following output:

```
segment_id     description    features  created_time          updated_time          name           attribute_name  operator  values   
ibm_employees  IBM Employees  -         2021-02-02T19:04:22Z  2021-02-02T19:04:22Z  IBM Employees  email           endsWith  <Array>
```
{: screen}

## ibmcloud ac segment update
{: #ac-ibmcloud-ac-segment-update}

You can update a segment, by using the command:

```sh
ibmcloud ac segment update {--file FILE-PATH | --name NAME --segment_id SEGMENT_ID --description DESCRIPTION --tags TAGS --rules RULES}
```
{: pre}

### Command options
{: #ac-ibmcloud-ac-segment-update-command}

<dl>
<dt>--name NAME</dt>
<dd>Segment name. Required field - input either as a flag or from file.</dd>
<dt>--segment_id SEGMENT_ID</dt>
<dd>Segment Id. Required field - input either as a flag or from file.</dd>
<dt>--description DESCRIPTION</dt>
<dd>Description of the segment. Required field - input either as a flag or from file.</dd>
<dt>--rules RULES</dt>
<dd>Rule array. Required field - input either as a flag or from file.</dd>
<dt>--tags TAGS</dt>
<dd>Tags associated with the segment. Required field - input either as a flag or from file.</dd>
<dt>--file FILE</dt>
<dd>Input via file. File format Supported - JSON</dd>
</dl>

### Example
{: #ac-ibmcloud-ac-segment-update-example}

To update description a segment with id `ibm_employees` using flags ([click here](#ac-fileinput) for using commands with '--file' flag), run the following command:

```sh
ibmcloud ac segment update --name "IBM India Employees" --segment_id "ibm_employees" --description "IBM India Employees" --tags "ibm" --rules '[{"attribute_name": "email", "operator": "endsWith", "values": ["@in.ibm.com"]}]'
```
{: pre}

### Output
{: #ac-ibmcloud-ac-segment-update-output}

The command returns the following output:

```
description    IBM India Employees   
created_time   2021-02-02T19:04:22Z   
updated_time   2021-02-02T19:10:01Z   
name           IBM India Employees   
segment_id     ibm_employees  
```
{: screen}

## ibmcloud ac segment delete
{: #ac-ibmcloud-ac-segment-delete}

You can delete a segment, by using the command:

```sh
ibmcloud ac segment delete --segment_id SEGMENT_ID
```
{: pre}

### Command options
{: #ac-ibmcloud-ac-segment-delete-command}

<dl>
<dt>--segment_id SEGMENT_ID</dt>
<dd>Segment Id</dd>
</dl>

### Example
{: #ac-ibmcloud-ac-segment-delete-example}

To delete a segment with id `ibm_employees`, run the following command:

```sh
ibmcloud ac segment delete --segment_id ibm_employees
```
{: pre}

### Output
{: #ac-ibmcloud-ac-segment-delete-output}

The command returns the following output:

```
OK
```
{: screen}

## Creating or Updating item from file
{: #ac-fileinput}

The plug-in provides you the functionality of creating or updating items in JSON format stored in a file.

Following is how you can create collection from a file.

```sh
ibmcloud ac collection create {--file FILE-PATH | --name NAME [--collection_id COLLECTION_ID] [--description DESCRIPTION] [--tags TAGS]}
```
{: pre}

Notice the '|' symbol. This indicates that there are two ways to use the command.

```
ibmcloud ac collection create --file FILE-PATH
OR
ibmcloud ac collection create --name NAME [--collection_id COLLECTION_ID] [--description DESCRIPTION] [--tags TAGS]
```
{: codeblock}

To view the supported JSON format visit the [API Docs](https://cloud.ibm.com/apidocs/app-configuration).

Use the file flag (cannot be combined with any other flag) to give the path of the file.

### Example
{: #ac-fileinput-example}

To create a collection with id `corporateDiscount` stored in a file *create_collection_body.json*, run the following command:

```sh
ibmcloud ac collection create --file create_collection_body.json
```
{: pre}

Here is the content of 'create_collection_body.json':

```
{
    "name": "Corporate Discount",
    "collection_id": "corporateDiscount",
    "description": "Discount for partner Organizations",
    "tags": "discount,sale"
}
```
{: codeblock}

### Output
{: #ac-fileinput-output}

The command returns the following output:

```
name            Corporate Discount
collection_id   corporateDiscount   
description     Discount for partner Organizations   
created_time    2021-02-02T19:17:07Z   
updated_time    2021-02-02T19:17:07Z  
```
{: screen}

The behaviour for create and update of collection or feature or segment is similar as above. For accepted JSON format structure, visit the [API Docs](https://cloud.ibm.com/apidocs/app-configuration)

## ibmcloud plug-in uninstall
{: #ac-ibmcloud-plugin-uninstall}

Use this command to uninstall the App Configuration CLI plug-in.

```sh
ibmcloud plugin uninstall app-configuration
```
{: pre}

Uninstall returns a success message, if no errors.
