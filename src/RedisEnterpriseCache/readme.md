<!-- region Generated -->
# Az.RedisEnterpriseCache
This directory contains the PowerShell module for the RedisEnterpriseCache service.

---
## Status
[![Az.RedisEnterpriseCache](https://img.shields.io/powershellgallery/v/Az.RedisEnterpriseCache.svg?style=flat-square&label=Az.RedisEnterpriseCache "Az.RedisEnterpriseCache")](https://www.powershellgallery.com/packages/Az.RedisEnterpriseCache/)

## Info
- Modifiable: yes
- Generated: all
- Committed: yes
- Packaged: yes

---
## Detail
This module was primarily generated via [AutoRest](https://github.com/Azure/autorest) using the [PowerShell](https://github.com/Azure/autorest.powershell) extension.

## Module Requirements
- [Az.Accounts module](https://www.powershellgallery.com/packages/Az.Accounts/), version 1.8.1 or greater

## Authentication
AutoRest does not generate authentication code for the module. Authentication is handled via Az.Accounts by altering the HTTP payload before it is sent.

## Development
For information on how to develop for `Az.RedisEnterpriseCache`, see [how-to.md](how-to.md).
<!-- endregion -->

## Run Generation
In this directory, run AutoRest:
> `autorest`

---
### AutoRest Configuration
> see https://aka.ms/autorest

``` yaml
require:
  - $(this-folder)/../readme.azure.noprofile.md
# lock the commit
input-file:
  - https://github.com/Azure/azure-rest-api-specs/blob/150da63a09d1cb156cb0b6d8fe575cb9ccf7b6de/specification/redisenterprise/resource-manager/Microsoft.Cache/preview/2020-10-01-preview/redisenterprise.json

module-version: 0.1.0
title: RedisEnterpriseCache
subject-prefix: 'RedisEnterpriseCache'

# This will remove the 'RedisEnterprise' prefix from the subject of every cmdlet
# beginning with 'RedisEnterprise', because we have already set the subject-prefix above
directive:
  # This will remove the 'RedisEnterprise' prefix from the subject of every cmdlet
  # beginning with 'RedisEnterprise', because we have already set the subject-prefix above
  - where:
      subject: (^RedisEnterprise)(.*) 
    set:
      subject: $2

  # Cmdlet renames
  - where:
      verb: Invoke
      subject: OperationGetStatus
    set:
      verb: Get
      subject: OperationStatus

  # Parameter renames and aliases
  - where:
      verb: Get|Update|Remove
      subject: ^$
      parameter-name: ClusterName
    set:
      alias: Name
  - where:
      parameter-name: SkuCapacity
    set:
      parameter-name: Capacity
      alias: SkuCapacity
  - where:
      parameter-name: SkuName
    set:
      parameter-name: Sku
      alias: SkuName

  # Remove unused variants
  - where:
      verb: Get
      variant: ^GetViaIdentity$
    remove: true
  - where:
      verb: Export
      variant: ^Export$|^ExportViaIdentity
    remove: true
  - where:
      verb: Import
      variant: ^Import$|^ImportViaIdentity
    remove: true
  - where:
      verb: Get
      subject: OperationStatus
      variant: ViaIdentity$
    remove: true
  - where:
      verb: New
      subject: DatabaseKey
      variant: ^Regenerate$|ViaIdentity
    remove: true
  - where:
      verb: Update
      subject: ^$|Database
      variant: ^Update$|ViaIdentity$
    remove: true

  # Hide cmdlets
  - where:
      verb: New|Get
      subject: ^$|^Database$|^DatabaseKey$
    hide: true
  - where:
      verb: Remove|Update|Import|Export
      subject: Database
    hide: true
  - where:
      subject: PrivateEndpointConnection|PrivateLinkResource
    hide: true

  # Fix bugs in generated code from namespace conflict
  - from: source-file-csharp
    where: $
    transform: $ = $.replace(/Origin\(System.Convert.ToString\(/g, 'Origin(global::System.Convert.ToString(');
  - from: source-file-csharp
    where: $
    transform: $ = $.replace(/Module.Instance.SetProxyConfiguration\(/g, 'Microsoft.Azure.PowerShell.Cmdlets.RedisEnterpriseCache.Module.Instance.SetProxyConfiguration(');
```
