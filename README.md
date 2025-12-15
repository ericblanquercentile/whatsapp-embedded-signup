# WhatsApp Embedded Signup

Static page for WhatsApp Embedded Signup (Meta Business Tech Provider flow).

## Usage

Open the page with URL parameters:

```
https://ericblanquercentile.github.io/whatsapp-embedded-signup/?appId=APP_ID&configId=CONFIG_ID&callback=CALLBACK_URL&state=STATE
```

### Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `appId` | Yes | Facebook App ID |
| `configId` | Yes | Embedded Signup configuration ID from Meta |
| `callback` | Yes | URL to POST the OAuth code after signup |
| `sdkVersion` | No | Facebook SDK version (default: `v22.0`) |
| `webhook_url` | No | Webhook URL to pass to the callback |
| `state` | No | State parameter for CSRF protection |

### Error Handling

If any required parameter (`appId`, `configId`, `callback`) is missing, the page displays an error message listing the missing parameters instead of the signup button.

## Flow

1. User clicks "Continue with Facebook"
2. Facebook Embedded Signup popup opens
3. User completes WhatsApp Business account setup
4. OAuth code is POSTed to the callback URL with:
   - `code`: OAuth authorization code
   - `state`: State parameter
   - `phone_number_id`: WhatsApp phone number ID
   - `waba_id`: WhatsApp Business Account ID
   - `webhook_url`: Webhook URL (if provided)
