---

copyright:
  years: 2018, 2019
lastupdated: "2019-09-10"

Keywords: Hyper Protect Crypto Services, event, security, IBM, activity tracker, LogDNA, KMS API calls, monitor KMS events

subcollection: hs-crypto

---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:external: target="_blank" .external}

# {{site.data.keyword.cloudaccesstrailshort}} events
{: #at-events}

As a security officer, auditor, or manager, you can use the Activity Tracker service to track how users and applications interact with {{site.data.keyword.cloud}} {{site.data.keyword.hscrypto}}.
{: shortdesc}

Activity Tracker records user-initiated activities that change the state of a service in the {{site.data.keyword.cloud_notm}}. You can use this service to investigate abnormal activity and critical actions and to comply with regulatory audit requirements. In addition, you can be alerted about actions as they happen. The events that are collected comply with the Cloud Auditing Data Federation (CADF) standard.

There are currently two Activity Tracker services that are available in the {{site.data.keyword.cloud_notm}} catalog. {{site.data.keyword.hscrypto}} sends events to both services, and you can use either service to monitor your {{site.data.keyword.hscrypto}} activity in {{site.data.keyword.cloud_notm}}. However, the {{site.data.keyword.cloudaccesstrailfull}} is deprecated and no new instances can be created, and support for existing service instances is available only through 30 September 2019.

For more information, see:
* [{{site.data.keyword.at_full_notm}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started)
* [{{site.data.keyword.cloudaccesstrailfull_notm}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started) (deprecated)

## List of events
{: #events}

The following table lists the actions that generate an event:

| Action                   | Description                 |
| ------------------------ | --------------------------- |
| `hs-crypto.secrets.create`     | Create a key                |
| `hs-crypto.secrets.read`       | Retrieve a key by ID        |
| `hs-crypto.secrets.delete`     | Delete a key by ID          |
| `hs-crypto.secrets.list`       | Retrieve a list of keys     |
| `hs-crypto.secrets.head`       | Retrieve the number of keys |
| `hs-crypto.secrets.wrap`       | Wrap a key                  |
| `hs-crypto.secrets.unwrap`     | Unwrap a key                |
<!-- | `hs-crypto.secrets.rewrap`     | rewrap a key                | -->
{: caption="Table 1. {{site.data.keyword.hscrypto}} actions that generate Activity Tracker events" caption-side="top"}

## Viewing events
{: #at-ui}

You can view the Activity Tracker events that are associated with your {{site.data.keyword.hscrypto}} service instance by using [{{site.data.keyword.at_full_notm}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) or [{{site.data.keyword.cloudaccesstrailfull_notm}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started) (deprecated).

### Using {{site.data.keyword.at_full_notm}}
{: #at-ui-logdna}

Events that are generated by an instance of {{site.data.keyword.hscrypto}} are automatically forwarded to the {{site.data.keyword.at_full_notm}} service instance that is available in the same location.

{{site.data.keyword.at_full_notm}} can have only one instance per location. To view events, you must access the web UI of the {{site.data.keyword.at_full_notm}} service in the same location where your service instance is available. For more information, see [Launching the web UI through the IBM Cloud UI](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch#launch_step2).

### Using {{site.data.keyword.cloudaccesstrailfull_notm}} (deprecated)
{: #at-ui-legacy}

{{site.data.keyword.cloudaccesstrailshort}} events are available in the {{site.data.keyword.cloudaccesstrailshort}} **account domain** that is available in the {{site.data.keyword.cloud_notm}} region where the events are generated. For more information, see [Viewing events](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-getting-started#gs_step4).

## Analyzing events
{: #at-events-analyze}

Due to the sensitivity of the information for an encryption key, when an event is generated as a result of an API call to the {{site.data.keyword.hscrypto}} service, the event that is generated does not include detailed information about the key. The event includes a correlation ID that you can use to identify the key internally in your cloud environment. The correlation ID is a field that is returned as part of the `responseBody.content` field. You can use this information to correlate the {{site.data.keyword.hscrypto}} key with the information of the action reported through the {{site.data.keyword.cloudaccesstrailshort}} event.
