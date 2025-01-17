
<explain-block title="fluentform/rendering_payment_form">

**Description**

This action runs when rendering payment form.

**Parameters**
- `$form` (object) Payment Form

**Usage**
```php 
add_action('fluentform/rendering_payment_form', function($form) {
   // Do your stuff when rendering payment form
}, 10, 1);
```

**Reference**

`do_action('fluentform/rendering_payment_form', $form);`

This action is located in `fluentform/app/Modules/Component/Component.php`

</explain-block>

------------------------------------------

<explain-block title="fluentform/before_insert_payment_form">

**Description**

If the form has payment then this action will be fired before submission. You can use this to do your payment related custom tasks.

**Parameters**
- `$insertData` Form response data
- `$formData` Form Raw Data
- `$form` Form Object

**Usage:**
```php 
add_action('fluentform/before_insert_payment_form', function ($insertData, $formRawData, $form){
   // Do your stuff here
}, 10, 3);
```

**Reference**

`$this->app->doAction('fluentform/submission_inserted_' . $form->type . '_form', $insertId, $formData, $form);`

This action is located in `fluentform/app/Services/Form/SubmissionHandlerService.php`

</explain-block>

------------------------------------------

<explain-block title="fluentform/render_payment_entries">

**Description**

This action runs before rendering the payment entries.

**Usage:**
```php 
add_action('fluentform/render_payment_entries', function (){
   // Do your stuff here
}, 10, 0);
```

**Reference**

`do_action('fluentform/render_payment_entries');`

This action is located in `fluentform/app/Modules/Registerer/Menu.php`

</explain-block>

------------------------------------------

<explain-block title="fluentform/rendering_payment_method_{$methodName}">

**Description**

This action runs when rendering the payment active methods.

**Parameters**
- `$paymentMethod` - (string) Current Payment Method
- `$data` - (array)  Current Payment Element
- `$form` - (object) Form

**Usage:**
```php 
add_action('fluentform/rendering_payment_method_{$methodName}', function ($paymentMethod, $data, $form){
   // Do your stuff here
}, 10, 3);
```

**Note:** `{$methodName}` is dynamic method name. Replace `{$methodName}` with Fluent Forms payment methods name.

**Reference**

`do_action('fluentform/rendering_payment_method_' . $methodName, $activatedMethod, $data, $form);`

This action is located in `fluentformpro/src/Payments/Components/PaymentMethods.php`, `fluentform/app/Services/FluentConversational/Classes/Converter/Converter.php`

</explain-block>

------------------------------------------

<explain-block title="fluentform/payment_frameless_{$paymentMethod}">

**Description**

This action runs before rendering the payment redirect handler page.

**Parameters**
- `$data` - (array) Payment Data

**Usage:**
```php 
add_action('fluentform/payment_frameless_{$paymentMethod}', function ($data){
   // Do your stuff here
}, 10, 1);
```

**Note:** `{$paymentMethod}` is dynamic method name. Replace `{$paymentMethod}` with Fluent Forms payment methods name.

**Reference**

`do_action('fluentform/payment_frameless_' . $paymentMethod, $data);`

This action is located in `fluentformpro/src/Payments/PaymentHandler.php`

</explain-block>

------------------------------------------

<explain-block title="fluentform/payment_method_render_{$paymentMethod}">

**Description**

This action runs if the form has single payment method, then the payment method is rendered using this method.

**Parameters**
- `$methodElement` (array) Payment Method Data
- `$form` (object) Form Object

**Usage:**
```php 
add_action('fluentform/payment_method_render_{$paymentMethod}', function ($methodElement, $data){
   // Do your stuff here
}, 10, 2);
```

**Note:** `{$paymentMethod}` is dynamic method name. Replace `{$paymentMethod}` with Fluent Forms payment methods name.

**Reference**

`do_action('fluentform/payment_method_render_' . $paymentMethod, $methodElement, $data);`

This action is located in `fluentformpro/src/Payments/Components/PaymentMethods.php`

</explain-block>

------------------------------------------

<explain-block title="fluentform/payment_refunded">

**Description**

