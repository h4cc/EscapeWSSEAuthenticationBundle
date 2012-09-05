## Introduction

The EscapeWSSEAuthentication bundle is a simple and easy way to implement WSSE authentication into Symfony2 applications

[![Build Status](https://secure.travis-ci.org/escapestudios/EscapeWSSEAuthenticationBundle.png)](http://travis-ci.org/escapestudios/EscapeWSSEAuthenticationBundle)

## Installation

app/autoload.php

```
$loader->registerNamespaces(array(
    //other namespaces
    'Escape' => __DIR__.'/../vendor/bundles',
  ));
```

app/AppKernel.php

```
public function registerBundles()
{
    return array(
        //other bundles
        new Escape\WSSEAuthenticationBundle\EscapeWSSEAuthenticationBundle(),
    );
    ...
```

## Configuration

app/config/config.yml

```
# Escape WSSE authentication configuration
escape_wsse_authentication:
    provider_class: Escape\WSSEAuthenticationBundle\Security\Core\Authentication\Provider\Provider
    listener_class: Escape\WSSEAuthenticationBundle\Security\Http\Firewall\Listener
```

## Usage example

app/config/security.yml

nonce_dir: location where nonces will be saved (use null to skip nonce-validation)
lifetime: lifetime of nonce

```
firewalls:
    wsse_secured:
        pattern:   ^/api/.*
        wsse:      { nonce_dir: null, lifetime: 300 } 

factories:
    - "%kernel.root_dir%/../vendor/bundles/Escape/WSSEAuthenticationBundle/Resources/config/security_factories.yml"
```

## Contributors
    * Dmitry Petrov <dmitry.petrov@opensoftdev.ru>
    * David Joos <david@escapestudios.com>
