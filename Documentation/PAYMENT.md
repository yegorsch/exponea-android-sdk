## 🔍 Payments

#### In-App Purchases

In order to use the automatic payment tracking, the Exponea SDK needs to set the BillingClient class listeners.

All In-App Purchase will handle all the purchases made inside the
app using the Google Play Store. After capture the purchased item, it will be send to the database in order to be flushed and send to the Exponea API.

The listeners can be activate or deactivated by setting the `automaticPaymentTracking` property in Exponea Configuration.

Purchase events contain all basic information about the device (OS, OS version, SDK, SDK version and device model) combined with additional purchase attributes brutto, item_id and item_title. Brutto attribute contains price paid by the player. Attribute item_title consists of human-friendly name of the bought item (e.g. Silver sword) and item_id corresponds to the product identifier for the in-app purchase.

#### In-App Payments

If you use in your project some virtual payments (e.g. purchase with in-game gold, coins, ...),  you can track them manually with simple call `trackPaymentEvent`.

```
fun trackPaymentEvent(
            timestamp: Long = Date().time,
            purchasedItem: PurchasedItem
    )
```

#### 💻 Usage

```
// Preparing the data.
val item = PurchasedItem(
        value = 0.911702,
        currency = "EUR",
        paymentSystem = "Virtual",
        productId = "android.test.purchased",
        productTitle = "Silver sword",
        deviceModel = "LGE Nexus 5",
        deviceType = "mobile",
        ip = "10.0.1.58",
        osName = "Android",
        osVersion = "5.0.1",
        sdk = "AndroidSDK",
        sdkVersion = "1.1.4"
)

// Call fetchCustomerAttributes to get the customer attributes.
   Exponea.trackPaymentEvent( item = item)
```