This action runs after a successful refund on every payment method. You can hook into this and get the refund data.

**Parameters**
- `$refund` (array)  Refund Data
- `$form_id` (int) Form ID

**Usage:**
```php 
add_action('fluentform/payment_refunded', function($refund, $form_id) {
   // Do your stuff here
}, 10, 2);
```

**Note:** `{$paymentMethod}` is dynamic method name. Replace `{$paymentMethod}` with Fluent Forms payment methods name.

**Reference**

`do_action('fluentform_payment_refunded', $refund, $refund->form_id);`

This action is located in `fluentformpro/src/Payments/PaymentMethods/BaseProcessor.php`

</explain-block>

------------------------------------------

<explain-block title="fluentform/ipn_paypal_action_{$txn_type}">

**Description**

This action runs when  PayPal ipn verification response. You can use to specify transaction type processing you want to perform.

**Parameters**
- `$encoded_data_array` (array) Encoded Data
- `$submissionId` (int) Submission ID
- `$submission` (object) Submission Object
- `$ipnVerified` (boolean) Ipn Verification

**Usage:**
```php 
add_action('fluentform/ipn_paypal_action_{$txn_type}', function($encoded_data_array, $submissionId, $submission, $ipnVerified) {
   // Do your stuff here
}, 10, 4);
```

