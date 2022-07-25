# Go Live

Whenever a user enters the app that is integrated with the Strømme platform, a "live mode request" is sent.
The motivation behind this, is keeping cost down. Rather than continuously sending live data, we want to buffer it and then send it. This reduces the overall cost, seeing as you're charged for a certain message size, and this size is also the size of the buffer. For example, if we send live data, which is 2 KB in size, and this gets rounded up to 10 KB, then it will be cheaper to buffer 5 live data messages (5 x 2 KB = 10 KB) and then send it.

This means that whenever a user enters their app, only then do they really need to see their data in real-time, and thus the "live mode request" is fired, and data flows into the app real-time.

## Request

| Method | Resource | Query Params |
| ------ | -------- | ------------ |
| GET    | /goLive  | deviceId     |
