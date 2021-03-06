EPWT Cache
==========
[![Latest Stable Version](https://poser.pugx.org/epwt/cache/v/stable)](https://packagist.org/packages/epwt/cache) [![Total Downloads](https://poser.pugx.org/epwt/cache/downloads)](https://packagist.org/packages/epwt/cache) [![Latest Unstable Version](https://poser.pugx.org/epwt/cache/v/unstable)](https://packagist.org/packages/epwt/cache) [![License](https://poser.pugx.org/epwt/cache/license)](https://packagist.org/packages/epwt/cache)
[![Analytics](https://ga-beacon.appspot.com/UA-62353612-1/gcds/epwt-cache)](https://github.com/igrigorik/ga-beacon) 

[![SensioLabsInsight](https://insight.sensiolabs.com/projects/736ce78f-ddec-4742-a475-c9a8725eaed0/big.png)](https://insight.sensiolabs.com/projects/736ce78f-ddec-4742-a475-c9a8725eaed0)

This library provides PSR-6 based caching.

## Requirements

 * PHP >= 5.4

## Currently Implemented Drivers

* Redis (predis & phpredis supported)

Usage
-------

```php

    $redisDriver = new EPWT\Cache\Drivers\RedisDriver();
    $redis = new Redis();
    $redis->connect('127.0.0.1');
    $redisDriver->setRedis($redis);
    
    $demoCachePool = new EPWT\Cache\Core\CacheItemPool('demo_pool');
    $demoCachePool->setDriver($redisDriver);
    
    $alternativeCachePool = new EPWT\Cache\Core\CacheItemPool('alternative_pool');
    $alternativeCachePool->setDriver($redisDriver);
    
    $cacheItemA = new EPWT\Cache\Core\CacheItem('a');
    $cacheItemA->setCacheItemPool($demoCachePool);
    $cacheItemA->set('foobar');
    
    $demoCachePool->save($cacheItemA);
    
    $a = $demoCachePool->getItem('a');
    $a->get();
    
    $alternativeCachePool->save($a);
    
```

License
-------

This bundle is under the MIT license. See the complete license in the file:

    LICENSE

About
-----

EPWT Cache is brought to you by [Aurimas Niekis](https://github.com/gcds).

Reporting an issue or a feature request
---------------------------------------

Issues and feature requests are tracked in the [Github issue tracker](https://github.com/gcds/epwt-cache/issues).
