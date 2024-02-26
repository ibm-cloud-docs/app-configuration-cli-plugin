---

copyright:
  years: 2021, 2024
lastupdated: "2024-02-26"

keywords: App Configuration CLI, App Configuration command line, App Configuration terminal, App Configuration shell

subcollection: app-configuration

---

{{site.data.keyword.attribute-definition-list}}

# App Configuration CLI
{: #app-configuration-cli}

With the {{site.data.keyword.appconfig_short}} service CLI plug-in, you can easily manage {{site.data.keyword.appconfig_short}} service instances by using the CLI commands.
{: shortdesc}

Current version: **`2.0.0`**

## Prerequisites
{: #ac-prereqs}

* An {{site.data.keyword.cloud_notm}} account. If you do not have an account, click [here](https://cloud.ibm.com/) to create one.
* An instance of [{{site.data.keyword.cloud_notm}} {{site.data.keyword.appconfig_short}}](https://cloud.ibm.com/catalog/services/app-configuration) service.
* [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-getting-started).
* Optionally, if you want to use private endpoint support that is provided by the {{site.data.keyword.cloud_notm}} platform, make sure you [enable VRF and service endpoints](https://cloud.ibm.com/docs/account?topic=account-vrf-service-endpoint&interface=ui).

## Installing {{site.data.keyword.appconfig_short}} CLI plug-in
{: #ac-install-cli}

Install the {{site.data.keyword.appconfig_short}} CLI plug-in by running the following command from the IBM plug-in repo `{{site.data.keyword.cloud_notm}}`:

```sh
ibmcloud plugin install app-configuration
```
{: pre}

You're notified on the command-line when updates to the {{site.data.keyword.cloud_notm}} CLI and plug-ins are available. Be sure to keep your CLI up-to-date so that you can use the new commands. You can view the current version of all installed plug-ins by running `ibmcloud plugin list`.
{: tip}

To run {{site.data.keyword.cloud_notm}} {{site.data.keyword.appconfig_short}} commands, use `ibmcloud app-configuration` or `ibmcloud ac`.
{: tip}

### Output
{: #ac-install-cli-output}

The command returns the following output:

```sh
Looking up 'app-configuration' from repository 'IBM Cloud'...
Plug-in 'app-configuration' found in repository 'IBM Cloud'
Attempting to download the binary file...
[==============================================================================================================================================] 100.00%
Installing binary...
OK
Plug-in 'app-configuration' was successfully installed into /Users/<username>/.bluemix/plugins/app-configuration. Use 'ibmcloud plugin show app-configuration' to show its details.
```
{: screen}

## Set service URL
{: #ac-set-service-url}

To target the {{site.data.keyword.appconfig_short}} instance, use one of the following options.

* Run the `ibmcloud app-configuration config set` command.

    ```sh
     ibmcloud app-configuration config set service-url https://{region}.apprapp.cloud.ibm.com/apprapp/feature/v1/instances/{instance_ID}
    ```
    {: pre}


* Export an environment variable with your {{site.data.keyword.appconfig_short}} service endpoint URL.

    ```sh
    export APP_CONFIGURATION_URL=https://{region}.apprapp.cloud.ibm.com/apprapp/feature/v1/instances/{instance_ID}
    ```
    {: pre}

* Set the service endpoint in the command.

    ```sh
    ibmcloud app-configuration environments --service-url https://{region}.apprapp.cloud.ibm.com/apprapp/feature/v1/instances/{instance_ID}
    ```
    {: pre}

Replace `{region}` and `{instance_ID}` with the values that apply to your {{site.data.keyword.appconfig_short}} service instance. To find the endpoint URL see [Endpoint URLs](/apidocs/app-configuration#endpoint-url).





<!-- Below content should be pasted from the generated CLI markdown -->
<!-- This file: https://github.ibm.com/devx-app-services/appconfiguration-cli/tree/development/plugin/commands/appconfigurationv1/app-configuration-cli.md -->

## Globals
{: #app-configuration-globals}

### Commands
{: #app-configuration-commands}

#### `ibmcloud app-configuration docs`
{: #app-configuration-cli-docs-command}

Opens the plugin documentation in the web browser.

```sh
ibmcloud app-configuration docs
```

##### Example
{: #app-configuration-docs-examples}

```sh
ibmcloud app-configuration docs
```
{: pre}

### Options
{: #app-configuration-global-options}

`--region` (string)
:   The region where you provisioned your App Configuration instance. Available values: us-south, eu-gb, au-syd, us-east.

`--guid` (string)
:   App Configuration service instance ID.

`--output` (string)
:   Choose an output format - can be 'json', 'yaml', or 'table'. Defaults to 'table'.

`-j`, `--jmes-query` (string)
:   Provide a JMESPath query to customize output.

`--service-url` (string)
:   Provide the base endpoint URL for the API.

`-q`, `--quiet`
:   Suppresses verbose messages.

`-v`, `--version`
:   Prints the plugin version.

#### Example
{: #app-configuration-global-options-example}

```sh
ibmcloud app-configuration
    --region=us-south \
    --guid=provide-here-your-appconfig-instance-uuid \
    --output=json \
    --jmes-query="[:10]" \
    --service-url="https://myservice.test.cloud.ibm.com"
    --quiet
```
Note: This example only demonstrates the global options available to all sub-commands and is not a valid command itself.

### `ibmcloud app-configuration config`
{: #app-configuration-cli-config-command}

Global parameters can also be stored in persistent configuration so that they do not need to be manually specified each time the plugin is invoked. Each parameter can be configured with the `config` command and its subcommands.

```sh
ibmcloud app-configuration config
```

### `ibmcloud app-configuration config set`
{: #app-configuration-cli-config-set-command}

Set a new config value for a specific option. Each subcommand of the `set` command maps to a global option. Each subcommand accepts a single argument, the string representation of the value to store for the option.

```sh
ibmcloud app-configuration config set <option> <value>
```

#### Examples
{: #app-configuration-config-set-command-examples}

```sh
ibmcloud app-configuration config set service-url \
    'https://ibm.cloud.com/my-api'
```

### `ibmcloud app-configuration config get`
{: #app-configuration-cli-config-get-command}

Print out the currently set value for a specific option. Each subcommand of the `get` command maps to a global option.

```sh
ibmcloud app-configuration config get <option>
```

#### Examples
{: #app-configuration-config-get-command-examples}

```sh
ibmcloud app-configuration config get service-url
```

### `ibmcloud app-configuration config unset`
{: #app-configuration-cli-config-unset-command}

Unset the currently set value for a specific option. Each subcommand of the `unset` command maps to a global option.

The subcommands available for this service are: `service-url`, .

```sh
ibmcloud app-configuration config unset <option>
```

#### Examples
{: #app-configuration-config-unset-command-examples}

```sh
ibmcloud app-configuration config unset service-url
```

### `ibmcloud app-configuration config list`
{: #app-configuration-cli-config-list-command}

List out all of the currently set config values.

```sh
ibmcloud app-configuration config list
```

#### Examples
{: #app-configuration-config-list-command-examples}

```sh
ibmcloud app-configuration config list
```

## Environments
{: #app-configuration-environments-cli}

Environments represent your application environments.

### `ibmcloud app-configuration environments`
{: #app-configuration-cli-environments-command}

List all the environments in the App Configuration service instance.
Note: If the `--all-pages` option is not set, the command will only retrieve a single page of the collection.

```sh
ibmcloud app-configuration environments [--expand EXPAND] [--sort SORT] [--tags TAGS] [--include INCLUDE] [--limit LIMIT] [--offset OFFSET] [--search SEARCH]
```


#### Command options
{: #app-configuration-environments-cli-options}

`--expand` (bool)
:   If set to `true`, returns expanded view of the resource details.

`--sort` (string)
:   Sort the environment details based on the specified attribute. By default, items are sorted by name.

    Allowable values are: `created_time`, `updated_time`, `id`, `name`.

`--tags` (string)
:   Filter the resources to be returned based on the associated tags. Specify the parameter as a list of comma separated tags. Returns resources associated with any of the specified tags.

`--include` ([]string)
:   Include feature, property, snapshots details in the response.

    Allowable list items are: `features`, `properties`, `snapshots`.

`--limit` (int64)
:   The number of records to retrieve. By default, the list operation return the first 10 records. To retrieve different set of records, use `limit` with `offset` to page through the available records.

    The default value is `10`. The maximum value is `100`. The minimum value is `1`.

`--offset` (int64)
:   The number of records to skip. By specifying `offset`, you retrieve a subset of items that starts with the `offset` value. Use `offset` with `limit` to page through the available records.

    The default value is `0`. The minimum value is `0`.

`--search` (string)
:   Searches for the provided keyword and returns the appropriate row with that value. Here the search happens on the '[Name OR Tag]' of the entity.

`--all-pages` (bool)
:   Invoke multiple requests to display all pages of the collection for environments.

#### Example
{: #app-configuration-environments-examples}

```sh
ibmcloud app-configuration environments \
    --expand true \
    --sort created_time \
    --tags 'version 1.1,pre-release' \
    --include features,properties,snapshots \
    --limit 10 \
    --offset 0 \
    --search 'test tag'
```
{: pre}

### `ibmcloud app-configuration environment-create`
{: #app-configuration-cli-environment-create-command}

Create an environment.

```sh
ibmcloud app-configuration environment-create --name NAME --environment-id ENVIRONMENT-ID [--description DESCRIPTION] [--tags TAGS] [--color-code COLOR-CODE]
```


#### Command options
{: #app-configuration-environment-create-cli-options}

`--name` (string)
:   Environment name. Allowed special characters are dot ( . ), hyphen( - ), underscore ( _ ) only. Required.

    The maximum length is `256` characters.

`--environment-id` (string)
:   Environment id. Allowed special characters are dot ( . ), hyphen( - ), underscore ( _ ) only. Required.

    The maximum length is `256` characters.

`--description` (string)
:   Environment description.

    The maximum length is `255` characters.

`--tags` (string)
:   Tags associated with the environment.

`--color-code` (string)
:   Color code to distinguish the environment. The Hex code for the color. For example `#FF0000` for `red`.

#### Example
{: #app-configuration-environment-create-examples}

```sh
ibmcloud app-configuration environment-create \
    --name 'Dev environment' \
    --environment-id dev-environment \
    --description 'Dev environment description' \
    --tags development \
    --color-code #FDD13A
```
{: pre}

### `ibmcloud app-configuration environment-update`
{: #app-configuration-cli-environment-update-command}

Update an environment.

```sh
ibmcloud app-configuration environment-update --environment-id ENVIRONMENT-ID [--name NAME] [--description DESCRIPTION] [--tags TAGS] [--color-code COLOR-CODE]
```


#### Command options
{: #app-configuration-environment-update-cli-options}

`--environment-id` (string)
:   Environment Id. Required.

`--name` (string)
:   Environment name. Allowed special characters are dot ( . ), hyphen( - ), underscore ( _ ) only.

    The maximum length is `256` characters.

`--description` (string)
:   Environment description.

    The maximum length is `255` characters.

`--tags` (string)
:   Tags associated with the environment.

`--color-code` (string)
:   Color code to distinguish the environment. The Hex code for the color. For example `#FF0000` for `red`.

#### Example
{: #app-configuration-environment-update-examples}

```sh
ibmcloud app-configuration environment-update \
    --environment-id environment_id \
    --name exampleString \
    --description exampleString \
    --tags exampleString \
    --color-code #FDD13A
```
{: pre}

### `ibmcloud app-configuration environment`
{: #app-configuration-cli-environment-command}

Retrieve the details of the environment.

```sh
ibmcloud app-configuration environment --environment-id ENVIRONMENT-ID [--expand EXPAND] [--include INCLUDE]
```


#### Command options
{: #app-configuration-environment-cli-options}

`--environment-id` (string)
:   Environment Id. Required.

`--expand` (bool)
:   If set to `true`, returns expanded view of the resource details.

`--include` ([]string)
:   Include feature, property, snapshots details in the response.

    Allowable list items are: `features`, `properties`, `snapshots`.

#### Example
{: #app-configuration-environment-examples}

```sh
ibmcloud app-configuration environment \
    --environment-id environment_id \
    --expand true \
    --include features,properties,snapshots
```
{: pre}

### `ibmcloud app-configuration environment-delete`
{: #app-configuration-cli-environment-delete-command}

Delete an Environment.

```sh
ibmcloud app-configuration environment-delete --environment-id ENVIRONMENT-ID
```


#### Command options
{: #app-configuration-environment-delete-cli-options}

`--environment-id` (string)
:   Environment Id. Required.

#### Example
{: #app-configuration-environment-delete-examples}

```sh
ibmcloud app-configuration environment-delete \
    --environment-id environment_id
```
{: pre}

## Collections
{: #app-configuration-collections-cli}

Collections are a way to group feature flags and properties.

### `ibmcloud app-configuration collections`
{: #app-configuration-cli-collections-command}

List of all the collections in the App Configuration service instance.
Note: If the `--all-pages` option is not set, the command will only retrieve a single page of the collection.

```sh
ibmcloud app-configuration collections [--expand EXPAND] [--sort SORT] [--tags TAGS] [--features FEATURES] [--properties PROPERTIES] [--include INCLUDE] [--limit LIMIT] [--offset OFFSET] [--search SEARCH]
```


#### Command options
{: #app-configuration-collections-cli-options}

`--expand` (bool)
:   If set to `true`, returns expanded view of the resource details.

`--sort` (string)
:   Sort the collection details based on the specified attribute. By default, items are sorted by name.

    Allowable values are: `created_time`, `updated_time`, `id`, `name`.

`--tags` (string)
:   Filter the resources to be returned based on the associated tags. Specify the parameter as a list of comma separated tags. Returns resources associated with any of the specified tags.

`--features` ([]string)
:   Filter collections by a list of comma separated features.

`--properties` ([]string)
:   Filter collections by a list of comma separated properties.

`--include` ([]string)
:   Include feature, property, snapshots details in the response.

    Allowable list items are: `features`, `properties`, `snapshots`.

`--limit` (int64)
:   The number of records to retrieve. By default, the list operation return the first 10 records. To retrieve different set of records, use `limit` with `offset` to page through the available records.

    The default value is `10`. The maximum value is `100`. The minimum value is `1`.

`--offset` (int64)
:   The number of records to skip. By specifying `offset`, you retrieve a subset of items that starts with the `offset` value. Use `offset` with `limit` to page through the available records.

    The default value is `0`. The minimum value is `0`.

`--search` (string)
:   Searches for the provided keyword and returns the appropriate row with that value. Here the search happens on the '[Name OR Tag]' of the entity.

`--all-pages` (bool)
:   Invoke multiple requests to display all pages of the collection for collections.

#### Example
{: #app-configuration-collections-examples}

```sh
ibmcloud app-configuration collections \
    --expand true \
    --sort created_time \
    --tags 'version 1.1,pre-release' \
    --features my-feature-id,cycle-rentals \
    --properties my-property-id,email-property \
    --include features,properties,snapshots \
    --limit 10 \
    --offset 0 \
    --search 'test tag'
```
{: pre}

### `ibmcloud app-configuration collection-create`
{: #app-configuration-cli-collection-create-command}

Create a collection.

```sh
ibmcloud app-configuration collection-create --name NAME --collection-id COLLECTION-ID [--description DESCRIPTION] [--tags TAGS]
```


#### Command options
{: #app-configuration-collection-create-cli-options}

`--name` (string)
:   Collection name. Allowed special characters are dot ( . ), hyphen( - ), underscore ( _ ) only. Required.

    The maximum length is `256` characters.

`--collection-id` (string)
:   Collection Id. Allowed special characters are dot ( . ), hyphen( - ), underscore ( _ ) only. Required.

    The maximum length is `256` characters.

`--description` (string)
:   Collection description.

    The maximum length is `255` characters.

`--tags` (string)
:   Tags associated with the collection.

#### Example
{: #app-configuration-collection-create-examples}

```sh
ibmcloud app-configuration collection-create \
    --name 'Web App Collection' \
    --collection-id web-app-collection \
    --description 'Collection for Web application' \
    --tags 'version: 1.1, pre-release'
```
{: pre}

### `ibmcloud app-configuration collection-update`
{: #app-configuration-cli-collection-update-command}

Update the collection name, tags and description. Collection Id cannot be updated.

```sh
ibmcloud app-configuration collection-update --collection-id COLLECTION-ID [--name NAME] [--description DESCRIPTION] [--tags TAGS]
```


#### Command options
{: #app-configuration-collection-update-cli-options}

`--collection-id` (string)
:   Collection Id of the collection. Required.

`--name` (string)
:   Collection name. Allowed special characters are dot ( . ), hyphen( - ), underscore ( _ ) only.

    The maximum length is `256` characters.

`--description` (string)
:   Description of the collection.

    The maximum length is `255` characters.

`--tags` (string)
:   Tags associated with the collection.

#### Example
{: #app-configuration-collection-update-examples}

```sh
ibmcloud app-configuration collection-update \
    --collection-id collection_id \
    --name exampleString \
    --description exampleString \
    --tags exampleString
```
{: pre}

### `ibmcloud app-configuration collection`
{: #app-configuration-cli-collection-command}

Retrieve the details of the collection.

```sh
ibmcloud app-configuration collection --collection-id COLLECTION-ID [--expand EXPAND] [--include INCLUDE]
```


#### Command options
{: #app-configuration-collection-cli-options}

`--collection-id` (string)
:   Collection Id of the collection. Required.

`--expand` (bool)
:   If set to `true`, returns expanded view of the resource details.

`--include` ([]string)
:   Include feature, property, snapshots details in the response.

    Allowable list items are: `features`, `properties`, `snapshots`.

#### Example
{: #app-configuration-collection-examples}

```sh
ibmcloud app-configuration collection \
    --collection-id collection_id \
    --expand true \
    --include features,properties,snapshots
```
{: pre}

### `ibmcloud app-configuration collection-delete`
{: #app-configuration-cli-collection-delete-command}

Delete the collection.

```sh
ibmcloud app-configuration collection-delete --collection-id COLLECTION-ID
```


#### Command options
{: #app-configuration-collection-delete-cli-options}

`--collection-id` (string)
:   Collection Id of the collection. Required.

#### Example
{: #app-configuration-collection-delete-examples}

```sh
ibmcloud app-configuration collection-delete \
    --collection-id collection_id
```
{: pre}

## Features
{: #app-configuration-features-cli}

Create and manage different types of feature flags for your apps and services.

### `ibmcloud app-configuration features`
{: #app-configuration-cli-features-command}

List all the feature flags in the specified environment.
Note: If the `--all-pages` option is not set, the command will only retrieve a single page of the collection.

```sh
ibmcloud app-configuration features --environment-id ENVIRONMENT-ID [--expand EXPAND] [--sort SORT] [--tags TAGS] [--collections COLLECTIONS] [--segments SEGMENTS] [--include INCLUDE] [--limit LIMIT] [--offset OFFSET] [--search SEARCH]
```


#### Command options
{: #app-configuration-features-cli-options}

`--environment-id` (string)
:   Environment Id. Required.

`--expand` (bool)
:   If set to `true`, returns expanded view of the resource details.

`--sort` (string)
:   Sort the feature details based on the specified attribute. By default, items are sorted by name.

    Allowable values are: `created_time`, `updated_time`, `id`, `name`.

`--tags` (string)
:   Filter the resources to be returned based on the associated tags. Specify the parameter as a list of comma separated tags. Returns resources associated with any of the specified tags.

`--collections` ([]string)
:   Filter features by a list of comma separated collections.

`--segments` ([]string)
:   Filter features by a list of comma separated segments.

`--include` ([]string)
:   Include the associated collections or targeting rules or change request details in the response.

    Allowable list items are: `collections`, `rules`, `change_request`.

`--limit` (int64)
:   The number of records to retrieve. By default, the list operation return the first 10 records. To retrieve different set of records, use `limit` with `offset` to page through the available records.

    The default value is `10`. The maximum value is `100`. The minimum value is `1`.

`--offset` (int64)
:   The number of records to skip. By specifying `offset`, you retrieve a subset of items that starts with the `offset` value. Use `offset` with `limit` to page through the available records.

    The default value is `0`. The minimum value is `0`.

`--search` (string)
:   Searches for the provided keyword and returns the appropriate row with that value. Here the search happens on the '[Name OR Tag]' of the entity.

`--all-pages` (bool)
:   Invoke multiple requests to display all pages of the collection for features.

#### Example
{: #app-configuration-features-examples}

```sh
ibmcloud app-configuration features \
    --environment-id environment_id \
    --expand true \
    --sort created_time \
    --tags 'version 1.1,pre-release' \
    --collections my-collection-id,ghzindiapvtltd \
    --segments my-segment-id,beta-users \
    --include collections,rules,change_request \
    --limit 10 \
    --offset 0 \
    --search 'test tag'
```
{: pre}

### `ibmcloud app-configuration feature-create`
{: #app-configuration-cli-feature-create-command}

Create a feature flag.

```sh
ibmcloud app-configuration feature-create --environment-id ENVIRONMENT-ID --name NAME --feature-id FEATURE-ID --type TYPE --enabled-value ENABLED-VALUE --disabled-value DISABLED-VALUE [--description DESCRIPTION] [--format FORMAT] [--enabled ENABLED] [--rollout-percentage ROLLOUT-PERCENTAGE] [--tags TAGS] [--segment-rules SEGMENT-RULES] [--collections COLLECTIONS]
```


#### Command options
{: #app-configuration-feature-create-cli-options}

`--environment-id` (string)
:   Environment Id. Required.

`--name` (string)
:   Feature name. Allowed special characters are dot ( . ), hyphen( - ), underscore ( _ ) only. Required.

    The maximum length is `256` characters.

`--feature-id` (string)
:   Feature id. Allowed special characters are dot ( . ), hyphen( - ), underscore ( _ ) only. Required.

    The maximum length is `256` characters.

`--type` (string)
:   Type of the feature (BOOLEAN, STRING, NUMERIC). If `type` is `STRING`, then `format` attribute is required. Required.

    Allowable values are: `BOOLEAN`, `STRING`, `NUMERIC`.

`--enabled-value` (interface{})
:   Value of the feature when it is enabled. The value can be Boolean, Numeric, String - TEXT, String - JSON, String - YAML value as per the `type` and `format` attributes. Required.

    Provide a JSON string option or specify a JSON file to read from by providing a filepath option that begins with a `@`, e.g. `--enabled-value=@path/to/file.json`.

`--disabled-value` (interface{})
:   Value of the feature when it is disabled. The value can be Boolean, Numeric, String - TEXT, String - JSON, String - YAML value as per the `type` and `format` attributes. Required.

    Provide a JSON string option or specify a JSON file to read from by providing a filepath option that begins with a `@`, e.g. `--disabled-value=@path/to/file.json`.

`--description` (string)
:   Feature description.

    The maximum length is `255` characters.

`--format` (string)
:   Format of the feature (TEXT, JSON, YAML) and it is a required attribute when `type` is `STRING`. It is not required for `BOOLEAN` and `NUMERIC` types. This property is populated in the response body of `POST, PUT and GET` calls if the type `STRING` is used and not populated for `BOOLEAN` and `NUMERIC` types.

    Allowable values are: `TEXT`, `JSON`, `YAML`.

`--enabled` (bool)
:   The state of the feature flag.

`--rollout-percentage` (int64)
:   Rollout percentage associated with feature flag. Supported only for Lite and Enterprise plans.

    The default value is `100`. The maximum value is `100`. The minimum value is `0`.

`--tags` (string)
:   Tags associated with the feature.

`--segment-rules` ([`FeatureSegmentRule[]`](#cli-feature-segment-rule-example-schema))
:   Specify the targeting rules that is used to set different feature flag values for different segments.

    Provide a JSON string option or specify a JSON file to read from by providing a filepath option that begins with a `@`, e.g. `--segment-rules=@path/to/file.json`.

`--collections` ([`CollectionRef[]`](#cli-collection-ref-example-schema))
:   List of collection id representing the collections that are associated with the specified feature flag.

    Provide a JSON string option or specify a JSON file to read from by providing a filepath option that begins with a `@`, e.g. `--collections=@path/to/file.json`.

#### Example
{: #app-configuration-feature-create-examples}

```sh
ibmcloud app-configuration feature-create \
    --environment-id environment_id \
    --name 'Cycle Rentals' \
    --feature-id cycle-rentals \
    --type BOOLEAN \
    --enabled-value "true" \
    --disabled-value "false" \
    --description 'Feature flag to enable Cycle Rentals' \
    --format TEXT \
    --enabled true \
    --rollout-percentage 100 \
    --tags 'version: 1.1, pre-release' \
    --segment-rules '[{"rules": [{"segments": ["betausers","premiumusers"]}], "value": "true", "order": 1, "rollout_percentage": 50}]' \
    --collections '[{"collection_id": "ghzinc"}]'
```
{: pre}

### `ibmcloud app-configuration feature-update`
{: #app-configuration-cli-feature-update-command}

Update a feature flag details.

```sh
ibmcloud app-configuration feature-update --environment-id ENVIRONMENT-ID --feature-id FEATURE-ID [--name NAME] [--description DESCRIPTION] [--enabled-value ENABLED-VALUE] [--disabled-value DISABLED-VALUE] [--enabled ENABLED] [--rollout-percentage ROLLOUT-PERCENTAGE] [--tags TAGS] [--segment-rules SEGMENT-RULES] [--collections COLLECTIONS]
```


#### Command options
{: #app-configuration-feature-update-cli-options}

`--environment-id` (string)
:   Environment Id. Required.

`--feature-id` (string)
:   Feature Id. Required.

`--name` (string)
:   Feature name. Allowed special characters are dot ( . ), hyphen( - ), underscore ( _ ) only.

    The maximum length is `256` characters.

`--description` (string)
:   Feature description.

    The maximum length is `255` characters.

`--enabled-value` (interface{})
:   Value of the feature when it is enabled. The value can be Boolean, Numeric, String - TEXT, String - JSON, String - YAML value as per the `type` and `format` attributes.

    Provide a JSON string option or specify a JSON file to read from by providing a filepath option that begins with a `@`, e.g. `--enabled-value=@path/to/file.json`.

`--disabled-value` (interface{})
:   Value of the feature when it is disabled. The value can be Boolean, Numeric, String - TEXT, String - JSON, String - YAML value as per the `type` and `format` attributes.

    Provide a JSON string option or specify a JSON file to read from by providing a filepath option that begins with a `@`, e.g. `--disabled-value=@path/to/file.json`.

`--enabled` (bool)
:   The state of the feature flag.

`--rollout-percentage` (int64)
:   Rollout percentage associated with feature flag. Supported only for Lite and Enterprise plans.

    The default value is `100`. The maximum value is `100`. The minimum value is `0`.

`--tags` (string)
:   Tags associated with the feature.

`--segment-rules` ([`FeatureSegmentRule[]`](#cli-feature-segment-rule-example-schema))
:   Specify the targeting rules that is used to set different property values for different segments.

    Provide a JSON string option or specify a JSON file to read from by providing a filepath option that begins with a `@`, e.g. `--segment-rules=@path/to/file.json`.

`--collections` ([`CollectionRef[]`](#cli-collection-ref-example-schema))
:   List of collection id representing the collections that are associated with the specified property.

    Provide a JSON string option or specify a JSON file to read from by providing a filepath option that begins with a `@`, e.g. `--collections=@path/to/file.json`.

#### Example
{: #app-configuration-feature-update-examples}

```sh
ibmcloud app-configuration feature-update \
    --environment-id environment_id \
    --feature-id feature_id \
    --name 'Cycle Rentals' \
    --description 'Feature flags to enable Cycle Rentals' \
    --enabled-value "true" \
    --disabled-value "false" \
    --enabled true \
    --rollout-percentage 100 \
    --tags 'version: 1.1, yet-to-release' \
    --segment-rules '[{"rules": [{"segments": ["betausers","premiumusers"]}], "value": "true", "order": 1, "rollout_percentage": 90}]' \
    --collections '[{"collection_id": "ghzinc"}]'
```
{: pre}

### `ibmcloud app-configuration feature-values-update`
{: #app-configuration-cli-feature-values-update-command}

Update the feature values. This method can be executed only by the `writer` role. This method allows the update of feature name, feature enabled_value, feature disabled_value, tags, description and feature segment rules, however this method does not allow toggling the feature flag and assigning feature to a collection.

```sh
ibmcloud app-configuration feature-values-update --environment-id ENVIRONMENT-ID --feature-id FEATURE-ID [--name NAME] [--description DESCRIPTION] [--tags TAGS] [--enabled-value ENABLED-VALUE] [--disabled-value DISABLED-VALUE] [--rollout-percentage ROLLOUT-PERCENTAGE] [--segment-rules SEGMENT-RULES]
```


#### Command options
{: #app-configuration-feature-values-update-cli-options}

`--environment-id` (string)
:   Environment Id. Required.

`--feature-id` (string)
:   Feature Id. Required.

`--name` (string)
:   Feature name. Allowed special characters are dot ( . ), hyphen( - ), underscore ( _ ) only.

    The maximum length is `256` characters.

`--description` (string)
:   Feature description.

    The maximum length is `255` characters.

`--tags` (string)
:   Tags associated with the feature.

`--enabled-value` (interface{})
:   Value of the feature when it is enabled. The value can be Boolean, Numeric, String - TEXT, String - JSON, String - YAML value as per the `type` and `format` attributes.

    Provide a JSON string option or specify a JSON file to read from by providing a filepath option that begins with a `@`, e.g. `--enabled-value=@path/to/file.json`.

`--disabled-value` (interface{})
:   Value of the feature when it is disabled. The value can be Boolean, Numeric, String - TEXT, String - JSON, String - YAML value as per the `type` and `format` attributes.

    Provide a JSON string option or specify a JSON file to read from by providing a filepath option that begins with a `@`, e.g. `--disabled-value=@path/to/file.json`.

`--rollout-percentage` (int64)
:   Rollout percentage associated with feature flag. Supported only for Lite and Enterprise plans.

    The default value is `100`. The maximum value is `100`. The minimum value is `0`.

`--segment-rules` ([`FeatureSegmentRule[]`](#cli-feature-segment-rule-example-schema))
:   Specify the targeting rules that is used to set different property values for different segments.

    Provide a JSON string option or specify a JSON file to read from by providing a filepath option that begins with a `@`, e.g. `--segment-rules=@path/to/file.json`.

#### Example
{: #app-configuration-feature-values-update-examples}

```sh
ibmcloud app-configuration feature-values-update \
    --environment-id environment_id \
    --feature-id feature_id \
    --name 'Cycle Rentals' \
    --description 'Feature flags to enable Cycle Rentals' \
    --tags 'version: 1.1, yet-to-release' \
    --enabled-value "true" \
    --disabled-value "false" \
    --rollout-percentage 100 \
    --segment-rules '[{"rules": [{"segments": ["betausers","premiumusers"]}], "value": "true", "order": 1, "rollout_percentage": 100}]'
```
{: pre}

### `ibmcloud app-configuration feature`
{: #app-configuration-cli-feature-command}

Retrieve details of a feature.

```sh
ibmcloud app-configuration feature --environment-id ENVIRONMENT-ID --feature-id FEATURE-ID [--include INCLUDE]
```


#### Command options
{: #app-configuration-feature-cli-options}

`--environment-id` (string)
:   Environment Id. Required.

`--feature-id` (string)
:   Feature Id. Required.

`--include` ([]string)
:   Include the associated collections or targeting rules or change request details in the response.

    Allowable list items are: `collections`, `rules`, `change_request`.

#### Example
{: #app-configuration-feature-examples}

```sh
ibmcloud app-configuration feature \
    --environment-id environment_id \
    --feature-id feature_id \
    --include collections,rules,change_request
```
{: pre}

### `ibmcloud app-configuration feature-delete`
{: #app-configuration-cli-feature-delete-command}

Delete a feature flag.

```sh
ibmcloud app-configuration feature-delete --environment-id ENVIRONMENT-ID --feature-id FEATURE-ID
```


#### Command options
{: #app-configuration-feature-delete-cli-options}

`--environment-id` (string)
:   Environment Id. Required.

`--feature-id` (string)
:   Feature Id. Required.

#### Example
{: #app-configuration-feature-delete-examples}

```sh
ibmcloud app-configuration feature-delete \
    --environment-id environment_id \
    --feature-id feature_id
```
{: pre}

### `ibmcloud app-configuration feature-toggle`
{: #app-configuration-cli-feature-toggle-command}

Toggle a feature.

```sh
ibmcloud app-configuration feature-toggle --environment-id ENVIRONMENT-ID --feature-id FEATURE-ID --enabled ENABLED
```


#### Command options
{: #app-configuration-feature-toggle-cli-options}

`--environment-id` (string)
:   Environment Id. Required.

`--feature-id` (string)
:   Feature Id. Required.

`--enabled` (bool)
:   The state of the feature flag. Required.

#### Example
{: #app-configuration-feature-toggle-examples}

```sh
ibmcloud app-configuration feature-toggle \
    --environment-id environment_id \
    --feature-id feature_id \
    --enabled true
```
{: pre}

## Properties
{: #app-configuration-properties-cli}

Create and manage different types of properties for your apps and services.

### `ibmcloud app-configuration properties`
{: #app-configuration-cli-properties-command}

List all the properties in the specified environment.
Note: If the `--all-pages` option is not set, the command will only retrieve a single page of the collection.

```sh
ibmcloud app-configuration properties --environment-id ENVIRONMENT-ID [--expand EXPAND] [--sort SORT] [--tags TAGS] [--collections COLLECTIONS] [--segments SEGMENTS] [--include INCLUDE] [--limit LIMIT] [--offset OFFSET] [--search SEARCH]
```


#### Command options
{: #app-configuration-properties-cli-options}

`--environment-id` (string)
:   Environment Id. Required.

`--expand` (bool)
:   If set to `true`, returns expanded view of the resource details.

`--sort` (string)
:   Sort the property details based on the specified attribute. By default, items are sorted by name.

    Allowable values are: `created_time`, `updated_time`, `id`, `name`.

`--tags` (string)
:   Filter the resources to be returned based on the associated tags. Specify the parameter as a list of comma separated tags. Returns resources associated with any of the specified tags.

`--collections` ([]string)
:   Filter properties by a list of comma separated collections.

`--segments` ([]string)
:   Filter properties by a list of comma separated segments.

`--include` ([]string)
:   Include the associated collections or targeting rules details in the response.

    Allowable list items are: `collections`, `rules`.

`--limit` (int64)
:   The number of records to retrieve. By default, the list operation return the first 10 records. To retrieve different set of records, use `limit` with `offset` to page through the available records.

    The default value is `10`. The maximum value is `100`. The minimum value is `1`.

`--offset` (int64)
:   The number of records to skip. By specifying `offset`, you retrieve a subset of items that starts with the `offset` value. Use `offset` with `limit` to page through the available records.

    The default value is `0`. The minimum value is `0`.

`--search` (string)
:   Searches for the provided keyword and returns the appropriate row with that value. Here the search happens on the '[Name OR Tag]' of the entity.

`--all-pages` (bool)
:   Invoke multiple requests to display all pages of the collection for properties.

#### Example
{: #app-configuration-properties-examples}

```sh
ibmcloud app-configuration properties \
    --environment-id environment_id \
    --expand true \
    --sort created_time \
    --tags 'version 1.1,pre-release' \
    --collections my-collection-id,ghzindiapvtltd \
    --segments my-segment-id,beta-users \
    --include collections,rules \
    --limit 10 \
    --offset 0 \
    --search 'test tag'
```
{: pre}

### `ibmcloud app-configuration property-create`
{: #app-configuration-cli-property-create-command}

Create a Property.

```sh
ibmcloud app-configuration property-create --environment-id ENVIRONMENT-ID --name NAME --property-id PROPERTY-ID --type TYPE --value VALUE [--description DESCRIPTION] [--format FORMAT] [--tags TAGS] [--segment-rules SEGMENT-RULES] [--collections COLLECTIONS]
```


#### Command options
{: #app-configuration-property-create-cli-options}

`--environment-id` (string)
:   Environment Id. Required.

`--name` (string)
:   Property name. Allowed special characters are dot ( . ), hyphen( - ), underscore ( _ ) only. Required.

    The maximum length is `256` characters.

`--property-id` (string)
:   Property id. Allowed special characters are dot ( . ), hyphen( - ), underscore ( _ ) only. Required.

    The maximum length is `256` characters.

`--type` (string)
:   Type of the property (BOOLEAN, STRING, NUMERIC, SECRETREF). If `type` is `STRING`, then `format` attribute is required. Required.

    Allowable values are: `BOOLEAN`, `STRING`, `NUMERIC`, `SECRETREF`.

`--value` (interface{})
:   Value of the Property. The value can be Boolean, Numeric, SecretRef, String - TEXT, String - JSON, String - YAML as per the `type` and `format` attributes. Required.

    Provide a JSON string option or specify a JSON file to read from by providing a filepath option that begins with a `@`, e.g. `--value=@path/to/file.json`.

`--description` (string)
:   Property description.

    The maximum length is `255` characters.

`--format` (string)
:   Format of the property (TEXT, JSON, YAML) and it is a required attribute when `type` is `STRING`. It is not required for `BOOLEAN`, `NUMERIC` or `SECRETREF` types. This attribute is populated in the response body of `POST, PUT and GET` calls if the type `STRING` is used and not populated for `BOOLEAN`, `NUMERIC` and `SECRETREF` types.

    Allowable values are: `TEXT`, `JSON`, `YAML`.

`--tags` (string)
:   Tags associated with the property.

`--segment-rules` ([`SegmentRule[]`](#cli-segment-rule-example-schema))
:   Specify the targeting rules that is used to set different property values for different segments.

    Provide a JSON string option or specify a JSON file to read from by providing a filepath option that begins with a `@`, e.g. `--segment-rules=@path/to/file.json`.

`--collections` ([`CollectionRef[]`](#cli-collection-ref-example-schema))
:   List of collection id representing the collections that are associated with the specified property.

    Provide a JSON string option or specify a JSON file to read from by providing a filepath option that begins with a `@`, e.g. `--collections=@path/to/file.json`.

#### Example
{: #app-configuration-property-create-examples}

```sh
ibmcloud app-configuration property-create \
    --environment-id environment_id \
    --name 'Email property' \
    --property-id email-property \
    --type BOOLEAN \
    --value "true" \
    --description 'Property for email' \
    --format TEXT \
    --tags 'version: 1.1, pre-release' \
    --segment-rules '[{"rules": [{"segments": ["betausers","premiumusers"]}], "value": "true", "order": 1}]' \
    --collections '[{"collection_id": "ghzinc"}]'
```
{: pre}

### `ibmcloud app-configuration property-update`
{: #app-configuration-cli-property-update-command}

Update a Property.

```sh
ibmcloud app-configuration property-update --environment-id ENVIRONMENT-ID --property-id PROPERTY-ID [--name NAME] [--description DESCRIPTION] [--value VALUE] [--tags TAGS] [--segment-rules SEGMENT-RULES] [--collections COLLECTIONS]
```


#### Command options
{: #app-configuration-property-update-cli-options}

`--environment-id` (string)
:   Environment Id. Required.

`--property-id` (string)
:   Property Id. Required.

`--name` (string)
:   Property name. Allowed special characters are dot ( . ), hyphen( - ), underscore ( _ ) only.

    The maximum length is `256` characters.

`--description` (string)
:   Property description.

    The maximum length is `255` characters.

`--value` (interface{})
:   Value of the Property. The value can be Boolean, Numeric, SecretRef, String - TEXT, String - JSON, String - YAML as per the `type` and `format` attributes.

    Provide a JSON string option or specify a JSON file to read from by providing a filepath option that begins with a `@`, e.g. `--value=@path/to/file.json`.

`--tags` (string)
:   Tags associated with the property.

`--segment-rules` ([`SegmentRule[]`](#cli-segment-rule-example-schema))
:   Specify the targeting rules that is used to set different property values for different segments.

    Provide a JSON string option or specify a JSON file to read from by providing a filepath option that begins with a `@`, e.g. `--segment-rules=@path/to/file.json`.

`--collections` ([`CollectionRef[]`](#cli-collection-ref-example-schema))
:   List of collection id representing the collections that are associated with the specified property.

    Provide a JSON string option or specify a JSON file to read from by providing a filepath option that begins with a `@`, e.g. `--collections=@path/to/file.json`.

#### Example
{: #app-configuration-property-update-examples}

```sh
ibmcloud app-configuration property-update \
    --environment-id environment_id \
    --property-id property_id \
    --name 'Email property' \
    --description 'Property for email' \
    --value "true" \
    --tags 'version: 1.1, pre-release' \
    --segment-rules '[{"rules": [{"segments": ["betausers","premiumusers"]}], "value": "true", "order": 1}]' \
    --collections '[{"collection_id": "ghzinc"}]'
```
{: pre}

### `ibmcloud app-configuration property-values-update`
{: #app-configuration-cli-property-values-update-command}

Update the property values. This method can be executed by the `writer` role. Property value and targeting rules can be updated, however this method does not allow assigning property to a collection.

```sh
ibmcloud app-configuration property-values-update --environment-id ENVIRONMENT-ID --property-id PROPERTY-ID [--name NAME] [--description DESCRIPTION] [--tags TAGS] [--value VALUE] [--segment-rules SEGMENT-RULES]
```


#### Command options
{: #app-configuration-property-values-update-cli-options}

`--environment-id` (string)
:   Environment Id. Required.

`--property-id` (string)
:   Property Id. Required.

`--name` (string)
:   Property name. Allowed special characters are dot ( . ), hyphen( - ), underscore ( _ ) only.

    The maximum length is `256` characters.

`--description` (string)
:   Property description.

    The maximum length is `255` characters.

`--tags` (string)
:   Tags associated with the property.

`--value` (interface{})
:   Value of the Property. The value can be Boolean, Numeric, SecretRef, String - TEXT, String - JSON, String - YAML as per the `type` and `format` attributes.

    Provide a JSON string option or specify a JSON file to read from by providing a filepath option that begins with a `@`, e.g. `--value=@path/to/file.json`.

`--segment-rules` ([`SegmentRule[]`](#cli-segment-rule-example-schema))
:   Specify the targeting rules that is used to set different property values for different segments.

    Provide a JSON string option or specify a JSON file to read from by providing a filepath option that begins with a `@`, e.g. `--segment-rules=@path/to/file.json`.

#### Example
{: #app-configuration-property-values-update-examples}

```sh
ibmcloud app-configuration property-values-update \
    --environment-id environment_id \
    --property-id property_id \
    --name 'Email property' \
    --description 'Property for email' \
    --tags 'version: 1.1, pre-release' \
    --value "true" \
    --segment-rules '[{"rules": [{"segments": ["betausers","premiumusers"]}], "value": "true", "order": 1}]'
```
{: pre}

### `ibmcloud app-configuration property`
{: #app-configuration-cli-property-command}

Retrieve details of a property.

```sh
ibmcloud app-configuration property --environment-id ENVIRONMENT-ID --property-id PROPERTY-ID [--include INCLUDE]
```


#### Command options
{: #app-configuration-property-cli-options}

`--environment-id` (string)
:   Environment Id. Required.

`--property-id` (string)
:   Property Id. Required.

`--include` ([]string)
:   Include the associated collections or targeting rules details in the response.

    Allowable list items are: `collections`, `rules`.

#### Example
{: #app-configuration-property-examples}

```sh
ibmcloud app-configuration property \
    --environment-id environment_id \
    --property-id property_id \
    --include collections,rules
```
{: pre}

### `ibmcloud app-configuration property-delete`
{: #app-configuration-cli-property-delete-command}

Delete a Property.

```sh
ibmcloud app-configuration property-delete --environment-id ENVIRONMENT-ID --property-id PROPERTY-ID
```


#### Command options
{: #app-configuration-property-delete-cli-options}

`--environment-id` (string)
:   Environment Id. Required.

`--property-id` (string)
:   Property Id. Required.

#### Example
{: #app-configuration-property-delete-examples}

```sh
ibmcloud app-configuration property-delete \
    --environment-id environment_id \
    --property-id property_id
```
{: pre}

## Segments
{: #app-configuration-segments-cli}

Segments define a group of users or resources based on rules. Feature flags or Properties can target segments to deliver variants of a feature or property.

### `ibmcloud app-configuration segments`
{: #app-configuration-cli-segments-command}

List all the segments.
Note: If the `--all-pages` option is not set, the command will only retrieve a single page of the collection.

```sh
ibmcloud app-configuration segments [--expand EXPAND] [--sort SORT] [--tags TAGS] [--include INCLUDE] [--limit LIMIT] [--offset OFFSET] [--search SEARCH]
```


#### Command options
{: #app-configuration-segments-cli-options}

`--expand` (bool)
:   If set to `true`, returns expanded view of the resource details.

`--sort` (string)
:   Sort the segment details based on the specified attribute. By default, items are sorted by name.

    Allowable values are: `created_time`, `updated_time`, `id`, `name`.

`--tags` (string)
:   Filter the resources to be returned based on the associated tags. Specify the parameter as a list of comma separated tags. Returns resources associated with any of the specified tags.

`--include` (string)
:   Segment details to include the associated rules in the response.

    Allowable values are: `rules`.

`--limit` (int64)
:   The number of records to retrieve. By default, the list operation return the first 10 records. To retrieve different set of records, use `limit` with `offset` to page through the available records.

    The default value is `10`. The maximum value is `100`. The minimum value is `1`.

`--offset` (int64)
:   The number of records to skip. By specifying `offset`, you retrieve a subset of items that starts with the `offset` value. Use `offset` with `limit` to page through the available records.

    The default value is `0`. The minimum value is `0`.

`--search` (string)
:   Searches for the provided keyword and returns the appropriate row with that value. Here the search happens on the '[Name OR Tag]' of the entity.

`--all-pages` (bool)
:   Invoke multiple requests to display all pages of the collection for segments.

#### Example
{: #app-configuration-segments-examples}

```sh
ibmcloud app-configuration segments \
    --expand true \
    --sort created_time \
    --tags 'version 1.1,pre-release' \
    --include rules \
    --limit 10 \
    --offset 0 \
    --search 'test tag'
```
{: pre}

### `ibmcloud app-configuration segment-create`
{: #app-configuration-cli-segment-create-command}

Create a segment.

```sh
ibmcloud app-configuration segment-create --name NAME --segment-id SEGMENT-ID --rules RULES [--description DESCRIPTION] [--tags TAGS]
```


#### Command options
{: #app-configuration-segment-create-cli-options}

`--name` (string)
:   Segment name. Allowed special characters are dot ( . ), hyphen( - ), underscore ( _ ) only. Required.

    The maximum length is `256` characters.

`--segment-id` (string)
:   Segment id. Allowed special characters are dot ( . ), hyphen( - ), underscore ( _ ) only. Required.

    The maximum length is `256` characters.

`--rules` ([`Rule[]`](#cli-rule-example-schema))
:   List of rules that determine if the entity belongs to the segment during feature / property evaluation. An entity is identified by an unique identifier and the attributes that it defines. Any feature flag and property value evaluation is performed in the context of an entity when it is targeted to segments. Required.

    Provide a JSON string option or specify a JSON file to read from by providing a filepath option that begins with a `@`, e.g. `--rules=@path/to/file.json`.

`--description` (string)
:   Segment description.

    The maximum length is `255` characters.

`--tags` (string)
:   Tags associated with the segments.

#### Example
{: #app-configuration-segment-create-examples}

```sh
ibmcloud app-configuration segment-create \
    --name 'Beta Users' \
    --segment-id beta-users \
    --rules '[{"attribute_name": "email", "operator": "endsWith", "values": ["@in.mnc.com","@us.mnc.com"]}]' \
    --description 'Segment containing the beta users' \
    --tags 'version: 1.1, stage'
```
{: pre}

### `ibmcloud app-configuration segment-update`
{: #app-configuration-cli-segment-update-command}

Update the segment properties.

```sh
ibmcloud app-configuration segment-update --segment-id SEGMENT-ID [--name NAME] [--description DESCRIPTION] [--tags TAGS] [--rules RULES]
```


#### Command options
{: #app-configuration-segment-update-cli-options}

`--segment-id` (string)
:   Segment Id. Required.

`--name` (string)
:   Segment name. Allowed special characters are dot ( . ), hyphen( - ), underscore ( _ ) only.

    The maximum length is `256` characters.

`--description` (string)
:   Segment description.

    The maximum length is `255` characters.

`--tags` (string)
:   Tags associated with segments.

`--rules` ([`Rule[]`](#cli-rule-example-schema))
:   List of rules that determine if the entity belongs to the segment during feature / property evaluation. An entity is identified by an unique identifier and the attributes that it defines. Any feature flag and property value evaluation is performed in the context of an entity when it is targeted to segments.

    Provide a JSON string option or specify a JSON file to read from by providing a filepath option that begins with a `@`, e.g. `--rules=@path/to/file.json`.

#### Example
{: #app-configuration-segment-update-examples}

```sh
ibmcloud app-configuration segment-update \
    --segment-id segment_id \
    --name exampleString \
    --description exampleString \
    --tags exampleString \
    --rules '[{"attribute_name": "exampleString", "operator": "is", "values": ["exampleString","anotherTestString"]}]'
```
{: pre}

### `ibmcloud app-configuration segment`
{: #app-configuration-cli-segment-command}

Retrieve details of a segment.

```sh
ibmcloud app-configuration segment --segment-id SEGMENT-ID [--include INCLUDE]
```


#### Command options
{: #app-configuration-segment-cli-options}

`--segment-id` (string)
:   Segment Id. Required.

`--include` ([]string)
:   Include feature and property details in the response.

    Allowable list items are: `features`, `properties`.

#### Example
{: #app-configuration-segment-examples}

```sh
ibmcloud app-configuration segment \
    --segment-id segment_id \
    --include features,properties
```
{: pre}

### `ibmcloud app-configuration segment-delete`
{: #app-configuration-cli-segment-delete-command}

Delete a segment.

```sh
ibmcloud app-configuration segment-delete --segment-id SEGMENT-ID
```


#### Command options
{: #app-configuration-segment-delete-cli-options}

`--segment-id` (string)
:   Segment Id. Required.

#### Example
{: #app-configuration-segment-delete-examples}

```sh
ibmcloud app-configuration segment-delete \
    --segment-id segment_id
```
{: pre}

## Snapshots
{: #app-configuration-snapshots-cli}

Snapshots are a way to capture the current configuration of your app or environment and sync the modified config into a Git repo.

### `ibmcloud app-configuration gitconfigs`
{: #app-configuration-cli-gitconfigs-command}

List all the Git configs.
Note: If the `--all-pages` option is not set, the command will only retrieve a single page of the collection.

```sh
ibmcloud app-configuration gitconfigs [--sort SORT] [--collection-id COLLECTION-ID] [--environment-id ENVIRONMENT-ID] [--limit LIMIT] [--offset OFFSET] [--search SEARCH]
```


#### Command options
{: #app-configuration-gitconfigs-cli-options}

`--sort` (string)
:   Sort the git configurations details based on the specified attribute. By default, items are sorted by name.

    Allowable values are: `created_time`, `updated_time`, `id`, `name`.

`--collection-id` (string)
:   Filters the response based on the specified collection_id.

`--environment-id` (string)
:   Filters the response based on the specified environment_id.

`--limit` (int64)
:   The number of records to retrieve. By default, the list operation return the first 10 records. To retrieve different set of records, use `limit` with `offset` to page through the available records.

    The default value is `10`. The maximum value is `100`. The minimum value is `1`.

`--offset` (int64)
:   The number of records to skip. By specifying `offset`, you retrieve a subset of items that starts with the `offset` value. Use `offset` with `limit` to page through the available records.

    The default value is `0`. The minimum value is `0`.

`--search` (string)
:   Searches for the provided keyword and returns the appropriate row with that value. Here the search happens on the '[Name]' of the entity.

`--all-pages` (bool)
:   Invoke multiple requests to display all pages of the collection for gitconfigs.

#### Example
{: #app-configuration-gitconfigs-examples}

```sh
ibmcloud app-configuration gitconfigs \
    --sort created_time \
    --collection-id collection_id \
    --environment-id environment_id \
    --limit 10 \
    --offset 0 \
    --search search_string
```
{: pre}

### `ibmcloud app-configuration gitconfig-create`
{: #app-configuration-cli-gitconfig-create-command}

Create a Git config.

```sh
ibmcloud app-configuration gitconfig-create --git-config-name GIT-CONFIG-NAME --git-config-id GIT-CONFIG-ID --collection-id COLLECTION-ID --environment-id ENVIRONMENT-ID --git-url GIT-URL --git-branch GIT-BRANCH --git-file-path GIT-FILE-PATH --git-token GIT-TOKEN
```


#### Command options
{: #app-configuration-gitconfig-create-cli-options}

`--git-config-name` (string)
:   Git config name. Allowed special characters are dot ( . ), hyphen( - ), underscore ( _ ) only. Required.

    The maximum length is `100` characters.

`--git-config-id` (string)
:   Git config id. Allowed special characters are dot ( . ), hyphen( - ), underscore ( _ ) only. Required.

    The maximum length is `30` characters.

`--collection-id` (string)
:   Collection Id. Required.

`--environment-id` (string)
:   Environment Id. Required.

`--git-url` (string)
:   Git url which will be used to connect to the github account. The url must be formed in this format, https://api.github.com/repos/{owner}/{repo_name} for the personal git account. If you are using the organization account then url must be in this format https://github.{organization_name}.com/api/v3/repos/{owner}/{repo_name} . Note do not provide /(slash) in the beginning or at the end of the url. Required.

`--git-branch` (string)
:   Branch name to which you need to write or update the configuration. Just provide the branch name, do not provide any /(slashes) in the beginning or at the end of the branch name. Note make sure branch exists in your repository. Required.

`--git-file-path` (string)
:   Git file path, this is a path where your configuration file will be written. The path must contain the file name with `json` extension. We only create or update `json` extension file. Note do not provide any /(slashes) in the beginning or at the end of the file path. Required.

`--git-token` (string)
:   Git token, this needs to be provided with enough permission to write and update the file. Required.

#### Example
{: #app-configuration-gitconfig-create-examples}

```sh
ibmcloud app-configuration gitconfig-create \
    --git-config-name boot-strap-configuration \
    --git-config-id boot-strap-configuration \
    --collection-id web-app-collection \
    --environment-id dev \
    --git-url https://github.ibm.com/api/v3/repos/jhondoe-owner/my-test-repo \
    --git-branch main \
    --git-file-path code/development/README.json \
    --git-token 61a792eahhGHji223jijb55a6cfdd4d5cde4c8a67esjjhjhHVH
```
{: pre}

### `ibmcloud app-configuration gitconfig-update`
{: #app-configuration-cli-gitconfig-update-command}

Update the gitconfig properties.

```sh
ibmcloud app-configuration gitconfig-update --git-config-id GIT-CONFIG-ID [--git-config-name GIT-CONFIG-NAME] [--collection-id COLLECTION-ID] [--environment-id ENVIRONMENT-ID] [--git-url GIT-URL] [--git-branch GIT-BRANCH] [--git-file-path GIT-FILE-PATH] [--git-token GIT-TOKEN]
```


#### Command options
{: #app-configuration-gitconfig-update-cli-options}

`--git-config-id` (string)
:   Git Config Id. Required.

`--git-config-name` (string)
:   Git config name. Allowed special characters are dot ( . ), hyphen( - ), underscore ( _ ) only.

    The maximum length is `100` characters.

`--collection-id` (string)
:   Collection Id.

`--environment-id` (string)
:   Environment Id.

`--git-url` (string)
:   Git url which will be used to connect to the github account. The url must be formed in this format, https://api.github.com/repos/{owner}/{repo_name} for the personal git account. If you are using the organization account then url must be in this format https://github.{organization_name}.com/api/v3/repos/{owner}/{repo_name} . Note do not provide /(slash) in the beginning or at the end of the url.

`--git-branch` (string)
:   Branch name to which you need to write or update the configuration. Just provide the branch name, do not provide any /(slashes) in the beginning or at the end of the branch name. Note make sure branch exists in your repository.

`--git-file-path` (string)
:   Git file path, this is a path where your configuration file will be written. The path must contain the file name with `json` extension. We only create or update `json` extension file. Note do not provide any /(slashes) in the beginning or at the end of the file path.

`--git-token` (string)
:   Git token, this needs to be provided with enough permission to write and update the file.

#### Example
{: #app-configuration-gitconfig-update-examples}

```sh
ibmcloud app-configuration gitconfig-update \
    --git-config-id git_config_id \
    --git-config-name exampleString \
    --collection-id exampleString \
    --environment-id exampleString \
    --git-url exampleString \
    --git-branch exampleString \
    --git-file-path exampleString \
    --git-token exampleString
```
{: pre}

### `ibmcloud app-configuration gitconfig`
{: #app-configuration-cli-gitconfig-command}

Retrieve details of a gitconfig.

```sh
ibmcloud app-configuration gitconfig --git-config-id GIT-CONFIG-ID
```


#### Command options
{: #app-configuration-gitconfig-cli-options}

`--git-config-id` (string)
:   Git Config Id. Required.

#### Example
{: #app-configuration-gitconfig-examples}

```sh
ibmcloud app-configuration gitconfig \
    --git-config-id git_config_id
```
{: pre}

### `ibmcloud app-configuration gitconfig-delete`
{: #app-configuration-cli-gitconfig-delete-command}

Delete a gitconfig.

```sh
ibmcloud app-configuration gitconfig-delete --git-config-id GIT-CONFIG-ID
```


#### Command options
{: #app-configuration-gitconfig-delete-cli-options}

`--git-config-id` (string)
:   Git Config Id. Required.

#### Example
{: #app-configuration-gitconfig-delete-examples}

```sh
ibmcloud app-configuration gitconfig-delete \
    --git-config-id git_config_id
```
{: pre}

### `ibmcloud app-configuration gitconfig-promote`
{: #app-configuration-cli-gitconfig-promote-command}

Promote configuration, this api will write or update your chosen configuration to the GitHub based on the git url, file path and branch data. In simple words this api will create or updates the bootstrap json file.

```sh
ibmcloud app-configuration gitconfig-promote --git-config-id GIT-CONFIG-ID
```


#### Command options
{: #app-configuration-gitconfig-promote-cli-options}

`--git-config-id` (string)
:   Git Config Id. Required.

#### Example
{: #app-configuration-gitconfig-promote-examples}

```sh
ibmcloud app-configuration gitconfig-promote \
    --git-config-id git_config_id
```
{: pre}

### `ibmcloud app-configuration gitconfig-restore`
{: #app-configuration-cli-gitconfig-restore-command}

Restore configuration, this api will write or update your chosen configuration from the GitHub to App configuration instance. The api will read the contents in the json file that was created using promote API and recreate or updates the App configuration instance with the file contents like properties, features and segments.

```sh
ibmcloud app-configuration gitconfig-restore --git-config-id GIT-CONFIG-ID
```


#### Command options
{: #app-configuration-gitconfig-restore-cli-options}

`--git-config-id` (string)
:   Git Config Id. Required.

#### Example
{: #app-configuration-gitconfig-restore-examples}

```sh
ibmcloud app-configuration gitconfig-restore \
    --git-config-id git_config_id
```
{: pre}

## OriginConfig
{: #app-configuration-origin-config-cli}

Use settings to add more configurations required by external applications to access App Configuration resources.

### `ibmcloud app-configuration originconfigs`
{: #app-configuration-cli-originconfigs-command}

List all the Origin Configs.

```sh
ibmcloud app-configuration originconfigs
```


#### Example
{: #app-configuration-originconfigs-examples}

```sh
ibmcloud app-configuration originconfigs
```
{: pre}

### `ibmcloud app-configuration originconfigs-update`
{: #app-configuration-cli-originconfigs-update-command}

Update the Origin Configs.

```sh
ibmcloud app-configuration originconfigs-update --allowed-origins ALLOWED-ORIGINS
```


#### Command options
{: #app-configuration-originconfigs-update-cli-options}

`--allowed-origins` ([]string)
:   List of allowed origins. Specify the parameter as a list of comma separated origins. Required.

#### Example
{: #app-configuration-originconfigs-update-examples}

```sh
ibmcloud app-configuration originconfigs-update \
    --allowed-origins exampleString,anotherTestString
```
{: pre}

## WorkflowConfigs
{: #app-configuration-workflow-configs-cli}

Manage feature flags enablement by adding additional workflow with ServiceNow® integration with App Configuration.

### `ibmcloud app-configuration workflowconfig`
{: #app-configuration-cli-workflowconfig-command}

Get the environment specific workflow Configs.

```sh
ibmcloud app-configuration workflowconfig --environment-id ENVIRONMENT-ID
```


#### Command options
{: #app-configuration-workflowconfig-cli-options}

`--environment-id` (string)
:   Environment Id. Required.

#### Example
{: #app-configuration-workflowconfig-examples}

```sh
ibmcloud app-configuration workflowconfig \
    --environment-id environment_id
```
{: pre}

### `ibmcloud app-configuration workflowconfig-create`
{: #app-configuration-cli-workflowconfig-create-command}

Create a Workflow.

```sh
ibmcloud app-configuration workflowconfig-create --environment-id ENVIRONMENT-ID --workflow-url WORKFLOW-URL --approval-group-name APPROVAL-GROUP-NAME --approval-expiration APPROVAL-EXPIRATION [--workflow-credentials WORKFLOW-CREDENTIALS | --workflow-credentials-username WORKFLOW-CREDENTIALS-USERNAME --workflow-credentials-password WORKFLOW-CREDENTIALS-PASSWORD --workflow-credentials-client-id WORKFLOW-CREDENTIALS-CLIENT-ID --workflow-credentials-client-secret WORKFLOW-CREDENTIALS-CLIENT-SECRET] --enabled ENABLED
```


#### Command options
{: #app-configuration-workflowconfig-create-cli-options}

`--environment-id` (string)
:   Environment Id. Required.

`--workflow-url` (string)
:   Only service now url https://xxxxx.service-now.com allowed, xxxxx is the service now instance id. Required.

    The maximum length is `200` characters.

`--approval-group-name` (string)
:   Group name of personals who can approve the Change Request on your Service Now. It must be first registered in your Service Now then it must be added here. Required.

    The maximum length is `100` characters.

`--approval-expiration` (int64)
:   Integer number identifies as hours which helps in adding approval start and end time to the created Change Request. Required.

    The maximum value is `999`. The minimum value is `1`.

`--workflow-credentials` ([`WorkflowCredentials`](#cli-workflow-credentials-example-schema))
:   The credentials of the Service Now instance. This JSON option can instead be provided by setting individual fields with other options. It is mutually exclusive with those options.

    Provide a JSON string option or specify a JSON file to read from by providing a filepath option that begins with a `@`, e.g. `--workflow-credentials=@path/to/file.json`.

`--enabled` (bool)
:   This option enables the workflow configuration per environment. User must set it to true if they wish to create Change Request for flag state changes. Required.

    The default value is `false`.

`--workflow-credentials-username` (string)
:   Service Now instance login username. This option provides a value for a sub-field of the JSON option 'workflow-credentials'. It is mutually exclusive with that option.

`--workflow-credentials-password` (string)
:   Service Now instance login password. This option provides a value for a sub-field of the JSON option 'workflow-credentials'. It is mutually exclusive with that option.

`--workflow-credentials-client-id` (string)
:   The auto-generated unique ID of the application in your Service Now instance. This option provides a value for a sub-field of the JSON option 'workflow-credentials'. It is mutually exclusive with that option.

`--workflow-credentials-client-secret` (string)
:   The secret string that both the Service Now instance and the client application use to authorize communications with one another. This option provides a value for a sub-field of the JSON option 'workflow-credentials'. It is mutually exclusive with that option.

#### Examples
{: #app-configuration-workflowconfig-create-examples}

```sh
ibmcloud app-configuration workflowconfig-create \
    --environment-id environment_id \
    --workflow-url https://xxxxx.service-now.com \
    --approval-group-name WorkflowCRApprovers \
    --approval-expiration 10 \
    --workflow-credentials '{"username": "user", "password": "pwd", "client_id": "client id value", "client_secret": "clientsecret"}' \
    --enabled true
```
{: pre}

Alternatively, granular options are available for the sub-fields of JSON string options:
```sh
ibmcloud app-configuration workflowconfig-create \
    --environment-id environment_id \
    --workflow-url https://xxxxx.service-now.com \
    --approval-group-name WorkflowCRApprovers \
    --approval-expiration 10 \
    --enabled true \
    --workflow-credentials-username admin \
    --workflow-credentials-password exampleString \
    --workflow-credentials-client-id f7b6379b55d08210f8ree233afc7256d \
    --workflow-credentials-client-secret exampleString
```
{: pre}

### `ibmcloud app-configuration workflowconfig-update`
{: #app-configuration-cli-workflowconfig-update-command}

Update a Workflow.

```sh
ibmcloud app-configuration workflowconfig-update --environment-id ENVIRONMENT-ID [--workflow-url WORKFLOW-URL] [--approval-group-name APPROVAL-GROUP-NAME] [--approval-expiration APPROVAL-EXPIRATION] [--workflow-credentials WORKFLOW-CREDENTIALS | --workflow-credentials-username WORKFLOW-CREDENTIALS-USERNAME --workflow-credentials-password WORKFLOW-CREDENTIALS-PASSWORD --workflow-credentials-client-id WORKFLOW-CREDENTIALS-CLIENT-ID --workflow-credentials-client-secret WORKFLOW-CREDENTIALS-CLIENT-SECRET] [--enabled ENABLED]
```


#### Command options
{: #app-configuration-workflowconfig-update-cli-options}

`--environment-id` (string)
:   Environment Id. Required.

`--workflow-url` (string)
:   Service Now instance URL. Only url https://xxxxx.service-now.com allowed, xxxxx is the service now instance id.

    The maximum length is `200` characters.

`--approval-group-name` (string)
:   Group name of personals who can approve the Change Request on your Service Now. It must be first registered in your Service Now then it must be added here.

    The maximum length is `100` characters.

`--approval-expiration` (int64)
:   Integer number identifies as hours which helps in adding approval start and end time to the created Change Request.

    The maximum value is `999`. The minimum value is `1`.

`--workflow-credentials` ([`WorkflowCredentials`](#cli-workflow-credentials-example-schema))
:   The credentials of the Service Now instance. This JSON option can instead be provided by setting individual fields with other options. It is mutually exclusive with those options.

    Provide a JSON string option or specify a JSON file to read from by providing a filepath option that begins with a `@`, e.g. `--workflow-credentials=@path/to/file.json`.

`--enabled` (bool)
:   This option enables the workflow configuration per environment. User must set it to true if they wish to create Change Request for flag state changes.

    The default value is `false`.

`--workflow-credentials-username` (string)
:   Service Now instance login username. This option provides a value for a sub-field of the JSON option 'workflow-credentials'. It is mutually exclusive with that option.

`--workflow-credentials-password` (string)
:   Service Now instance login password. This option provides a value for a sub-field of the JSON option 'workflow-credentials'. It is mutually exclusive with that option.

`--workflow-credentials-client-id` (string)
:   The auto-generated unique ID of the application in your Service Now instance. This option provides a value for a sub-field of the JSON option 'workflow-credentials'. It is mutually exclusive with that option.

`--workflow-credentials-client-secret` (string)
:   The secret string that both the Service Now instance and the client application use to authorize communications with one another. This option provides a value for a sub-field of the JSON option 'workflow-credentials'. It is mutually exclusive with that option.

#### Examples
{: #app-configuration-workflowconfig-update-examples}

```sh
ibmcloud app-configuration workflowconfig-update \
    --environment-id environment_id \
    --workflow-url exampleString \
    --approval-group-name exampleString \
    --approval-expiration 1 \
    --workflow-credentials '{"username": "admin", "password": "exampleString", "client_id": "f7b6379b55d08210f8ree233afc7256d", "client_secret": "exampleString"}' \
    --enabled false
```
{: pre}

Alternatively, granular options are available for the sub-fields of JSON string options:
```sh
ibmcloud app-configuration workflowconfig-update \
    --environment-id environment_id \
    --workflow-url exampleString \
    --approval-group-name exampleString \
    --approval-expiration 1 \
    --enabled false \
    --workflow-credentials-username admin \
    --workflow-credentials-password exampleString \
    --workflow-credentials-client-id f7b6379b55d08210f8ree233afc7256d \
    --workflow-credentials-client-secret exampleString
```
{: pre}

### `ibmcloud app-configuration workflowconfig-delete`
{: #app-configuration-cli-workflowconfig-delete-command}

Delete a  Workflow config.

```sh
ibmcloud app-configuration workflowconfig-delete --environment-id ENVIRONMENT-ID
```


#### Command options
{: #app-configuration-workflowconfig-delete-cli-options}

`--environment-id` (string)
:   Environment Id. Required.

#### Example
{: #app-configuration-workflowconfig-delete-examples}

```sh
ibmcloud app-configuration workflowconfig-delete \
    --environment-id environment_id
```
{: pre}

## Config
{: #app-configuration-config-cli}

Export and Import configurations from and to App Configuration instance.

### `ibmcloud app-configuration instance-import`
{: #app-configuration-cli-instance-import-command}

Import configuration to the instance.

```sh
ibmcloud app-configuration instance-import [--environments ENVIRONMENTS] [--collections COLLECTIONS] [--segments SEGMENTS] [--clean CLEAN]
```


#### Command options
{: #app-configuration-instance-import-cli-options}

`--environments` ([`ImportEnvironmentSchema[]`](#cli-import-environment-schema-example-schema))
:   Array will contain features and properties per environment.

    Provide a JSON string option or specify a JSON file to read from by providing a filepath option that begins with a `@`, e.g. `--environments=@path/to/file.json`.

`--collections` ([`ImportCollectionSchema[]`](#cli-import-collection-schema-example-schema))
:   Array will contain collections details.

    Provide a JSON string option or specify a JSON file to read from by providing a filepath option that begins with a `@`, e.g. `--collections=@path/to/file.json`.

`--segments` ([`ImportSegmentSchema[]`](#cli-import-segment-schema-example-schema))
:   Array will contain segments details.

    Provide a JSON string option or specify a JSON file to read from by providing a filepath option that begins with a `@`, e.g. `--segments=@path/to/file.json`.

`--clean` (string)
:   Full instance import requires query parameter `clean=true` to perform wiping of the existing data.

#### Example
{: #app-configuration-instance-import-examples}

```sh
ibmcloud app-configuration instance-import \
    --environments '[{"name": "Dev", "environment_id": "dev", "description": "Environment created on instance creation", "tags": "exampleString", "color_code": "#FDD13A", "features": [{"name": "Cycle Rentals", "feature_id": "cycle-rentals", "description": "exampleString", "type": "NUMERIC", "format": "TEXT", "enabled_value": "1", "disabled_value": "2", "enabled": true, "rollout_percentage": 100, "tags": "exampleString", "segment_rules": [{"rules": [{"segments": ["exampleString","anotherTestString"]}], "value": "exampleString", "order": 38, "rollout_percentage": 100}], "collections": [{"collection_id": "web-app"}], "isOverridden": true}], "properties": [{"name": "Daily Discount", "property_id": "daily_discount", "description": "exampleString", "type": "NUMERIC", "format": "TEXT", "value": "100", "tags": "pre-release, v1.2", "segment_rules": [{"rules": [{"segments": ["exampleString","anotherTestString"]}], "value": "200", "order": 1}], "collections": [{"collection_id": "web-app"}], "isOverridden": true}]}]' \
    --collections '[{"collection_id": "web-app", "name": "web-app", "description": "web app collection", "tags": "v1"}]' \
    --segments '[{"name": "Testers", "segment_id": "khpwj68h", "description": "Testers", "tags": "test", "rules": [{"attribute_name": "email", "operator": "is", "values": ["john@bluecharge.com","alice@bluecharge.com"]}]}]' \
    --clean true
```
{: pre}

### `ibmcloud app-configuration instance-export`
{: #app-configuration-cli-instance-export-command}

Get the instance configuration.

```sh
ibmcloud app-configuration instance-export
```


#### Example
{: #app-configuration-instance-export-examples}

```sh
ibmcloud app-configuration instance-export
```
{: pre}

### `ibmcloud app-configuration gitconfig-promote-restore`
{: #app-configuration-cli-gitconfig-promote-restore-command}

This api will either promote or restore your chosen configuration from or to the GitHub based on the git url, file path and branch data.

```sh
ibmcloud app-configuration gitconfig-promote-restore --git-config-id GIT-CONFIG-ID --action ACTION
```


#### Command options
{: #app-configuration-gitconfig-promote-restore-cli-options}

`--git-config-id` (string)
:   Git Config Id. Required.

`--action` (string)
:   Promote configuration to Git or Restore configuration from Git. Required.

    Allowable values are: `promote`, `restore`.

#### Example
{: #app-configuration-gitconfig-promote-restore-examples}

```sh
ibmcloud app-configuration gitconfig-promote-restore \
    --git-config-id git_config_id \
    --action promote
```
{: pre}

## Schema examples
{: #app-configuration-schema-examples}

The following schema examples represent the data that you need to specify for a command option. These examples model the data structure and include placeholder values for the expected value type. When you run a command, replace these values with the values that apply to your environment as appropriate.

### CollectionRef[]
{: #cli-collection-ref-example-schema}

The following example shows the format of the CollectionRef[] object.

```json

[ {
  "collection_id" : "ghzinc"
} ]
```
{: codeblock}

### FeatureSegmentRule[]
{: #cli-feature-segment-rule-example-schema}

The following example shows the format of the FeatureSegmentRule[] object.

```json

[ {
  "rules" : [ {
    "segments" : [ "betausers", "premiumusers" ]
  } ],
  "value" : "true",
  "order" : 1,
  "rollout_percentage" : 50
} ]
```
{: codeblock}

### ImportCollectionSchema[]
{: #cli-import-collection-schema-example-schema}

The following example shows the format of the ImportCollectionSchema[] object.

```json

[ {
  "collection_id" : "web-app",
  "name" : "web-app",
  "description" : "web app collection",
  "tags" : "v1"
} ]
```
{: codeblock}

### ImportEnvironmentSchema[]
{: #cli-import-environment-schema-example-schema}

The following example shows the format of the ImportEnvironmentSchema[] object.

```json

[ {
  "name" : "Dev",
  "environment_id" : "dev",
  "description" : "Environment created on instance creation",
  "tags" : "exampleString",
  "color_code" : "#FDD13A",
  "features" : [ {
    "name" : "Cycle Rentals",
    "feature_id" : "cycle-rentals",
    "description" : "exampleString",
    "type" : "NUMERIC",
    "format" : "TEXT",
    "enabled_value" : "1",
    "disabled_value" : "2",
    "enabled" : true,
    "rollout_percentage" : 100,
    "tags" : "exampleString",
    "segment_rules" : [ {
      "rules" : [ {
        "segments" : [ "exampleString", "anotherExampleString" ]
      } ],
      "value" : "exampleString",
      "order" : 38,
      "rollout_percentage" : 100
    } ],
    "collections" : [ {
      "collection_id" : "web-app"
    } ],
    "isOverridden" : true
  } ],
  "properties" : [ {
    "name" : "Daily Discount",
    "property_id" : "daily_discount",
    "description" : "exampleString",
    "type" : "NUMERIC",
    "format" : "TEXT",
    "value" : "100",
    "tags" : "pre-release, v1.2",
    "segment_rules" : [ {
      "rules" : [ {
        "segments" : [ "exampleString", "anotherExampleString" ]
      } ],
      "value" : "200",
      "order" : 1
    } ],
    "collections" : [ {
      "collection_id" : "web-app"
    } ],
    "isOverridden" : true
  } ]
} ]
```
{: codeblock}

### ImportSegmentSchema[]
{: #cli-import-segment-schema-example-schema}

The following example shows the format of the ImportSegmentSchema[] object.

```json

[ {
  "name" : "Testers",
  "segment_id" : "khpwj68h",
  "description" : "Testers",
  "tags" : "test",
  "rules" : [ {
    "attribute_name" : "email",
    "operator" : "is",
    "values" : [ "john@bluecharge.com", "alice@bluecharge.com" ]
  } ]
} ]
```
{: codeblock}

### Rule[]
{: #cli-rule-example-schema}

The following example shows the format of the Rule[] object.

```json

[ {
  "attribute_name" : "email",
  "operator" : "endsWith",
  "values" : [ "@in.mnc.com", "@us.mnc.com" ]
} ]
```
{: codeblock}

### SegmentRule[]
{: #cli-segment-rule-example-schema}

The following example shows the format of the SegmentRule[] object.

```json

[ {
  "rules" : [ {
    "segments" : [ "betausers", "premiumusers" ]
  } ],
  "value" : "true",
  "order" : 1
} ]
```
{: codeblock}

### WorkflowCredentials
{: #cli-workflow-credentials-example-schema}

The following example shows the format of the WorkflowCredentials object.

```json

{
  "username" : "user",
  "password" : "pwd",
  "client_id" : "client id value",
  "client_secret" : "clientsecret"
}
```
{: codeblock}


## Uninstall
{: #ac-ibmcloud-plugin-uninstall}

Use this command to uninstall the App Configuration CLI plug-in.

```sh
ibmcloud plugin uninstall app-configuration
```
{: pre}

Uninstall returns a success message, if no errors.
