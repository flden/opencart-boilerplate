# opencart-boilerplate

## Extensions

- 

### Can I make all out of stock items show last?
https://forum.opencart.com/viewtopic.php?t=161016

### Quick checkout redirect when 0 products
```php
// catalog/controller/extension/quickcheckout/cart.php

if (!$this->cart->hasProducts() && empty($this->session->data['vouchers'])) {
  //$json['redirect'] = $this->url->link('checkout/cart');
  $json['redirect'] = '/';
}
```

### Закрыть паролем
```
// .htaccess

AuthType Basic
AuthName "Admin zone"
AuthUserFile /sata1/home/users/<project_name>/.htpasswd
Require valid-use

// .htpasswd (root:123456)
root:$apr1$6PD30Kac$b9.ZSDiC/HQguA4vxVlv30

```

### Get link to category image and resize
```php
// catalog/controller/product/category.php

$results = $this->model_catalog_category->getCategories($category_id);

foreach ($results as $result) {
  $filter_data = array(
    'filter_category_id'  => $result['category_id'],
    'filter_sub_category' => true
  );

$data['categories'][] = array(
    'name' => $result['name'] . ($this->config->get('config_product_count') ? ' (' . $this->model_catalog_product->getTotalProducts($filter_data) . ')' : ''),
    'href' => $this->url->link('product/category', 'path=' . $this->request->get['path'] . '_' . $result['category_id'] . $url),
  
    // Insert this
    'thumb' => $this->model_tool_image->resize($result['image'], 80,80),
  );
}


```
