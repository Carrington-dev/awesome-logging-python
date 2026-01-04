# Awesome Python Logging [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of awesome Python logging libraries, tools, and resources for production-ready structured logging that's simple, powerful, and fast.

## Contents

- [Built-in Libraries](#built-in-libraries)
- [Third-Party Libraries](#third-party-libraries)
- [Structured Logging](#structured-logging)
- [Log Aggregation & Management](#log-aggregation--management)
- [Formatters & Handlers](#formatters--handlers)
- [Testing & Debugging](#testing--debugging)
- [Performance & Monitoring](#performance--monitoring)
- [Resources](#resources)

## Built-in Libraries

### logging
The Python standard library's built-in logging module provides a flexible framework for emitting log messages from Python programs.

**Features:**
- Hierarchical logger naming
- Multiple severity levels (DEBUG, INFO, WARNING, ERROR, CRITICAL)
- Configurable handlers and formatters
- Thread-safe logging
- Configuration via dictConfig or fileConfig

**When to use:** Built into Python, no dependencies required. Perfect for simple applications and when you need maximum compatibility.

```python
import logging

logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)
logger.info("Application started")
```

## Third-Party Libraries

### 🏆 Loguru
**[loguru](https://github.com/Delgan/loguru)** - Ready to use out of the box without boilerplate.

![GitHub Stars](https://img.shields.io/github/stars/Delgan/loguru?style=social)

**Why it's the best choice for most projects:**
- Zero configuration - works immediately
- Automatic string formatting
- Exceptions catching
- Structured logging support
- File rotation and retention
- Asynchronous, thread-safe, and multiprocess-safe
- Beautiful colored console output

```python
from loguru import logger

logger.info("That's it, beautiful and simple logging!")
logger.add("file_{time}.log", rotation="500 MB")
```

**Use Loguru when:** You want the simplest, most Pythonic logging experience with powerful features out of the box.

### structlog
**[structlog](https://github.com/hynek/structlog)** - Structured logging for Python.

**Features:**
- True structured logging (not just JSON)
- Context binding
- Processor pipelines
- Integration with standard library logging
- Type hints throughout
- Excellent performance

```python
import structlog

log = structlog.get_logger()
log.info("user.logged_in", user_id=42, username="alice")
```

**Use structlog when:** You need production-grade structured logging with context preservation and integration with existing logging infrastructure.

### Python JSON Logger
**[python-json-logger](https://github.com/madzak/python-json-logger)** - JSON formatter for the standard library.

**Features:**
- Drops into existing logging setup
- Configurable field names
- Custom fields support
- Exception formatting
- Compatible with log aggregators

**Use when:** You want JSON logging but need to stick with the standard library's logging module.

### Eliot
**[eliot](https://github.com/itamarst/eliot)** - Logging that tells you *why* it happened.

**Features:**
- Action-based logging
- Causal chains
- Message correlation
- Structured by design
- Cross-process tracing

**Use when:** You need to understand complex system behaviors and trace causality across operations.

## Structured Logging

### logbook
**[logbook](https://github.com/getlogbook/logbook)** - A cool logging replacement for Python.

**Features:**
- More Pythonic than standard logging
- Contextual logging
- Flexible handler system
- Better performance
- Thread and multiprocess support

### pygogo
**[pygogo](https://github.com/reubano/pygogo)** - Structured logging with superpowers.

**Features:**
- Reduces logging boilerplate
- Automatic log formatting
- Hierarchical logging
- Multiple output formats
- Email notifications

## Log Aggregation & Management

### sentry-sdk
**[sentry-sdk](https://github.com/getsentry/sentry-python)** - Official Python SDK for Sentry.io

**Features:**
- Error tracking and monitoring
- Performance monitoring
- Release tracking
- Breadcrumbs
- Context enrichment

### elasticsearch-py
**[elasticsearch-py](https://github.com/elastic/elasticsearch-py)** - Official Python client for Elasticsearch

**Use with:** ELK stack (Elasticsearch, Logstash, Kibana) for centralized logging.

### fluentd-python
**[fluent-logger-python](https://github.com/fluent/fluent-logger-python)** - Python client for Fluentd

**Features:**
- Structured event collector
- Unifies data collection
- JSON-based logging

## Formatters & Handlers

### colorlog
**[colorlog](https://github.com/borntyping/python-colorlog)** - Colored terminal output for Python's logging module

**Features:**
- ANSI color support
- Custom color schemes
- Compatible with standard logging
- Windows support

### rich
**[rich](https://github.com/Textualize/rich)** - Beautiful terminal formatting

**Features:**
- Rich text and formatting
- Syntax highlighting
- Progress bars
- Tables and panels
- Logging handler included

```python
from rich.logging import RichHandler
import logging

logging.basicConfig(
    level="INFO",
    format="%(message)s",
    handlers=[RichHandler(rich_tracebacks=True)]
)
```

### notifiers
**[notifiers](https://github.com/liiight/notifiers)** - Send notifications from your logs

**Features:**
- 40+ notification services
- Slack, Discord, Email, Telegram, etc.
- Easy integration with logging

## Testing & Debugging

### pytest-logging
**[pytest-logging](https://github.com/eisensheng/pytest-logging)** - Capture log messages during pytest runs

### testfixtures
**[testfixtures](https://github.com/simplistix/testfixtures)** - Collection of helpers for testing, including log capture

### logassert
**[logassert](https://github.com/pacha/logassert)** - Assert on log messages in tests

## Performance & Monitoring

### logging-tree
**[logging-tree](https://github.com/brandon-rhodes/logging_tree)** - Introspect and display the logging tree

### logging-color
**[logging-color](https://github.com/borntyping/python-colorlog)** - High-performance colored logging

### aiologger
**[aiologger](https://github.com/B2W-BIT/aiologger)** - Asynchronous logging for asyncio applications

## Resources

### Documentation
- [Python Logging HOWTO](https://docs.python.org/3/howto/logging.html) - Official Python documentation
- [Logging Best Practices](https://docs.python-guide.org/writing/logging/) - The Hitchhiker's Guide to Python
- [12-Factor App Logs](https://12factor.net/logs) - Logging as event streams

### Articles & Guides
- [Good logging practice in Python](https://fangpenlin.com/posts/2012/08/26/good-logging-practice-in-python/)
- [The Ultimate Guide to Logging in Python](https://www.loggly.com/ultimate-guide/python-logging-basics/)
- [Structured Logging: The Best Friend You'll Want When Things Go Wrong](https://engineering.grab.com/structured-logging)

### Videos
- [Logging in Python](https://www.youtube.com/watch?v=jxmzY9soFXg) - Real Python
- [Advanced Python: Logging](https://www.youtube.com/watch?v=urrfJgHwIJA) - Socratica

## Comparison & Recommendations

### Quick Decision Guide

**For new projects:** Use **Loguru** - it's the most developer-friendly option with excellent defaults.

**For enterprise applications:** Use **structlog** - best for production environments requiring structured logging with context preservation.

**For standard library compatibility:** Use **python-json-logger** - adds JSON formatting to existing logging setup.

**For microservices:** Use **structlog** or **eliot** - both excel at distributed tracing and correlation.

**For debugging complex flows:** Use **eliot** - designed specifically for understanding causality.

**For simple scripts:** Use Python's built-in **logging** - no dependencies needed.

### Feature Comparison

| Feature | logging | loguru | structlog | eliot |
|---------|---------|--------|-----------|-------|
| Zero config | ❌ | ✅ | ❌ | ✅ |
| Structured logging | ❌ | ⚠️ | ✅ | ✅ |
| Context binding | ❌ | ⚠️ | ✅ | ✅ |
| Performance | Good | Excellent | Excellent | Good |
| Learning curve | Medium | Low | Medium | High |
| Async support | ⚠️ | ✅ | ✅ | ✅ |
| Type hints | ❌ | ⚠️ | ✅ | ❌ |
| Dependencies | 0 | 0 | 0 | Few |

## Contributing

Contributions are welcome! Please read the [contribution guidelines](CONTRIBUTING.md) first.

## License

[![CC0](https://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, Carrington Muleya has waived all copyright and related or neighboring rights to this work.