**Note:** `{$txn_type}` is dynamic [IPN transaction types](https://developer.paypal.com/api/nvp-soap/ipn/IPNandPDTVariables/#link-ipntransactiontypes). Replace `{$txn_type}` with INP transaction type.

**Reference**

`do_action('fluentform/ipn_paypal_action_' . $encoded_data_array['txn_type'], $encoded_data_array, $submissionId, $submission, $ipnVerified);`

This action is located in `fluentformpro/src/Payments/PaymentMethods/PayPal/API/IPN.php`

</explain-block>

------------------------------------------

<explain-block title="fluentform/ipn_paypal_action_web_accept">

**Description**

This action runs during the web accept PayPal ipn.

**Parameters**
- `$encoded_data_array` (array) Encoded Data
- `$submissionId` (int) Submission ID
- `$submission` (object) Submission Object
- `$ipnVerified` (boolean) Ipn Verification

**Usage:**
```php 
add_action('fluentform/ipn_paypal_action_web_accept', function($encoded_data_array, $submissionId, $submission, $ipnVerified) {
   // Do your stuff here
}, 10, 4);
```

**Reference**

`do_action('fluentform/ipn_paypal_action_web_accept', $encoded_data_array, $submissionId, $submission, $ipnVerified);`

This action is located in `fluentformpro/src/Payments/PaymentMethods/PayPal/API/IPN.php`

</explain-block>

------------------------------------------

<explain-block title="fluentform/process_payment">

**Description**

This action runs when process payment

**Parameters**
- `$submissionId` (int) Form ID
- `$submissionData` (array) Submission Data
- `$form` (object) Form
- `$methodSettings` (array) Selected Method Settings
- `$subscriptionItems` (boolean) Is Subscription
- `$totalPayable` (int) Payable amount
- `$submissionServiceHandler` (object) Service Handler Instance

**Usage:**
```php 
add_action('fluentform/process_payment', function($submissionId, $submissionData, $form, $methodSettings, $subscriptionItems, $totalPayable, $submissionServiceHandler) {
   // Do your stuff here
}, 10, 7);
```

**Reference**

`do_action('fluentform/process_payment', $this->submissionId, $this->submissionData, $this->form, $this->methodSettings, !!$subscriptionItems, $totalPayable, $this->submissionServiceHandler);`

This action is located in `fluentformpro/src/Payments/Classes/PaymentAction.php`

</explain-block>

------------------------------------------

<explain-block title="fluentform/process_payment_{$method_name}">

**Description**

This action runs when process payment.

**Parameters**
- `$submissionId` (int) Form ID
- `$submissionData` (array) Submission Data
- `$form` (object) Form
- `$methodSettings` (array) Selected Method Settings
- `$subscriptionItems` (boolean) Is Subscription
- `$totalPayable` (int) Payable amount

**Usage:**
```php 
add_action('fluentform/process_payment_{$method_name}', function($submissionId, $submissionData, $form, $methodSettings, $subscriptionItems, $totalPayable) {
   // Do your stuff here when process payment
}, 10, 6);
```

**Note:** `{$method_name}` is dynamic value. Replace `{$method_name}` with valid fluent form payment method name.

**Reference**

`do_action('fluentform/process_payment_' . $this->selectedPaymentMethod, $this->submissionId, $this->submissionData, $this->form, $this->methodSettings, !!$subscriptionItems, $totalPayable);`

This action is located in `fluentformpro/src/Payments/Classes/PaymentAction.php`

</explain-block>

------------------------------------------

<explain-block title="fluentform/form_payment_success">

**Description**

This action runs after PayPal subscription complete

**Parameters**
- `$submission` (object) Submission Object
- `$transaction` (array) Transaction Data
- `$formId` (int) Form ID
- `$ipnVerified` (boolean) Ipn Verification

**Usage:**
```php 
add_action('fluentform/form_payment_success', function($submission, $transaction, $formId, $ipnVerified) {
   // Do your stuff here
}, 10, 4);
```

**Reference**

`do_action('fluentform/form_payment_success', $submission, $transaction, $formId, false);`

This action is located in `fluentformpro/src/Payments/PaymentMethods/PayPal/API/IPN.php`

</explain-block>

------------------------------------------

<explain-block title="fluentform/before_entry_payment_deleted">

**Description**

This action runs before payment entries delete

**Parameters**
- `$entries` (array) Deleted entries id
- `$transactions` (array) Transaction entries to delete

**Usage:**
```php 
add_action('fluentform/before_entry_payment_deleted', function($entries, $transactions) {
   // Do your stuff here
}, 10, 2);
```

**Reference**

`do_action('fluentform/before_entry_payment_deleted', $entries, $transactionData);`

This action is located in `fluentformpro/src/Payments/Classes/PaymentEntries.php`

</explain-block>

------------------------------------------

<explain-block title="fluentform/after_entry_payment_deleted">

**Description**

This action runs after payment entries deleted

**Parameters**
- `$entries` (array) Deleted entries id
- `$transactions` (array) Transaction entries to delete

**Usage:**
```php 
add_action('fluentform/after_entry_payment_deleted', function($entries, $transactions) {
   // Do your stuff here
}, 10, 2);
```

**Reference**

`do_action('fluentform/after_entry_payment_deleted', $entries, $transactionData);`

This action is located in `fluentformpro/src/Payments/Classes/PaymentEntries.php`

</explain-block>

------------------------------------------

<explain-block title="fluentform/payment_subscription_status_to_cancelled">

**Description**

This action runs when subscription payment status change to cancelled

**Parameters**
- `$subscription` (object) Subscription data
- `$submission` (object) Submission data
- `$oldStatus` (string) Subscription old status

**Usage:**
```php 
add_action('fluentform/payment_subscription_status_to_cancelled', function($subscription, $submission, $oldStatus) {
   // Do your stuff here
}, 10, 3);
```

**Reference**

`do_action('fluentform/payment_subscription_status_to_cancelled', $subscription, $submission, $oldStatus);`

This action is located in `fluentformpro/src/Payments/Classes/PaymentManagement.php`

</explain-block>


------------------------------------------

<explain-block title="fluentform/payment_subscription_status_{$payment_method}_to_{$newStatus}">

**Description**

This action runs when subscription payment status change to cancelled

**Parameters**
- `$subscription` (object) Subscription data
- `$submission` (object) Submission data
- `$oldStatus` (string) Subscription old status

**Usage:**
```php 
add_action('fluentform/payment_subscription_status_{$payment_method}_to_{$newStatus}', function($subscription, $submission, $oldStatus) {
   // Do your stuff here
}, 10, 3);
```

**Note:** `{$payment_method}` and `{$newSatus}` is dynamic value. Replace `{$payment_method}` with fluentform valid payment method and `{$newSatus}` with valid subscription payment status for responsible payment method.

**Reference**

`do_action('fluentform/payment_subscription_status_' . $submission->payment_method . '_to_' . $newStatus, $subscription, $submission, $oldStatus);`

This action is located in `fluentformpro/src/Payments/Classes/PaymentManagement.php`

</explain-block>

------------------------------------------

<explain-block title="fluentform/payment_receipt_before_content">

**Description**

This action runs before rendering payment receipt

**Parameters**
- `$submission` (object) Submission data

**Usage:**
```php 
add_action('fluentform/payment_receipt_before_content', function($submission) {
   // Do your stuff here
}, 10, 1);
```

**Reference**

`do_action('fluentform/payment_receipt_before_content', $this->entry);`

This action is located in `fluentformpro/src/Payments/Classes/PaymentReceipt.php`

</explain-block>

------------------------------------------------

<explain-block title="fluentform/payment_receipt_after_content">

**Description**

This action runs after rendered payment receipt

**Parameters**
- `$submission` (object) Submission data

**Usage:**
```php 
add_action('fluentform/payment_receipt_after_content', function($submission) {
   // Do your stuff here
}, 10, 1);
```

**Reference**

`do_action('fluentform/payment_receipt_after_content', $this->entry);`

This action is located in `fluentformpro/src/Payments/Classes/PaymentReceipt.php`

</explain-block>

-------------------------------------------

<explain-block title="fluentform/payment_view_{$route}">

**Description**

This action runs before rendering the payment handler view.

**Parameters**
- `$data` - (array) Payment Data

**Usage:**
```php 
add_action('fluentform/payment_view_{$route}', function($data) {
   // Do your stuff here
}, 10, 1);
```

**Note:** `{$route}` is dynamic value. Replace `{$route}` with valid payment view route.

**Reference**

`do_action('fluentform/payment_view_' . $route, $data);`

This action is located in `fluentformpro/src/Payments/PaymentHandler.php`

</explain-block>

-------------------------------------------

<explain-block title="fluentform/ipn_endpoint_{$paymentMethod}">

**Description**

This action runs when payment handler api notify.


**Usage:**
```php 
add_action('fluentform/ipn_endpoint_{$paymentMethod}', function() {
   // Do your stuff here
}, 10, 0);
```

**Note:** `{$paymentMethod}` is dynamic value. Replace `{$paymentMethod}` with valid payment method.

**Reference**

`do_action('fluentform/ipn_endpoint_' . $paymentMethod);`

This action is located in `fluentformpro/src/Payments/PaymentHandler.php`

</explain-block>

-------------------------------------------

<explain-block title="fluentform/subscription_payment_canceled">

**Description**

This action runs when recorded subscription cancelled.

**Parameters**
- `$subscription` - (object) Subscription data
- `$submission` - (object) Submission data
- `$vendorData` - (array) Subscription vendor data

**Usage:**
```php 
add_action('fluentform/subscription_payment_canceled', function($subscription, $submission, $vendorData) {
   // Do your stuff here
}, 10, 3);
```


**Reference**

`do_action('fluentform/subscription_payment_canceled', $subscription, $submission, $vendorData);`

This action is located in `fluentformpro/src/Payments/PaymentHelper.php`

</explain-block>

-------------------------------------------

<explain-block title="fluentform/subscription_payment_canceled_{$payment_method}">

**Description**

This action runs when recorded subscription cancelled.

**Parameters**
- `$subscription` - (object) Subscription data
- `$submission` - (object) Submission data
- `$vendorData` - (array) Subscription vendor data

**Usage:**
```php 
add_action('fluentform/subscription_payment_canceled_{$payment_method}', function($subscription, $submission, $vendorData) {
   // Do your stuff here
}, 10, 3);
```

**Note:** `{$payment_method}` is dynamic value. Replace `{$payment_method}` with valid fluentform payment method name.


**Reference**

`do_action('fluentform/subscription_payment_canceled_' . $submission->payment_method, $subscription, $submission, $vendorData);`

This action is located in `fluentformpro/src/Payments/PaymentHelper.php`

</explain-block>






