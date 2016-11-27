# Event Dispatcher

Ultra easy-to-use `Symfony\EventDispatcher` to `Nette Framework`.

-----

[![Build Status](https://img.shields.io/travis/contributte/event-dispatcher.svg?style=flat-square)](https://travis-ci.org/contributte/event-dispatcher)
[![Code coverage](https://img.shields.io/coveralls/contributte/event-dispatcher.svg?style=flat-square)](https://coveralls.io/r/contributte/event-dispatcher)
[![Downloads this Month](https://img.shields.io/packagist/dm/contributte/event-dispatcher.svg?style=flat-square)](https://packagist.org/packages/contributte/event-dispatcher)
[![Downloads total](https://img.shields.io/packagist/dt/contributte/event-dispatcher.svg?style=flat-square)](https://packagist.org/packages/contributte/event-dispatcher)
[![Latest stable](https://img.shields.io/packagist/v/contributte/event-dispatcher.svg?style=flat-square)](https://packagist.org/packages/contributte/event-dispatcher)
[![HHVM Status](https://img.shields.io/hhvm/contributte/event-dispatcher.svg?style=flat-square)](http://hhvm.h4cc.de/package/contributte/event-dispatcher)

## Discussion / Help

[![Join the chat](https://img.shields.io/gitter/room/contributte/contributte.svg?style=flat-square)](https://gitter.im/contributte/contributte?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

## Install

```
composer require contributte/event-dispatcher
```

## Usage

```yaml
extensions:
    events: Contributte\EventDispatcher\DI\EventDispatcherExtensions
```

Extension looks for all events implementing `Contributte\EventDispatcher\EventSubscriber`. And automatically adds them to the event dispatcher. 
That's all. You don't have to be worried.

## Configuration

### Laziness

Lazy options is enabled (`true`) as default. But you can override it.

```yaml
events:
    lazy: true/false
```

### Nette.Application

There are several nette events on which you can listen to.

```php
use Contributte\EventDispatcher\Events\Application\ApplicationEvents;
```

- `ApplicationEvents::ON_STARTUP`
- `ApplicationEvents::ON_SHUTDOWN`
- `ApplicationEvents::ON_REQUEST`
- `ApplicationEvents::ON_PRESENTER`
- `ApplicationEvents::ON_RESPONSE`
- `ApplicationEvents::ON_ERROR`

## Example

```php
use Contributte\EventDispatcher\Events\Application\ApplicationEvents;
use Contributte\EventDispatcher\Events\Application\RequestEvent;
use Contributte\EventDispatcher\EventSubscriber;

final class LogRequestSubscriber implements EventSubscriber
{

	/**
	 * @return array
	 */
	public static function getSubscribedEvents()
	{
		return [ApplicationEvents::ON_REQUEST => 'onLog'];
	}

	/**
	 * @param RequestEvent $event
	 * @return void
	 */
	public function onLog(RequestEvent $event)
	{
	}
}

```

-----

Thank you for testing, reporting and contributing.