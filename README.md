# WhatsApp Embedded Signup

Static page for WhatsApp Embedded Signup (Meta Business Tech Provider flow).

## Usage

Open the page with URL parameters:

```
https://ericblanquercentile.github.io/whatsapp-embedded-signup/?appId=APP_ID&configId=CONFIG_ID&callback=CALLBACK_URL
```

### Required Parameters

| Parameter | Description |
|-----------|-------------|
| `appId` | Facebook App ID |
| `configId` | Embedded Signup configuration ID from Meta |
| `callback` | URL to POST the OAuth code after signup |

### Optional Parameters

| Parameter | Default | Description |
|-----------|---------|-------------|
| `sdkVersion` | `v22.0` | Facebook SDK version |
| `webhook_url` | | Webhook URL to pass to the callback |
| `state` | (random UUID) | State parameter for CSRF protection |

### Display Mode

| Parameter | Default | Description |
|-----------|---------|-------------|
| `mode` | `full` | Display mode: `full` (standalone page with gradient background) or `embedded` (minimal, transparent, for iframe embedding) |
| `origin` | `*` | Parent window origin for postMessage communication (used in embedded mode) |

### Customization

| Parameter | Default | Description |
|-----------|---------|-------------|
| `button_label` | `Continue with Facebook` | Text displayed on the signup button |
| `connecting_label` | `Connecting...` | Text displayed while connecting |
| `button_style` | | Set to `native` for browser default button style (useful in embedded mode) |

### Debug

| Parameter | Description |
|-----------|-------------|
| `debug` | Set to `true` to show version info overlay |

## Error Handling

If any required parameter (`appId`, `configId`, `callback`) is missing, the page displays an error message listing the missing parameters instead of the signup button.

## Embedded Mode Example

For embedding in an iframe with native button style:

```
https://ericblanquercentile.github.io/whatsapp-embedded-signup/?appId=APP_ID&configId=CONFIG_ID&callback=CALLBACK_URL&mode=embedded&button_label=Configure%20WhatsApp&connecting_label=Please%20wait...&button_style=native
```

## Flow

1. User clicks the signup button
2. Facebook Embedded Signup popup opens
3. User completes WhatsApp Business account setup
4. OAuth code is POSTed to the callback URL with:
   - `code`: OAuth authorization code
   - `state`: State parameter
   - `phone_number_id`: WhatsApp phone number ID
   - `waba_id`: WhatsApp Business Account ID
   - `webhook_url`: Webhook URL (if provided)

In embedded mode, `mode=embedded` and `origin` parameters are also added to the callback URL query string for parent window communication.
