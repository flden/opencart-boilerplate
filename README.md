# opencart-boilerplate

### Quick checkout redirect when 0 products
```php
// catalog/controller/extension/quickcheckout/cart.php

if (!$this->cart->hasProducts() && empty($this->session->data['vouchers'])) {
  //$json['redirect'] = $this->url->link('checkout/cart');
  $json['redirect'] = '/';
}
```
