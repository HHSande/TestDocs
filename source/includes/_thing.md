# Thing

A thing represents the device as an IoT device in the cloud. This is used for communication between the devices and the cloud.

## Requests

The API offers several endpoints you can use to manage your things.

## Create Thing

Creates a thing in AWS IoT Core, along with a certificate containing permissions regarding the actions the given thing is allowed to perform.
This also links the given device with the thing you create.

| Method | Resource     |
| ------ | ------------ |
| POST   | /createThing |

### Payload parameters

| Field     | Type   | Description                                          | Constraints |
| --------- | ------ | ---------------------------------------------------- | ----------- |
| deviceId  | String | The id of the device to be associated with the thing | Required    |
| thingName | String | The user defined thing name                          | Required    |

> Body Structure

```json
{
  "deviceId": "Test123",
  "thingName": "TestName"
}
```

> Response Structure

```json
{
  "certPem": "something",
  "keyPair": "keypair",
  "thingId": "thingId"
}
```

## Delete Thing

Deletes the thing in AWS IoT Core, also deleting the certificate and removes the association between the thing and the device.

| Method | Resource     |
| ------ | ------------ |
| DELETE | /deleteThing |

### Payload Parameters

| Field     | Type   | Description                 | Constraints |
| --------- | ------ | --------------------------- | ----------- |
| thingName | String | The user defined thing name | Required    |

> Body Structure

```json
{
  "thingName": "TestName"
}
```
