# Device

A device represents the physical device sending data to our platform, for instance a HAN-device.

## Requests

The API offers several endpoints you can use to manage your device.

## Create Device

Creates an entry in the database with the given device ID.

| Method | Resource      |
| ------ | ------------- |
| POST   | /createDevice |

### Payload Parameters

| Field    | Type   | Description                    | Constraints |
| -------- | ------ | ------------------------------ | ----------- |
| deviceId | String | ID of the device to be created | Required    |

> Body Structure

```json
{
  "deviceId": "Test123"
}
```

## Delete Device

Deletes the entry from the database with the given device ID.

| Method | Resource      |
| ------ | ------------- |
| DELETE | /createDevice |

### Payload Parameters

| Field    | Type   | Description                    | Constraints |
| -------- | ------ | ------------------------------ | ----------- |
| deviceId | String | ID of the device to be deleted | Required    |

> Body Structure

```json
{
  "deviceId": "Test123"
}
```

## List Device

Lists all devices related to a given partner.

| Method | Resource    | Query Params |
| ------ | ----------- | ------------ |
| GET    | /listDevice | partnerId    |

### Payload Paramters

| Field     | Type   | Description                               | Constraints |
| --------- | ------ | ----------------------------------------- | ----------- |
| partnerId | String | ID of the partner to list the devices for | Required    |

> Response Structure

```json
{
  "devices": [
    {
      "deviceId": "Test123",
      "partnerId": "Partner1337"
    },
    {
      "deviceId": "Test321",
      "partnerId": "Partner1337"
    }
  ]
}
```
