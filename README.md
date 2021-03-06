# Pimcore plugin api-bridge-magento

## Package content

Bridge includes 2 extensions:

1. magento extension https://github.com/oleksandrmakhno/api-bridge-pimcore 
2. pimcore plugin https://github.com/oleksandrmakhno/api-bridge-magento

## How it works

1. very simple
2. in magento we have product 'shirt' with sku = e123
3. in pimcore we have object MagentoBaseProduct 'shirt' with sku = e123
4. for example when in magento we open PDP (product details page) for 'shirt' - api call to pimcore fetch product media data

## Pimcore plugin installation

Using Composer:

```
composer require oleksandrmakhno/api-bridge-magento
```

Manually: 

```
https://github.com/oleksandrmakhno/api-bridge-magento.git
```

Manage pimcore settings: 

```
1. pimcore => settings => object => classes => add class 'MagentoBaseProduct' => import (button in the bottom) => install/objectDefinition/class_MagentoBaseProduct_export.json => save
2. pimcore => settings => system => web service api => web service api enabled (check checkbox) => save 
3. pimcore => settings => users / roles => users => create user 'api-bridge-magento'
4. pimcore => settings => users / roles => users => select user 'api-bridge-magento' => generate user api key (mypimcorerestapikey) => save
5. (install extension to magento) magento => system => configuration => api bridge pimcore => settings => pimcore api user key => set generated value (mypimcorerestapikey) => save config
6. pimcore => extras => extensions => extension 'ApiBridgeMagento' => enable
7. pimcore => objects panel => home (right click) add object => MagentoBaseProduct (sku=e123) => save & publish
```

## Test api call

1. pimcore api returns data or nothing
2. we can test in browser
```
http://pimcore.local/plugin/ApiBridgeMagento/api/gateway?paramCommand=commandGetProduct&paramSku=e123&paramApiKey=mypimcorerestapikey
response: {"sku":"e123","info":null,"imageMain":null}
```

## Release history

* 20160205 0.0.1 pimcore plugin initial version
* 20160216 0.0.2 added logic to install as pimcore plugin
* 20160329 0.1.0 version for installation process testing
* 20160329 0.2.0 version for installation process testing
* 20160329 0.3.0 version for installation process testing
* 20160329 0.4.0 description added
* 20160329 0.5.0 folder structure changed, images added
* 20160329 0.6.0 added folders doc, install
* 20160330 1.0.0 public release

## Maintainer

* Oleksandr Makhno
* option25@gmail.com 
* <a href='https://ua.linkedin.com/in/oleksandr-makhno-98a30b45'>https://ua.linkedin.com/in/oleksandr-makhno-98a30b45</a>
