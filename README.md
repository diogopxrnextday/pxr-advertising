# OneLine

Welcome by the Next Day Media OneLine project. The OneLine handles all the logic needed for a publisher to serve ads.

#### Stub

In head code:

```html
<script async src="//oneline.nextday.media/static/tags/XXXXXXXXXX.js"></script>
```

## Event listeners

OneLine offers external script the possibility to receive events. You can subscribe to topics to add custom behaviour.

### Topics

You can subscribe to the following topics:

| Topic           | Description                             | Data                       |
| --------------- | --------------------------------------- | -------------------------- |
| `isEmpty`       | When the placement has no ad to display | {id: `<id of the ad div>`} |
| `isNotEmpty`    | When the placement has an ad to display | {id: `<id of the ad div>`} |
| `tcfReady`      | When tcf is ready                       | -                          |
| `documentReady` | When documentReady is ready             | -                          |
| `ageGateReady`  | When ageGateReady is ready              | -                          |

### Subscribe example isEmpty (add div)

```javascript
ndmOne.event.subscribe(ndmOne.event.topic.isEmpty, (data) => {
  console.log("Event isEmpty : ", data);
  if (data.id !== "ndm-predefined-1") {
    return;
  }
  let e = document.getElementById(data.id);
  let n = document.createElement("div");
  n.innerHTML = "Event: isEmpty";
  e.parentNode.insertBefore(n, e.nextSibling);
});
```

#### Control ad unit

If the rendering of the view is completed. You can request the ad units.

```javascript
import { NdmOne } from "@nextdaymedia/oneline";

declare const ndmOne: NdmOne;

  ndmOne.adUnitRequest(); // Set command to load all matching ad units on the page
  // ndmOne.adUnitRequest(['ndm-1', 'ndm-2']); // Or load only this div's
  // ndmOne.adUnitRequest(['push-up-all']); // Or load only all push up's

```
