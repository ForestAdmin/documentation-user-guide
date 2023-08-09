---
description: >-
  The synergy between Forest Admin and Metabase is perfect. While Forest Admin
  provides an easy way to manage data, Metabase enables you to analyze and
  extract insights from that data.
---

# Metabase

{% embed url="https://www.youtube.com/watch?v=5gh5s8Spb0E" %}

All you have to do to embed your Metabase dashboard into Forest Admin is to create a new chart on Forest Admin and select the **Chart type**: "Smart Chart"

<figure><img src="../.gitbook/assets/image (575).png" alt=""><figcaption></figcaption></figure>

Then, click on "Edit in builder" to start creating your Smart Chart.

**Component**

No custom javascript is required to integrate Metabase, so you can leave the Component code by default:

```javascript
import Component from '@glimmer/component';
import { loadExternalStyle, loadExternalJavascript } from 'client/utils/smart-view-utils';

export default class extends Component {}
```

**Style**

To create a visually attractive look, you can alter the CSS to fit your preferences, but this style should provide a quite good design experience.

```css
.c-smart-chart {
  height: 100%;
  width: 100%;
}

.c-smart-chart__content {
  display: flex;
  width: 100%;
  height: 100%;
  flex-direction: column;
  overflow: hidden;
  color: var(--color-beta-on-surface_medium);
}

.c-smart-chart__metabase {
  flex-grow: 1;
  border: none;
  margin: 0;
  padding: 0;
}
```

**Template**

The integration is done using an `<iframe>` to be included in your template. The `src` tag must be modified to specify the correct `METABASE_SITE_URL` and `JWT_TOKEN`.

```html
<div class="c-smart-chart">
  <div class="c-smart-chart__content">
    <iframe src="https://METABASE_SITE_URL/embed/dashboard/JWT_TOKEN#theme=transparent&bordered=false&titled=true" frameborder="0" allowtransparency class="c-smart-chart__metabase">
    </iframe>
  </div>
</div>
```

**`METABASE_SITE_URL`**

This corresponds to the hostname of your Metabase instance. For example, if your Metabase instance is accessible through _https://myanalytics.mycompany.com_, then you must set your `METABASE_SITE_URL` to `myanalytics.mycompany.com`.

**`JWT_TOKEN`**

The JWT\_TOKEN ensures valid authentication when retrieving the Metabase dashboard. The simplest way to do this is to generate it online using [https://token.dev](https://token.dev/). To sign the JWT token, you need to use the `METABASE_SECRET_KEY` provided by Metabase.

You must replace `METABASE_DASHBOARD_ID` by the the correct dashboard ID provided by Metabase.

_JWT Payload:_

```json
{
  "resource": { "dashboard": METABASE_DASHBOARD_ID },
  "params": {}
}
```

And voilà! Your Metabase dashboard is now fully integrated into Forest Admin 💚.\


<figure><img src="../.gitbook/assets/image (562).png" alt=""><figcaption></figcaption></figure>
